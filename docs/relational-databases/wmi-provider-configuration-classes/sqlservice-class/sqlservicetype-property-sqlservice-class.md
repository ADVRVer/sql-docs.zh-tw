---
description: SqlServiceType 屬性 (SqlService 類別)
title: 'SqlServiceType 屬性 (SqlService) '
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SqlServiceType Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SqlServiceType property
ms.assetid: dbff2968-3011-41d6-a141-52d814af0213
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 685fb402647c7a757f7a894705cf7754d696b24d
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89542803"
---
# <a name="sqlservicetype-property-sqlservice-class"></a>SqlServiceType 屬性 (SqlService 類別)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  取得受管理之服務的類型。  
  
## <a name="syntax"></a>語法  
  
```  
  
object.SqlServiceType [= value]  
```  
  
## <a name="parts"></a>組件  
 *object*  
 表示此服務的 [SqlService 類別](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) 物件。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 指定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務類型的 uint32 值。  
  
## <a name="remarks"></a>備註  
 傳回值可以是下列其中一個：  
  
|類型|定義|  
|----------|----------------|  
|*1*|MSSQLSERVER 是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務。|  
|*2*|SQLSERVERAGENT 是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 服務。|  
|*3*|MSFTESQL 是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 全文檢索搜尋引擎服務。|  
|*4*|MsDtsServer 是 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 服務。|  
|*5*|MSSQLServerOLAPService 是 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 服務。|  
|*6*|ReportServer 是 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 服務。|  
|*7*|SQLBrowser 是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Browser 服務。|  
|*8*|Nsservice.exe 是 [!INCLUDE[ssNoVersion](../../../includes/ssns-md.md)] 通知服務。|  
|*9*|MSSQLFDLauncher 是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 全文檢索篩選背景程式啟動器服務。|  
|*10*|SQLPBENGINE 是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Polybase 引擎服務。|  
|*11*|SQLPBDMS 是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Polybase 資料移動服務。|  
|*12*|MSSQLLaunchpad 是啟動控制 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 板服務。|  
  
## <a name="see-also"></a>另請參閱  
 [啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
