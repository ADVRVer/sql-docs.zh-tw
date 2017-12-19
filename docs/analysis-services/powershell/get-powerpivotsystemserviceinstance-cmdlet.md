---
title: "Get-powerpivotsystemserviceinstance 指令程式 |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 56027a8e-1949-4349-b616-68c8b1d2963c
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2e52176bc32adbaee46a22d3c4df6a331cf7c39b
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2017
---
# <a name="get-powerpivotsystemserviceinstance-cmdlet"></a>Get-PowerPivotSystemServiceInstance 指令程式
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]傳回的一或多個執行個體[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]伺服陣列中的應用程式伺服器上執行的系統服務。  

>[!NOTE] 
>這份文件可能包含過時的資訊和範例。 使用 Get-help cmdlet 取得最新。
  
 **適用於** ：SharePoint 2010 和 SharePoint 2013。  
  
## <a name="syntax"></a>語法  
  
```  
Get-PowerPivotSystemServiceInstance [-Identity <PowerPivotMidTierServiceInstancePipeBind>] [<CommonParameters>]  
```  
  
## <a name="description"></a>說明  
 Get-PowerPivotSystemServiceInstance Cmdlet 會傳回在伺服器陣列中執行的一或多個 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 系統服務執行個體的屬性。 此指令程式會報告應用程式類型、狀態 (線上或離線) 和識別。 若要檢視特定執行個體的其他屬性，請將 Identity 參數和 format-list 選項加入至指令程式中。  
  
## <a name="parameters"></a>參數  
  
### <a name="-identity-powerpivotmidtierserviceinstancepipebind"></a>識別\<PowerPivotMidTierServiceInstancePipeBind >  
 指定要取得的服務執行個體。 值必須是可在伺服器陣列中唯一識別物件的有效 GUID。  
  
|||  
|-|-|  
|必要項？|false|  
|位置？|0|  
|預設值||  
|接受管線輸入？|true|  
|接受萬用字元？|false|  
  
### <a name="commonparameters"></a>\<一般參數 >  
 這個指令程式支援一般參數：Verbose、Debug、ErrorAction、ErrorVariable、WarningAction、WarningVariable、OutBuffer 和 OutVariable。 如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)。  
  
## <a name="inputs-and-outputs"></a>輸入和輸出  
 輸入類型是可透過管道傳送至指令程式的物件類型。 傳回類型是指令程式所傳回的物件類型。  
  
|||  
|-|-|  
|輸入|無。|  
|輸出|無。|  
  
## <a name="example-1"></a>範例 1  
  
```  
C:\PS>Get-PowerPivotSystemServiceInstance -Identity 1234567-890a-bcde-fghijklm | format-list| format-list  
```  
  
 這個範例會傳回指定之執行個體的其他屬性，包括伺服器名稱、版本和升級狀態。  
  
  
