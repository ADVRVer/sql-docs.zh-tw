---
title: DBSCHEMA_TABLES 資料列集 |Microsoft 文件
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 06fc718e4d4bde23bfee4240e89d77bcde3bbf50
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "34032059"
---
# <a name="dbschematables-rowset"></a>DBSCHEMA_TABLES 資料列集
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  識別的量值群組和維度內公開為資料表[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]。  
  
## <a name="rowset-columns"></a>資料列集資料行  
 **DBSCHEMA_TABLES**資料列集包含下列資料行。  
  
|資料行名稱|類型指標|長度|Description|  
|-----------------|--------------------|------------|-----------------|  
|**TABLE_CATALOG 排列**|**DBTYPE_WSTR**|255|這個物件所屬之目錄的名稱。|  
|**TABLE_SCHEMA**|**DBTYPE_WSTR**|255|此物件所屬 Cube 的名稱。|  
|**TABLE_NAME**|**DBTYPE_WSTR**|255|物件的名稱，如果**TABLE_TYPE**是**資料表**。|  
|**TABLE_TYPE**|**DBTYPE_WSTR**||資料表的類型。<br /><br /> **資料表**指出物件是量值群組。<br /><br /> **系統資料表**指出物件是維度。|  
|**TABLE_GUID**|**DBTYPE_GUID**||不支援。|  
|**DESCRIPTION**|**DBTYPE_WSTR**||物件的可讀取描述。|  
|**TABLE_PROPID**|**DBTYPE_UI4**||不支援。|  
|**DATE_CREATED**|**DBTYPE_DBTIMESTAMP**||不支援。|  
|**DATE_MODIFIED**|**DBTYPE_DBTIMESTAMP**||上次修改物件的日期。|  
|**TABLE_OLAP_TYPE**|**DBTYPE_WSTR**||物件的 OLAP 類型。<br /><br /> **MEASURE_GROUP**指出物件是量值群組。<br /><br /> **CUBE_DIMENSION**指出物件是維度。|  
  
 排序資料列集**TABLE_TYPE**， **table_catalog 排列**， **TABLE_SCHEMA**，和**TABLE_NAME**。  
  
## <a name="restriction-columns"></a>限制資料行  
 **DBSCHEMA_TABLES**上表中列出的資料行可能會限制資料列集。  
  
|資料行名稱|類型指標|限制狀態|  
|-----------------|--------------------|-----------------------|  
|**TABLE_CATALOG 排列**|**DBTYPE_WSTR**|選擇性|  
|**TABLE_SCHEMA**|**DBTYPE_WSTR**|選擇性|  
|**TABLE_NAME**|**DBTYPE_WSTR**|選擇性|  
|**TABLE_TYPE**|**DBTYPE_WSTR**|選擇性|  
|**TABLE_OLAP_TYPE**|**DBTYPE_WSTR**|選擇性|  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 結構描述資料列集](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  
