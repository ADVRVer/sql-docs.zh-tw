---
title: ISSCommandWithParameters::GetParameterProperties (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- GetParameterProperties method
ms.assetid: 7f4cc5ea-d028-4fe5-9192-bd153ab3c26c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6d492a64b6d8a4e8ddf7de27067f1f0bcfef205e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2020
ms.locfileid: "62638080"
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
 *pcParams*[out][in]  
 記憶體的指標，其中包含在 *prgParamProperties* 中傳回的 SSPARAMPROPS 結構數目。  
  
 *prgParamProperties*[out]  
 藉其傳回 SSPARAMPROPS 結構陣列的記憶體指標。 提供者會為結構配置記憶體，並將位址傳回此記憶體;取用者不再需要結構時，會使用**IMalloc：： Free**釋放此記憶體。 在呼叫**IMalloc：： Free** for *prgParamProperties*之前，取用者也必須針對每個 DBPROP 結構的*vValue*屬性呼叫**VariantClear** ，以便在 variant 包含參考型別（例如 BSTR）的情況下，避免發生記憶體流失的情況。如果*時 pcparams*在輸出上為零，或發生 DB_E_ERRORSOCCURRED 以外的錯誤，則提供者不會配置任何記憶體，並可確保*prgParamProperties*在輸出上為 null 指標。  
  
## <a name="return-code-values"></a>傳回碼值  
 **GetParameterProperties**方法會傳回與 Core OLE DB **ICommandProperties：： GetProperties**方法相同的錯誤碼，不同之處在于無法引發 DB_S_ERRORSOCCURRED 和 DB_E_ERRORSOCCURED。  
  
## <a name="remarks"></a>備註  
 **ISSCommandWithParameters：： GetParameterProperties**的行為一致，與**GetParameterInfo**有關。 如果尚未呼叫[ISSCommandWithParameters：： SetParameterProperties](isscommandwithparameters-setparameterproperties-ole-db.md)或**SetParameterInfo** ，或已使用 cParams 等於零的呼叫， **GetParameterInfo**會衍生參數資訊，並傳回這個。 如果至少已針對一個參數呼叫**ISSCommandWithParameters：： SetParameterProperties**或**SetParameterInfo** ， **ISSCommandWithParameters：： GetParameterProperties**只會針對已呼叫**ISSCommandWithParameters：： SetParameterProperties**的參數傳回屬性。 如果在**ISSCommandWithParameters：： GetParameterProperties**或**GetParameterInfo**之後呼叫**ISSCommandWithParameters：： SetParameterProperties** ，則對**ISSCommandWithParameters：： GetParameterProperties**的後續呼叫會針對已呼叫**ISSCommandWithParameters：： SetParameterProperties**的參數傳回覆寫的值。  
  
 SSPARAMPROPS 結構定義如下：  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
|member|描述|  
|------------|-----------------|  
|*iOrdinal*|所傳遞參數的序數。|  
|*cPropertySets*|*rgPropertySets* 中的 DBPROPSET 結構數目。|  
|*rgPropertySets*|藉其傳回 DBPROPSET 結構陣列的記憶體指標。|  
  
## <a name="see-also"></a>另請參閱  
 [ISSCommandWithParameters &#40;OLE DB&#41;](isscommandwithparameters-ole-db.md)  
  
  
