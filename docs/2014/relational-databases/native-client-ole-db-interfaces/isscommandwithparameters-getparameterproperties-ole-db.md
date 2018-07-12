---
title: Getparameterinfo (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- GetParameterProperties method
ms.assetid: 7f4cc5ea-d028-4fe5-9192-bd153ab3c26c
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 66377f57af64b4db43e20714c53a3e78a5daafab
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428317"
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>ISSCommandWithParameters::GetParameterProperties (OLE DB)
  傳回 SSPARAMPROPS 屬性集結構的陣列，而且每個 UDT 或 XML 參數使用一個 SSPARAMPROPS 屬性集。  
  
## <a name="syntax"></a>語法  
  
```  
  
HRESULT GetParameterProperties(  
DB_UPARAMS *pcParams,  
SSPARAMPROPS **prgParamProperties);  
```  
  
## <a name="arguments"></a>引數  
 *pcParams*[out] [in]  
 包含的 SSPARAMPROPS 結構數目的記憶體指標，要傳入*prgParamProperties*。  
  
 *prgParamProperties*[out]  
 藉其傳回 SSPARAMPROPS 結構陣列的記憶體指標。 提供者會為結構配置記憶體，並將位址傳回給這個記憶體中;取用者釋放這個記憶體**imalloc:: Free**當它不再需要的結構。 然後再呼叫**imalloc:: Free** for *prgParamProperties*，取用者還必須呼叫**VariantClear**如*vValue*屬性若要防止記憶體流失，在變數包含參考的情況下每個 DBPROP 結構的型別 （例如 BSTR。)如果*pcParams*是零個輸出，或發生錯誤 DB_E_ERRORSOCCURRED 之外，提供者不會配置任何記憶體並確保*prgParamProperties*輸出上的 null 指標。  
  
## <a name="return-code-values"></a>傳回碼值  
 **GetParameterProperties**方法會傳回相同的錯誤碼與核心 OLE DB **icommandproperties:: Getproperties**除了 DB_S_ERRORSOCCURRED 和 DB_E_ERRORSOCCURED 之外的方法，不可為引發。  
  
## <a name="remarks"></a>備註  
 **Getparameterinfo**採取一致的行為相對於**GetParameterInfo**。 如果[isscommandwithparameters:: Setparameterproperties](isscommandwithparameters-setparameterproperties-ole-db.md)或是**SetParameterInfo**尚未呼叫或已經呼叫 cparams 等於零， **GetParameterInfo**衍生參數資訊並傳回此資訊。 如果**isscommandwithparameters:: Setparameterproperties**或是**SetParameterInfo**至少一個參數，呼叫**Getparameterinfo** ，會傳回這些參數的屬性**isscommandwithparameters:: Setparameterproperties**已呼叫。 如果**isscommandwithparameters:: Setparameterproperties**之後，會呼叫**Getparameterinfo**或是**GetParameterInfo**，後續呼叫**Getparameterinfo**為其傳回這些參數的覆寫的值**isscommandwithparameters:: Setparameterproperties**被呼叫。  
  
 SSPARAMPROPS 結構定義如下：  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
|成員|描述|  
|------------|-----------------|  
|*iOrdinal*|所傳遞參數的序數。|  
|*cPropertySets*|的 DBPROPSET 結構數目中*rgPropertySets*。|  
|*rgPropertySets*|藉其傳回 DBPROPSET 結構陣列的記憶體指標。|  
  
## <a name="see-also"></a>另請參閱  
 [ISSCommandWithParameters &#40;OLE DB&#41;](isscommandwithparameters-ole-db.md)  
  
  
