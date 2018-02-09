---
title: "建立方法 (ADOX) |Microsoft 文件"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Catalog::raw_Create
- _Catalog::Create
helpviewer_keywords:
- Create method [ADOX]
ms.assetid: 64f5c21c-b581-42d8-bdc7-c4f1bebaf105
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 81c480c08a9d214ab8d35730c4aa34465d418d27
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="create-method-adox"></a>建立方法 (ADOX)
建立新的目錄。  
  
## <a name="syntax"></a>語法  
  
```  
  
Catalog.Create ConnectString  
```  
  
#### <a name="parameters"></a>參數  
 *ConnectString*  
 A**字串**用來連接到資料來源的值。  
  
## <a name="remarks"></a>備註  
 **建立**方法會建立並開啟新的 ADO[連接](../../../ado/reference/ado-api/connection-object-ado.md)中指定的資料來源*ConnectString*。 如果成功，新**連接**物件指派給[ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md)屬性。  
  
 如果提供者不支援建立新的目錄，就會發生錯誤。  
  
## <a name="applies-to"></a>適用於  
 [Catalog 物件 (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>另請參閱  
 [Create 方法範例 (VB)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [ActiveConnection 屬性 (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)
