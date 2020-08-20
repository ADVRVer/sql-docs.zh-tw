---
description: 進階合併式複寫衝突 - 選擇解析程式
title: 選擇解析程式 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- default conflict resolver
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: b7dec3fa-d9d9-409d-b946-f9b9a3202829
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ad013d29b6915f83e4fd80df3e929e4585064b9f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482398"
---
# <a name="advanced-merge-replication-conflict---choose-a-resolver"></a>進階合併式複寫衝突 - 選擇解析程式
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  選擇解決器時，請考慮應用程式中衝突解決的重要性，並考慮是否可使用預設的優先權式衝突解決器還是需要使用發行項解決器。  
  
 如果您的資料分割 (Partition) 方式不會讓多位使用者寫入同一資料分割區，而且您的複寫拓撲相對上比較簡單 (一個「發行者」以及少數幾個「訂閱者」)，那麼衝突發生的機會微乎其微。 在這些環境中，您可能不需要複雜的衝突解決策略。 建議您使用衝突解決方案的預設設定，即利用客訂閱以及先變更者為贏的策略。 如果拓撲較為複雜 (例如使用重新發行「訂閱者」)，則具有特定優先權的主訂閱可能更合適。  
  
 如果業務需求所需的方案比預設解決器能提供的要更為精確，則建議使用發行項解決器。 如果選擇使用發行項解決器，建議使用商務邏輯處理常式。 如需詳細資訊，請參閱[在合併同步處理期間執行商務邏輯](../../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md)。  
  
 最後，選擇是使用預設解決器還是發行項解決器應基於應用程式的資料和商務邏輯需求。 試想員工在不同的「訂閱者」端將客戶排名資料輸入一組未分割的資料表中；員工的工作跨多個類別 (分公司經理、直線經理、銷售人員等)，且由工作類別決定誰的資料優先權較高。 在此情況下，您可以建立一個發行項解決器，使用發行項的工作類別資料來決定發生衝突時的成功者。  
  
 如果偶而會有衝突發生，以下是您在實作衝突解決策略時應考慮的幾個重要決定。  
  
|衝突解決問題|建議|  
|-------------------------------|--------------------|  
|不同類別的使用者需要不同的優先權值。|使用預設解決器，並建立具有不同優先權值的主訂閱。<br /><br /> Or<br /><br /> 使用可在發行項中辨識授權值資料行之發行項解決器來協助解決衝突。|  
|希望使用先改變者為贏的衝突解決方案。|使用預設解決器並建立客訂閱。|  
|可接受多位使用者變更同一個資料列，只要同一資料行沒有衝突變更即可。|使用預設解決器或發行項解決器，並啟用資料行層級追蹤。|  
|以旗標將資料列上任何值的多次變更標示為衝突。|使用預設解決器或發行項解決器，並啟用資料列層級追蹤。|  
|以旗標將邏輯記錄中任何值的多次變更標示為衝突。|使用啟用了邏輯記錄層級追蹤的預設解決器 (邏輯記錄功能不支援自訂解決器或商務邏輯處理常式)。|  
|衝突結果資料需與原始衝突資料不同。|使用可計算新值的發行項解決器。|  
  
## <a name="see-also"></a>另請參閱  
 [Detecting and Resolving Conflicts in Logical Records](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-resolving-in-logical-record.md)   
 [進階合併式複寫衝突偵測與解決](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [重新發行資料](../../../relational-databases/replication/republish-data.md)  
  
  
