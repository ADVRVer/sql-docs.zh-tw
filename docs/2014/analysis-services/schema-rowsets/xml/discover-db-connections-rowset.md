---
title: DISCOVER_DB_CONNECTIONS 資料列集 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DISCOVER_DB_CONNECTIONS rowset
ms.assetid: 12a51a4e-5f3d-4449-9d94-7836fea1bc8b
caps.latest.revision: 18
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f22c330fcc1deef1e86f4442ed8524235a3ba5c0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37295548"
---
# <a name="discoverdbconnections-rowset"></a>DISCOVER_DB_CONNECTIONS 資料列集
  提供有關目前從伺服器到資料庫之間已開啟之連接的資源使用量與活動資訊。  
  
## <a name="rowset-columns"></a>資料列集資料行  
 `DISCOVER_DB_CONNECTIONS`資料列集包含下列資料行。  
  
|資料行名稱|類型指標|長度|描述|  
|-----------------|--------------------|------------|-----------------|  
|`CONNECTION_CATALOG_NAME`|`DBTYPE_WSTR`||目前連接之資料庫的資料庫名稱。|  
|`CONNECTION_ID`|`DBTYPE_I4`||識別連接的唯一號碼。|  
|`CONNECTION_IDLE_TIME_MS`|`DBTYPE_I8`||自從連接啟動以後的閒置時間，以毫秒為單位。|  
|`CONNECTION_IN_USE`|`DBTYPE_I4`||指出連接是使用中 (1) 或是閒置 (0)。|  
|`CONNECTION_LAST_COMMAND_END_TIME`|`DBTYPE_DBTIMESTAMP`||當上一個命令完成其執行時，伺服器的 UTC 日期與時間。|  
|`CONNECTION_LAST_COMMAND_START_TIME`|`DBTYPE_DBTIMESTAMP`||當上一個命令起始其執行時，伺服器的 UTC 日期與時間。|  
|`CONNECTION_SERVER_NAME`|`DBTYPE_WSTR`||目前連接的伺服器名稱。|  
|`CONNECTION_SPID`|`DBTYPE_I4`||工作階段識別碼。|  
|`CONNECTION_START_TIME`|`DBTYPE_DBTIMESTAMP`||連接起始時，伺服器的 UTC 日期和時間。|  
|`CONNECTION_USAGE_TIME_MS`|`DBTYPE_I8`||自從連接啟動之後的連接使用中時間，以毫秒為單位。|  
  
 這個結構描述資料列集並未排序。  
  
> [!IMPORTANT]  
>  `DISCOVER_DB_CONNECTIONS` 資料列集將只會在服務連接到關聯式資料來源時顯示資訊。  
  
## <a name="restriction-columns"></a>限制資料行  
 在下表列出的資料行上可能會限制 `DISCOVER_DB_CONNECTIONS` 資料列集。  
  
|資料行名稱|類型指標|限制狀態|  
|-----------------|--------------------|-----------------------|  
|CONNECTION_ID|DBTYPE_I4|選擇性。|  
|CONNECTION_IN_USE|DBTYPE_I4|選擇性。|  
|CONNECTION_SERVER_NAME|DBTYPE_WSTR|選擇性。|  
|CONNECTION_CATALOG_NAME|DBTYPE_WSTR|必要。|  
|CONNECTION_SPID|DBTYPE_I4|選擇性。|  
  
## <a name="see-also"></a>另請參閱  
 [XML for Analysis 結構描述資料列集](xml-for-analysis-schema-rowsets.md)  
  
  
