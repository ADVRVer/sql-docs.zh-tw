---
title: MDSCHEMA_INPUT_DATASOURCES 資料列集 |Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- MDSCHEMA_INPUT_DATASOURCES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MDSCHEMA_INPUT_DATASOURCES rowset
ms.assetid: 12482fd5-16e3-4171-9cb0-76d0d4f5308e
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: e256ec44816db43f61c332a76942d27f63cb676b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="mdschemainputdatasources-rowset"></a>MDSCHEMA_INPUT_DATASOURCES 資料列集
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  說明在資料庫內定義的資料來源。  
  
## <a name="rowset-columns"></a>資料列集資料行  
 **MDSCHEMA_INPUT_DATASOURCES**資料列集包含下列資料行。  
  
|資料行名稱|類型指標|長度|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||此資料來源所屬目錄的名稱。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||不支援。|  
|**DATASOURCE_NAME**|**DBTYPE_WSTR**||資料來源物件的名稱。|  
|**DATASOURCE_TYPE**|**DBTYPE_WSTR**||資料來源的類型。 有效值包括：<br /><br /> **關聯式**<br /><br /> **Olap**|  
|**CREATED_ON**|**DBTYPE_DBTIMESTAMP**||建立資料來源的日期。|  
|**LAST_SCHEMA_UPDATE**|**DBTYPE_DBTIMESTAMP**||上次修改資料來源的日期和時間。|  
|**DESCRIPTION**|**DBTYPE_WSTR**||動作的易記描述。|  
|**逾時**|**DBTYPE_UI4**||資料來源的逾時。|  
  
 這個結構描述資料列集並未排序。  
  
## <a name="restriction-columns"></a>限制資料行  
 **MDSCHEMA_INPUT_DATASOURCES**上表中列出的資料行可能會限制資料列集。  
  
|資料行名稱|類型指標|限制狀態|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|選擇性。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|選擇性。|  
|**DATASOURCE_NAME**|**DBTYPE_WSTR**|選擇性。|  
|**DATASOURCE_TYPE**|**DBTYPE_WSTR**|選擇性。|  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB for OLAP 結構描述資料列集](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
