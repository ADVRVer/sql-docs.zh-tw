---
title: 保存的資料來源物件 | Microsoft Docs
description: 保存的資料來源物件
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB data source objects [OLE DB Driver for SQL Server]
- data source objects [OLE DB]
- OLE DB Driver for SQL Server, persisted data source objects
- persisted data source objects
author: pmasl
ms.author: pelopes
ms.openlocfilehash: c8ba02b1b459e3f1381138eaa708658b317cd9f8
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "68015937"
---
# <a name="persisted-data-source-objects"></a>保存的資料來源物件
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server 利用 **IPersistFile** 介面來支援保存的資料來源物件。  
  
## <a name="examples"></a>範例  
 **A.保存資料來源初始化：**  
  
 這個範例會示範一個函數，此函數會保存定義伺服器和資料庫的資料來源初始化屬性，以及使用 Windows 驗證模式來進行連接。 伺服器名稱和資料庫名稱會在此函式的 *pLocation* 和 *pDatasource* 參數中接收。  
  
```  
HRESULT SetAndSaveInitProps  
    (  
    IDBInitialize* pIDBInitialize,  
    WCHAR* pDataSource,  
    WCHAR* pCatalog,  
    BOOL bUseWinNTAuth  
    )  
    {  
    const ULONG     nProps = 4;  
    ULONG           nSSProps;  
    ULONG           nPropSets;  
    ULONG           nProp;  
    IDBProperties*  pIDBProperties  = NULL;  
    IPersistFile*   pIPersistFile   = NULL;  
    DBPROP          aInitProps[nProps];  
    DBPROP*         aSSInitProps    = NULL;  
    DBPROPSET*      aInitPropSets   = NULL;  
    HRESULT         hr;  
  
        nSSProps = 0;  
        nPropSets = 1;  
  
    aInitPropSets = new DBPROPSET[nPropSets];  
  
    // Initialize common property options.  
    for (nProp = 0; nProp < nProps; nProp++)  
        {  
        VariantInit(&aInitProps[nProp].vValue);  
        aInitProps[nProp].dwOptions = DBPROPOPTIONS_REQUIRED;  
        aInitProps[nProp].colid = DB_NULLID;  
        }  
  
    // Level of prompting that will be done to complete the connection  
    // process.  
    aInitProps[0].dwPropertyID = DBPROP_INIT_PROMPT;  
    aInitProps[0].vValue.vt = VT_I2;  
    aInitProps[0].vValue.iVal = DBPROMPT_NOPROMPT;       
  
    // Server name.  
    aInitProps[1].dwPropertyID = DBPROP_INIT_DATASOURCE;      
    aInitProps[1].vValue.vt = VT_BSTR;  
    aInitProps[1].vValue.bstrVal = SysAllocString(pDataSource);  
  
    // Database.  
    aInitProps[2].dwPropertyID = DBPROP_INIT_CATALOG;  
    aInitProps[2].vValue.vt = VT_BSTR;  
    aInitProps[2].vValue.bstrVal = SysAllocString(pCatalog);  
  
    aInitProps[3].dwPropertyID = DBPROP_AUTH_INTEGRATED;  
    if (bUseWinNTAuth == TRUE)  
    {  
        aInitProps[3].vValue.vt = VT_BSTR;  
        aInitProps[3].vValue.bstrVal = SysAllocString(L"SSPI");  
    } //end if  
  
    // Now that properties are set, construct the PropertySet array.  
    aInitPropSets[0].guidPropertySet = DBPROPSET_DBINIT;  
    aInitPropSets[0].cProperties = nProps;  
    aInitPropSets[0].rgProperties = aInitProps;  
  
    // Set initialization properties  
    pIDBInitialize->QueryInterface(IID_IDBProperties,  
        (void**) &pIDBProperties);  
    hr = pIDBProperties->SetProperties(nPropSets, aInitPropSets);  
    if (FAILED(hr))  
        {  
        // Display error from failed SetProperties.  
        }  
    pIDBProperties->Release();  
  
    // Free references on OLE known strings.  
    for (nProp = 0; nProp < nProps; nProp++)  
        {  
        if (aInitProps[nProp].vValue.vt == VT_BSTR)  
            SysFreeString(aInitProps[nProp].vValue.bstrVal);  
        }  
  
    for (nProp = 0; nProp < nSSProps; nProp++)  
        {  
        if (aSSInitProps[nProp].vValue.vt == VT_BSTR)  
            SysFreeString(aSSInitProps[nProp].vValue.bstrVal);  
        }  
  
    // Free dynamically allocated memory.  
    delete [] aInitPropSets;  
    delete [] aSSInitProps;  
  
    // On success, persist the data source.  
    if (SUCCEEDED(hr))  
        {  
        pIDBInitialize->QueryInterface(IID_IPersistFile,  
            (void**) &pIPersistFile);  
  
        hr = pIPersistFile->Save(OLESTR("MyDataSource.txt"), FALSE);  
  
        if (FAILED(hr))  
            {  
            // Display errors from IPersistFile interface.  
            }  
        pIPersistFile->Release();  
        }  
  
    return (hr);  
    }  
```  
  
 **B.使用保存的資料來源初始化：**  
  
 此範例會搭配其他初始化屬性來使用保存的資料來源物件，這些屬性會提供 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入和密碼。  
  
```  
HRESULT InitFromPersistedDS  
    (  
    IDBInitialize* pIDBInitialize,  
    WCHAR* pPersistedDSN,  
    WCHAR* pUID,  
    WCHAR* pPWD  
    )  
    {  
    //const ULONG   nProps = 3;  
    const ULONG     nProps = 1;  
    const ULONG     nPropSets = 1;  
    ULONG           nProp;  
    IDBProperties*  pIDBProperties  = NULL;  
    IPersistFile*   pIPersistFile   = NULL;  
    DBPROP          aInitProps[nProps];  
    DBPROPSET       aInitPropSets[nPropSets];  
    HRESULT         hr;  
  
    // First load the persisted data source information.  
    pIDBInitialize->QueryInterface(IID_IPersistFile,  
        (void**) &pIPersistFile);  
  
    hr = pIPersistFile->Load(pPersistedDSN, STGM_DIRECT);  
  
    if (FAILED(hr))  
        {  
        // Display errors from IPersistFile interface.  
        }  
    pIPersistFile->Release();  
  
    if (FAILED(hr))  
        {  
        return (hr);  
        }  
  
    // Initialize common property options.  
    for (nProp = 0; nProp < nProps; nProp++)  
        {  
        VariantInit(&aInitProps[nProp].vValue);  
        aInitProps[nProp].dwOptions = DBPROPOPTIONS_REQUIRED;  
        aInitProps[nProp].colid = DB_NULLID;  
        }  
  
    // Level of prompting that will be done to complete the connection  
    // process.  
    aInitProps[0].dwPropertyID = DBPROP_INIT_PROMPT;  
    aInitProps[0].vValue.vt = VT_I2;  
    aInitProps[0].vValue.iVal = DBPROMPT_NOPROMPT;      
  
    // Now that properties are set, construct the PropertySet array.  
    aInitPropSets[0].guidPropertySet = DBPROPSET_DBINIT;  
    aInitPropSets[0].cProperties = nProps;  
    aInitPropSets[0].rgProperties = aInitProps;  
  
    // Set initialization properties  
    pIDBInitialize->QueryInterface(IID_IDBProperties,  
        (void**) &pIDBProperties);  
    hr = pIDBProperties->SetProperties(nPropSets, aInitPropSets);  
    if (SUCCEEDED(hr))  
        {  
        hr = pIDBInitialize->Initialize();  
        if (FAILED(hr))  
            {  
            DumpError(pIDBInitialize, IID_IDBInitialize);  
            }  
        }  
    else  
        {  
        // Display error from failed SetProperties.  
        }  
    pIDBProperties->Release();  
  
    // Free references on OLE known strings.  
    for (nProp = 0; nProp < nProps; nProp++)  
        {  
        if (aInitProps[nProp].vValue.vt == VT_BSTR)  
            SysFreeString(aInitProps[nProp].vValue.bstrVal);  
        }  
  
    return (hr);  
    }  
```  
  
 **IPersistFile::Save** 方法可以在呼叫 **IDBInitialize::Initialize** 之前或之後呼叫。 當從 **IDBInitialize::Initialize** 成功傳回之後呼叫此方法時，可確保已保存有效的資料來源規格。  
  
## <a name="see-also"></a>另請參閱  
 [資料來源物件 &#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
