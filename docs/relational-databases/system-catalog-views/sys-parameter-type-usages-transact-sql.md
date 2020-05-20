---
title: sys.databases parameter_type_usages （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.parameter_type_usages
- sys.parameter_type_usages_TSQL
- parameter_type_usages_TSQL
- parameter_type_usages
dev_langs:
- TSQL
helpviewer_keywords:
- sys.parameter_type_usages catalog view
ms.assetid: af0e167b-bffb-4525-84ec-3607f9268d3d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f0302cac5c0076849132ebef7904bd0d53d09208
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825027"
---
# <a name="sysparameter_type_usages-transact-sql"></a>sys.parameter_type_usages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  針對每個使用者自訂類型參數，各傳回一個資料列。  
  
> [!NOTE]  
>  這份檢視不會傳回編號程序的參數資料列。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|這個參數所屬物件的識別碼。|  
|**parameter_id**|**int**|參數的識別碼。 在物件中，這是唯一的。|  
|**user_type_id**|**int**|使用者自訂類型的識別碼。<br /><br /> 若要傳回類型的名稱，請在此資料行上加入[sys.databases](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)目錄檢視。|  
  
## <a name="permissions"></a>權限  
 需要 **public** 角色的成員資格。  如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [純量類型目錄檢視 &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)   
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
