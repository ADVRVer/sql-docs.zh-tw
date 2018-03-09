---
title: "Azure HDInsight 刪除叢集工作 | Microsoft Docs"
ms.custom: 
ms.date: 02/28/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: control-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.afpdelcltask.f1
- sql14.dts.designer.afpdelcltask.f1
ms.assetid: e298776e-d18a-4393-a8e6-65ee3d555749
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: db580410f37f1310ccc2bf30f6620157fcb60cf9
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="azure-hdinsight-delete-cluster-task"></a>Azure HDInsight 刪除叢集工作
**Azure HDInsight 刪除叢集工作**可讓 SSIS 套件刪除指定之 Azure 訂用帳戶和資源群組中的 Azure HDInsight 叢集。
  
**Azure HDInsight 刪除叢集工作**是 [Azure SQL Server Integration Services (SSIS) Feature Pack](../../integration-services/azure-feature-pack-for-integration-services-ssis.md) 的元件。
  
> [!NOTE]
> 刪除 HDInsight 叢集可能需要 10~20 分鐘。  
  
若要加入 **Azure HDInsight 刪除叢集工作**，請將其拖放至 SSIS 設計工具，並按兩下或在其上按一下滑鼠右鍵，然後按一下 [編輯]  ，即可看到以下 [Azure HDInsight 刪除叢集工作編輯器]  對話方塊。  
  
下表提供此對話方塊中欄位的描述。  
  
|||  
|-|-|  
|**欄位**|**說明**|  
|AzureResourceManagerConnection|選取現有的 Azure Resource Manager 連線管理員或建立新的連線管理員，以用來刪除 HDInsight 叢集。|
|SubscriptionId|指定 HDInsight 叢集所在的訂用帳戶 ID。|
|ResourceGroup|指定 HDInsight 叢集所在的 Azure 資源群組。|
|ClusterName|指定要刪除之叢集的名稱。|  
|FailIfNotExists|指定若叢集不存在則工作是否會失敗。|
