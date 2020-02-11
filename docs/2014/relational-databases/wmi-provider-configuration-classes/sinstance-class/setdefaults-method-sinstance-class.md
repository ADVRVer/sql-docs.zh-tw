---
title: SetDefaults 方法（SInstance 類別） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDefaults Method (SInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: dc3c6a85-0711-4688-bf4f-91168c57af28
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: ad13821341291a91a989297f29e1459a40de5afe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "62720944"
---
# <a name="setdefaults-method-sinstance-class"></a>SetDefaults 方法 (SInstance 類別)
  使用覆寫現有資料的選項，設定[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]實例的所有預設值。  
  
## <a name="syntax"></a>語法  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a>組件  
 *目標*  
 代表伺服器實例的[SInstance 類別](sinstance-class.md)物件。  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|*OverwriteAll*|指定是否要覆寫 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 用戶端執行個體上之現有值的布林值：`true` 表示要覆寫現有的資料，`false` 表示不覆寫現有的資料。|  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 
  `uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [設定伺服器網路通訊協定與網路程式庫](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
