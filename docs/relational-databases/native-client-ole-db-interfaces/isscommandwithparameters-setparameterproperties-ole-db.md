---
title: 'Isscommandwithparameters:: Setparameterproperties (OLE DB) |Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSCommandWithParameters::SetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- SetParameterProperties method
ms.assetid: 4cd0281a-a2a0-43df-8e46-eb478b64cb4b
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 01d61838d1267b54eedd1c389c198d50fa52f7d5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63052849"
---
# <a name="isscommandwithparameterssetparameterproperties-ole-db"></a>ISSCommandWithParameters::SetParameterProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  依照序數根據每個參數來設定參數的屬性，或指定 SSPARAMPROPS 結構的陣列來設定大量參數屬性。  
  
## <a name="syntax"></a>語法  
  
```  
  
HRESULT SetParameterProperties(  
      DB_UPARAMS cParams,   
      SSPARAMPROPS rgParamProperties[]);  
```  
  
## <a name="arguments"></a>引數  
 *cParams*[in]  
 *rgParamProperties* 陣列中 SSPARAMPROPS 結構的數目。 如果這個數目為零，則 **ISSCommandWithParameters::SetParameterProperties** 會刪除可能已針對命令中的任何參數所指定的所有屬性。  
  
 *rgParamProperties*[in]  
 要設定的 SSPARAMPROPS 結構的陣列。  
  
## <a name="return-code-values"></a>傳回碼值  
 **ISSCommandWithParameters::SetParameterProperties** 方法所傳回的錯誤碼與核心 OLE DB **ICommandProperties::SetProperties** 方法相同。  
  
## <a name="remarks"></a>備註  
 您可以依序數按照每個參數使用這個方法來設定參數屬性，或在從屬性陣列建立 SSPARAMPROPS 之後，使用單一的 **ISSCommandWithParameters::SetParameterProperties** 呼叫來設定參數屬性。  
  
 在呼叫 **ISSCommandWithParameters::SetParameterProperties** 方法之前，必須先呼叫 **SetParameterInfo** 方法。 呼叫 `SetParameterProperties(0, NULL)` 會清除所有指定的參數屬性，呼叫 `SetParameterInfo(0,NULL,NULL)` 則會清除所有的參數資訊，包括任何可能與參數相關聯的屬性。  
  
 呼叫**isscommandwithparameters:: Setparameterproperties**即可指定屬性參數而不是型別 DBTYPE_XML 或 DBTYPE_UDT 會傳回 DB_E_ERRORSOCCURRED 或 DB_S_ERRORSOCCURRED，並標記*dwStatus*所有 DBPROPs SSPARAMPROPS 中包含具有 DBPROPSTATUS_NOTSET 的該參數的欄位。 系統會周遊 SSPARAMPROPS 中包含的每個 DBPROPSET 的 DBPROP 陣列，以偵測 DB_E_ERRORSOCCURRED 或 DB_S_ERRORSOCCURRED 所參考的是哪一個參數。  
  
 如果呼叫 **ISSCommandWithParameters::SetParameterProperties** 來指定參數 (尚未使用 **SetParameterInfo** 設定其參數資訊) 的屬性，則提供者會傳回 E_UNEXPECTED 且顯示下列錯誤訊息：  
  
 必須先針對指定的參數呼叫 SetParameterInfo 方法，然後才能呼叫 SetParameterProperties 方法。 而在設定參數屬性之前，也必須先設定參數資訊。  
  
 如果 **ISSCommandWithParameters::SetParameterProperties** 的呼叫所包含的參數中有些已設定參數資訊，有些尚未設定，則 SSPARAMPROPS 屬性集的 DBPROPSET 中的 dwStatus 屬性會以 DBSTATUS_NOTSET 傳回。  
  
 SSPARAMPROPS 結構定義如下：  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 在開始 database engine 的改進[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]允許 isscommandwithparameters:: Setparameterproperties 以取得更精確的預期結果的描述。 這些更精確的結果可能不同於在舊版的 isscommandwithparameters:: Setparameterproperties 傳回的值[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 中繼資料探索](../../relational-databases/native-client/features/metadata-discovery.md)。  
  
|成員|描述|  
|------------|-----------------|  
|*iOrdinal*|所傳遞參數的序數。|  
|*cPropertySets*|*rgPropertySets* 中的 DBPROPSET 結構數目。|  
|*rgPropertySets*|藉其傳回 DBPROPSET 結構陣列的記憶體指標。|  
  
## <a name="see-also"></a>另請參閱  
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
