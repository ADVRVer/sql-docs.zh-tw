---
title: "記錄屬性選項 (緩時變維度精靈) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.loaddimwizard.histattriboption.f1"
ms.assetid: a176ec66-ec39-4c99-99d1-c1afa8450e1e
caps.latest.revision: 22
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 22
---
# 記錄屬性選項 (緩時變維度精靈)
  使用 [記錄屬性選項] 對話方塊，依開始和結束日期來顯示記錄屬性，或者在基於此目的而建立的資料行中記錄記錄屬性。  
  
 若要深入了解這個精靈，請參閱＜ [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md)＞。  
  
## 選項。  
 **使用單一資料行顯示目前與逾期記錄**  
 如果您選擇使用單一資料行來記錄記錄屬性的狀態，則可以使用下列選項：  
  
|選項|說明|  
|------------|-----------------|  
|**指出目前記錄的資料行**|選取要指出目前記錄的資料行。|  
|**目前值**|使用 [True] 或 [目前] 來顯示記錄是否為目前的。|  
|**逾期值**|使用 [False] 或 [逾期] 來顯示記錄是否為記錄值。|  
  
 **使用開始和結束日期以識別目前與逾期記錄**  
 此選項的維度資料表必須包含日期資料行。 如果您選擇依開始和結束日期顯示記錄屬性，則可以使用下列選項：  
  
|選項|說明|  
|------------|-----------------|  
|**開始日期資料行**|選取維度資料表中的資料行以包含開始日期。|  
|**結束日期資料行**|選取維度資料表中的資料行以包含結束日期。|  
|**設定日期值的變數**|從清單中選取日期變數。|  
  
## 請參閱＜  
 [使用緩時變維度精靈來設定輸出](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  