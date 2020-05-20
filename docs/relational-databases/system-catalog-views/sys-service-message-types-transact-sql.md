---
title: sys.databases service_message_types （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.service_message_types
- service_message_types
- sys.service_message_types_TSQL
- service_message_types_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.service_message_types catalog view
ms.assetid: 6a38709a-60fe-46f6-89da-718f74f15600
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d5c2b7a1ca52a22a189395164544ff6fb8adb687
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831326"
---
# <a name="sysservice_message_types-transact-sql"></a>sys.service_message_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  這份目錄檢視針對在 Service Broker 中登錄的每一種訊息類型，各包含一個資料列。
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|訊息類型的名稱，它在資料庫中是唯一的。 不是 NULLABLE。|  
|**message_type_id**|**int**|訊息類型的識別碼，它在資料庫中是唯一的。 不是 NULLABLE。|  
|**principal_id**|**int**|擁有這個訊息類型的資料庫主體識別碼。 NULLABLE。|  
|**驗證**|**char(2)**|在傳送這種類型的訊息之前，已由 Broker 完成的驗證。 不是 NULLABLE。 值為下列其中之一：<br /><br /> N = 無<br /><br /> X = XML<br /><br /> E = 空的|  
|**validation_desc**|**nvarchar(60)**|在傳送這種類型的訊息之前，已由 Broker 完成的驗證描述。 NULLABLE。 值為下列其中之一：<br /><br /> 無<br /><br /> XML<br /><br /> EMPTY|  
|**xml_collection_id**|**int**|如果是使用 XML 結構描述來進行驗證，則使用該結構描述集合的識別碼。<br /><br /> 否則為 NULL。|  
  
## <a name="permissions"></a>權限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
  
