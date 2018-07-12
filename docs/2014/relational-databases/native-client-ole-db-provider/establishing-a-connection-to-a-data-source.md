---
title: 建立資料來源的連接 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data sources [SQL Server Native Client]
- connections [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, data source connections
- CoCreateInstance method
- OLE DB data sources [SQL Server Native Client]
ms.assetid: 7ebd1394-cc8d-4bcf-92f3-c374a26e7ba0
caps.latest.revision: 43
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9b07fd8c9710c591806721d019f7dc776298fbab
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425287"
---
# <a name="establishing-a-connection-to-a-data-source"></a>建立資料來源的連接
  若要存取[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者，取用者必須先建立資料來源物件的執行個體藉由呼叫**CoCreateInstance**方法。 唯一類別識別項 (CLSID) 會識別每個 OLE DB 提供者。 針對[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者，類別識別項為 CLSID_SQLNCLI10。 您也可以使用符號 sqlncli_clsid 符號將會解析為[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用您所參考之 sqlncli.h 中的 Native Client OLE DB 提供者。  
  
 資料來源物件會公開**IDBProperties**介面，取用者可以使用提供基本的驗證資訊，例如伺服器名稱、 資料庫名稱、 使用者識別碼和密碼。 **Idbproperties:: Setproperties**呼叫方法來設定這些屬性。  
  
 如果有多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體在電腦上執行，伺服器名稱會指定為 ServerName\InstanceName。  
  
 資料來源物件也會公開**IDBInitialize**介面。 設定屬性之後，連接到資料來源建立的方法是呼叫**idbinitialize:: Initialize**方法。 例如：  
  
```  
CoCreateInstance(CLSID_SQLNCLI10,   
                 NULL,   
                 CLSCTX_INPROC_SERVER,  
                 IID_IDBInitialize,   
                 (void **) &pIDBInitialize)  
```  
  
 此呼叫**CoCreateInstance**建立與 CLSID_SQLNCLI10 相關聯類別的單一物件 （CSLID 相關聯的資料和將用來建立物件的程式碼）。 IID_IDBInitialize 是介面的識別項的參考 (**IDBInitialize**) 用來與物件通訊。  
  
 以下是初始化與建立資料來源之連接的範例函數。  
  
```  
void InitializeAndEstablishConnection() {  
   // Initialize the COM library.  
   CoInitialize(NULL);  
  
   // Obtain access to the SQL Server Native Client OLE DB provider.  
   hr = CoCreateInstance(CLSID_SQLNCLI10,   
                         NULL,   
                         CLSCTX_INPROC_SERVER,  
                         IID_IDBInitialize,   
                         (void **) &pIDBInitialize);  
   // Initialize property values needed to establish connection.  
   for (i = 0 ; i < 4 ; i++)   
      VariantInit(&InitProperties[i].vValue);  
  
   // Server name.  
   // See DBPROP structure for more information on InitProperties  
   InitProperties[0].dwPropertyID  = DBPROP_INIT_DATASOURCE;  
   InitProperties[0].vValue.vt    = VT_BSTR;  
   InitProperties[0].vValue.bstrVal=   
                     SysAllocString(L"Server");  
   InitProperties[0].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[0].colid       = DB_NULLID;  
  
   // Database.  
   InitProperties[1].dwPropertyID  = DBPROP_INIT_CATALOG;  
   InitProperties[1].vValue.vt    = VT_BSTR;  
   InitProperties[1].vValue.bstrVal= SysAllocString(L"database");  
   InitProperties[1].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[1].colid       = DB_NULLID;  
  
   // Username (login).  
   InitProperties[2].dwPropertyID  = DBPROP_AUTH_INTEGRATED;  
   InitProperties[2].vValue.vt    = VT_BSTR;  
   InitProperties[2].vValue.bstrVal= SysAllocString(L"SSPI");  
   InitProperties[2].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[2].colid       = DB_NULLID;  
   InitProperties[3].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[3].colid       = DB_NULLID;  
  
   // Construct the DBPROPSET structure(rgInitPropSet). The   
   // DBPROPSET structure is used to pass an array of DBPROP   
   // structures (InitProperties) to the SetProperties method.  
   rgInitPropSet[0].guidPropertySet = DBPROPSET_DBINIT;  
   rgInitPropSet[0].cProperties   = 4;  
   rgInitPropSet[0].rgProperties   = InitProperties;  
  
   // Set initialization properties.  
   hr = pIDBInitialize->QueryInterface(IID_IDBProperties,   
                           (void **)&pIDBProperties);  
   hr = pIDBProperties->SetProperties(1, rgInitPropSet);   
   pIDBProperties->Release();  
  
   // Now establish the connection to the data source.  
   pIDBInitialize->Initialize();  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [建立 SQL Server Native Client OLE DB 提供者應用程式](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
