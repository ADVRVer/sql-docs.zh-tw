---
title: "Invoke-processcube 指令程式 |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b10ba7c1-8f10-4e72-9626-f9285e4341fd
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e54ec7316c74bd1551194c318e9a981dff341b72
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="invoke-processcube-cmdlet"></a>Invoke-ProcessCube 指令程式

[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  使用特定的處理類型變數來處理 Cube。  
  
>[!NOTE] 
>這份文件可能包含過時的資訊和範例。 使用 Get-help cmdlet 取得最新。
  
## <a name="syntax"></a>語法  
 `Invoke-ProcessCube [-Name] <System.String> [-Database] <System.String> [-ProcessType] <Microsoft.AnalysisServices.ProcessType> [<CommonParameters>]`  
  
 `Invoke-ProcessCube –DatabaseCube <Microsoft.AnalysisServices.Cube> [-ProcessType] <Microsoft.AnalysisServices.ProcessType> [<CommonParameters>]`  
  
## <a name="description"></a>說明  
 Invoke-ProcessCube 指令程式會將 Cube 處理至您指定的層級。 例如，ProcessFull 會使用全新的資料來覆寫現有的資料。 處理 Cube 時，您必須指定處理類型。 如需詳細資訊，請參閱[處理選項和設定 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md)。  
  
## <a name="parameters"></a>參數  
  
### <a name="-name-string"></a>-名稱\<字串 >  
 指定要處理的 Cube。  
  
|||  
|-|-|  
|必要項？|true|  
|位置？|0|  
|預設值||  
|接受管線輸入？|false|  
|接受萬用字元？|false|  
  
### <a name="-database-string"></a>-資料庫\<字串 >  
 指定 Cube 所屬的資料庫。  
  
|||  
|-|-|  
|必要項？|true|  
|位置？|1|  
|預設值||  
|接受管線輸入？|false|  
|接受萬用字元？|false|  
  
### <a name="-processtype-microsoftanalysisservicesprocesstype"></a>-ProcessType \<Microsoft.AnalysisServices.ProcessType >  
 指定處理類型：ProcessFull、ProcessAdd、ProcessUpdate、ProcessIndexes、ProcessData、ProcessDefault、ProcessClear、ProcessStructure、ProcessCelarStructureOnly、ProcessScriptCache、ProcessRecalc。  
  
|||  
|-|-|  
|必要項？|true|  
|位置？|2|  
|預設值||  
|接受管線輸入？|false|  
|接受萬用字元？|false|  
  
### <a name="-databasecube-microsoftanalysissevicescube"></a>-DatabaseCube \<Microsoft.AnalysisSevices.Cube >  
 指定要處理的 Microsoft.AnalysisServices.Cube 物件。 如果您想要經由管線傳入 Cube 名稱，請使用此參數。  
  
|||  
|-|-|  
|必要項？|true|  
|位置？|具名|  
|預設值||  
|接受管線輸入？|True (ByPropertyName)|  
|接受萬用字元？|false|  
  
### <a name="commonparameters"></a>\<一般參數 >  
 這個指令程式支援一般參數：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。 如需詳細資訊，請參閱 [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)。  
  
## <a name="inputs-and-outputs"></a>輸入和輸出  
 輸入類型是可透過管道傳送至指令程式的物件類型。 傳回類型是指令程式所傳回的物件類型。  
  
|||  
|-|-|  
|輸入|無|  
|輸出|無|  
  
## <a name="example-1"></a>範例 1  
 `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Cubes\Adventure Works > Get-Item .| Invoke-ProcessCube–ProcessType:ProcessDefault`  
  
 此命令會使用管道傳送要處理之 Cube 的識別。  
  
## <a name="example-2"></a>範例 2  
 `PS SQL SERVER:\sqlas\locahost\default > Invoke-ProcessCube “Adventure Works” –database AWTEST –ProcessType:ProcessDefault`  
  
 這個命令會處理 AWTEST 資料庫中的 Adventure Works Cube。   
  
  
