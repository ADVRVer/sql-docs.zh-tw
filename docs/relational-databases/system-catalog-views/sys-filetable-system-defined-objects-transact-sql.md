---
title: sys.filetable_system_defined_objects (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.filetable_system_defined_objects_TSQL
- filetable_system_defined_objects
- filetable_system_defined_objects_TSQL
- sys.filetable_system_defined_objects
dev_langs:
- TSQL
helpviewer_keywords:
- sys.filetable_system_defined_objects catalog view
ms.assetid: 62022e6b-46f6-495f-b14b-53f41e040361
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: a9d4cdb95349c9af9416caca7ca8dcf8893c0b4d
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="sysfiletablesystemdefinedobjects-transact-sql"></a>sys.filetable_system_defined_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  顯示與 FileTable 相關的系統定義物件清單。 針對每個系統定義物件，各包含一個資料列。  
  
 當您建立 FileTable 時，同時會建立相關物件，例如條件約束和索引。 您不能改變或卸除這些物件，只有當 FileTable 本身卸除時它們才會消失。  
  
 如需有關 FileTable 的詳細資訊，請參閱 [FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md)。  
  
|資料行|資料類型|Description|  
|------------|---------------|-----------------|  
|**object_id**|**int**|與 FileTable 相關的系統定義物件的物件識別碼。<br /><br /> 參考中的物件**sys.objects**。|  
|**parent_object_id**|**int**|父 FileTable 的物件識別碼。<br /><br /> 參考中的物件**sys.objects**。|  
  
## <a name="see-also"></a>另請參閱  
 [建立、改變及卸除 FileTable](../../relational-databases/blob/create-alter-and-drop-filetables.md)   
 [管理 FileTable](../../relational-databases/blob/manage-filetables.md)  
  
  
