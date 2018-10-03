---
title: SetDefaults 方法 （ServerSettings 類別） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- SetDefaults Method (ServerSettings Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: 76e4cfab-4b15-4da4-bb2f-8aac6f927f79
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 8454317ff08a4576970c2ffc448605ac5825f1d1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48080138"
---
# <a name="setdefaults-method-serversettings-class"></a>SetDefaults 方法 (ServerSettings 類別)
  設定執行個體的所有預設值[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]覆寫現有資料的選項。  
  
## <a name="syntax"></a>語法  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a>組件  
 *object*  
 A [ServerSettings 類別](serversettings-class.md)物件，表示[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]用戶端執行個體。  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|*OverwriteAll*|指定是否要覆寫 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體上之現有值的布林值。`true` 表示要覆寫現有的資料，`false` 表示不覆寫現有的資料。|  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 u`int32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [設定伺服器網路通訊協定和網路程式庫](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
