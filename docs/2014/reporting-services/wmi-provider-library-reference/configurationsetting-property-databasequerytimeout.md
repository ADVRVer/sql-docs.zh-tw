---
title: DatabaseQueryTimeout 屬性 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- DatabaseQueryTimeout Property
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseQueryTimeout property
ms.assetid: 96faed97-9799-4bbf-a66f-fdd532d3eace
caps.latest.revision: 35
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: bcfd675860851b62dd2868adae00c6f6f13f6357
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36035827"
---
# <a name="databasequerytimeout-property-wmi-msreportserverconfigurationsetting"></a>DatabaseQueryTimeout 屬性 (WMI MSReportServer_ConfigurationSetting)
  指定在報表伺服器認定命令失敗，或是花太多時間執行之前必須經過的秒數。 報表伺服器會針對 SQL 目錄，而不是報表資料來源排定查詢的時間。 讀取/寫入  
  
## <a name="syntax"></a>語法  
  
```vb  
Public Dim DatabaseQueryTimeout As UInt32  
```  
  
```csharp  
public UInt32 DatabaseQueryTimeout;  
```  
  
## <a name="property-values"></a>屬性值  
 32 位元不帶正負號`integer`物件，代表查詢允許執行的秒數。  
  
## <a name="example-code"></a>範例程式碼  
 [MSReportServer_ConfigurationSetting 類別](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>需求  
 **命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [MSReportServer_ConfigurationSetting 成員](msreportserver-configurationsetting-members.md)  
  
  