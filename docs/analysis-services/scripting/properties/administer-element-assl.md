---
title: Administer 元素 (ASSL) |Microsoft 文件
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 823f9ef44da2c718f8e0d355cf402581976fb0c7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "34035249"
---
# <a name="administer-element-assl"></a>Administer 元素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  指出相關聯的權限是否包含管理權[資料庫](../../../analysis-services/scripting/objects/database-element-assl.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<DatabasePermission>  
      ...  
      <Administer>...</Administer>  
   ...  
</DatabasePermission>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|布林|  
|預設值|False|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[DatabasePermission](../../../analysis-services/scripting/objects/databasepermission-element-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 **管理**元素會指出使用者是否可以只在指定的資料庫上執行管理功能。 伺服器管理員角色可以在此執行個體包含的所有資料庫上執行管理功能。  
  
 對應目的父代的項目**管理**在 「 分析管理物件 (AMO) 物件模型而言， <xref:Microsoft.AnalysisServices.DatabasePermission>。  
  
## <a name="see-also"></a>另請參閱  
 [Permission 資料類型 & #40;ASSL & #41;](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)   
 [Role 元素 & #40;ASSL & #41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [屬性 & #40;ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
