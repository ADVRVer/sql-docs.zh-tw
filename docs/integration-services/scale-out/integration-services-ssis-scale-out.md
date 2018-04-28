---
title: SQL Server Integration Services (SSIS) Scale Out | Microsoft Docs
ms.description: This article provides an overview of the SQL Server Integration Services (SSIS) Scale Out feature, which provides high-performance execution of SSIS packages
ms.custom: ''
ms.date: 12/13/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: scale-out
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dcfbd1c5-c001-4fb7-b9ae-916e49ab6a96
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 7dae1d65334003843ea5ad55143db40f862715a6
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="integration-services-ssis-scale-out"></a>Integration Services (SSIS) 相應放大
SQL Server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS) Scale Out 透過將套件執行散佈到多部電腦，來提供 SSIS 套件的高效能執行。 設定 Scale Out 之後，您可以從 SQL Server Management Studio (SSMS)，透過相應放大模式來平行執行多個套件執行。

## <a name="components"></a>Components
[!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out 包含一個 [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out Master 及一或多個 [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out Worker。

-   相應放大主機負責相應放大管理，以及接收來自使用者的套件執行要求。 如需詳細資訊，請參閱 [Scale Out Master](integration-services-ssis-scale-out-master.md)。

-   Scale Out Worker 會從 Scale Out Master 提取執行工作，並執行套件。 如需詳細資訊，請參閱 [Scale Out Worker](integration-services-ssis-scale-out-worker.md)。

## <a name="configuration-options"></a>設定選項
您可以在下列設定中設定 Scale Out：

-   **在單一電腦上**，其中，Scale Out Master 和 Scale Out Worker 是在同一部電腦上並排執行。

-   **在多部電腦上**其中，每個 Scale Out Worker 都在不同的電腦上。

## <a name="what-you-can-do"></a>您可以採取的方法
設定 Scale Out 之後，您可以執行下列動作：

-   平行執行多個部署至 SSISDB 目錄的套件。 如需詳細資訊，請參閱 [在 Scale Out 中執行套件](run-packages-in-integration-services-ssis-scale-out.md)。

-   管理 Scale Out Manager 應用程式中的 Scale Out 拓撲。 如需詳細資訊，請參閱 [Integration Services Scale Out Manager](integration-services-ssis-scale-out-manager.md)。

## <a name="next-steps"></a>後續步驟
-   [在單一電腦上開始使用 Integration Services (SSIS) Scale Out](get-started-with-ssis-scale-out-onebox.md)

-   [逐步解說：設定 Integration Services 相應放大](walkthrough-set-up-integration-services-scale-out.md)
