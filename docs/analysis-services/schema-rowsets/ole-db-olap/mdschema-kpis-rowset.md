---
title: MDSCHEMA_KPIS 資料列集 |Microsoft 文件
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bbf191fafa07bbc436c9971a5c16f4fb455f78bd
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="mdschemakpis-rowset"></a>MDSCHEMA_KPIS 資料列集
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  描述資料庫內的關鍵效能指標 (KPI)。  
  
## <a name="rowset-columns"></a>資料列集資料行  
 **MDSCHEMA_KPIS**資料列集包含下列資料行。  
  
|資料行名稱|類型指標|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|來源資料庫。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|不支援。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|KPI 的父 Cube。|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**|KPI 的相關量值群組。<br /><br /> 您可以使用此資料行來決定 KPI 的維度性。 如果 「**\<NULL >**」，將會建立維度的所有量值群組的 KPI。<br /><br /> 預設值是"**\<NULL >**"。|  
|**KPI_NAME**|**DBTYPE_WSTR**|KPI 的名稱。|  
|**KPI_CAPTION**|**DBTYPE_WSTR**|與 KPI 相關聯的標籤或標題。 主要用於顯示用途。 如果標題不存在， **KPI_NAME**傳回。|  
|**KPI_DESCRIPTION**|**DBTYPE_WSTR**|人們可讀取的 KPI 描述。|  
|**KPI_DISPLAY_FOLDER**|**DBTYPE_WSTR**|識別用戶端應用程式用於顯示成員之顯示資料夾路徑的字串。 資料夾層級的分隔符號是由用戶端應用程式所定義。 工具和用戶端所提供的[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]，反斜線 (\\) 為層級分隔符號。 若要提供多個顯示資料夾，請使用分號 （;） 來分隔資料夾。|  
|**KPI_VALUE**|**DBTYPE_WSTR**|KPI 值之量值維度中成員的唯一名稱。|  
|**KPI_GOAL**|**DBTYPE_WSTR**|KPI Goal 之量值維度中成員的唯一名稱。<br /><br /> 傳回**NULL**不是否有定義任何目標。|  
|**KPI_STATUS**|**DBTYPE_WSTR**|KPI Status 的量值維度中成員的唯一名稱。<br /><br /> 傳回**NULL**沒有定義狀態。|  
|**KPI_TREND**|**DBTYPE_WSTR**|KPI Trend 的量值維度中成員的唯一名稱。<br /><br /> 傳回**NULL**是否有任何定義的趨勢。|  
|**KPI_STATUS_GRAPHIC**|**DBTYPE_WSTR**|KPI 預設圖形表示。|  
|**KPI_TREND_GRAPHIC**|**DBTYPE_WSTR**|KPI 預設圖形表示。|  
|**KPI_WEIGHT**|**DBTYPE_WSTR**|KPI Weight 之量值維度中成員的唯一名稱。|  
|**KPI_CURRENT_TIME_MEMBER**|**DBTYPE_WSTR**|定義 KPI 暫時內容之時間維度中成員的唯一名稱。<br /><br /> 傳回**NULL**如果沒有定義 Time 成員。|  
|**KPI_PARENT_KPI_NAME**|**DBTYPE_WSTR**|父 KPI 的名稱。|  
|**範圍**|**DBTYPE_I4**|KPI 的範圍。 KPI 可以是工作階段 KPI 或是全域 KPI。<br /><br /> 此資料行可以有下列其中一個值：<br /><br /> MDKPI_SCOPE_GLOBAL=1<br /><br /> MDKPI_SCOPE_SESSION=2|  
|**註解**|**DBTYPE_WSTR**|(選擇性) 一組注意事項 (以 XML 格式表示)。|  
  
 這個結構描述資料列集並未排序。  
  
## <a name="restriction-columns"></a>限制資料行  
 **MDSCHEMA_KPIS**上表中列出的資料行可能會限制資料列集。  
  
|資料行名稱|類型指標|限制狀態|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|選擇性。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|選擇性。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|選擇性。|  
|**KPI_NAME**|**DBTYPE_WSTR**|選擇性。|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|（選擇性）預設限制為值的**1**。 點陣圖，下列有效的值之一：<br /><br /> **1** CUBE<br /><br /> **2**維度|  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB for OLAP 結構描述資料列集](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
