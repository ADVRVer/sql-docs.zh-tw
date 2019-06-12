---
title: 適用於 Integration Services (SSIS) 的 Azure Feature Pack | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.SSIS.AZURE.F1
- SQL14.SSIS.AZURE.F1
ms.assetid: 31de555f-ae62-4f2f-a6a6-77fea1fa8189
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 29e30a8a7da41bcb7c75c61ef5ed78d0e3096536
ms.sourcegitcommit: fc0eb955b41c9c508a1fe550eb5421c05fbf11b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66403178"
---
# <a name="azure-feature-pack-for-integration-services-ssis"></a>Azure Feature Pack for Integration Services (SSIS)

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


SQL Server Integration Services (SSIS) Feature Pack for Azure 是一個延伸模組，可提供此頁面上所列的元件，以便讓 SSIS 連接到 Azure 服務、在 Azure 和內部部署資料來源之間轉送資料，以及處理儲存在 Azure 中的資料。

[![下載 SSIS Feature Pack for Azure](../analysis-services/media/download.png)](https://www.microsoft.com/download/details.aspx?id=54798) **下載**

- SQL Server 2017 - [Microsoft SQL Server 2017 Integration Services Feature Pack for Azure](https://www.microsoft.com/download/details.aspx?id=54798)
- SQL Server 2016 - [Microsoft SQL Server 2016 Integration Services Feature Pack for Azure](https://www.microsoft.com/download/details.aspx?id=49492)
- SQL Server 2014 - [Microsoft SQL Server 2014 Integration Services Feature Pack for Azure](https://www.microsoft.com/download/details.aspx?id=47366)
- SQL Server 2012 - [Microsoft SQL Server 2012 Integration Services Feature Pack for Azure](https://www.microsoft.com/download/details.aspx?id=47367)

下載頁面也包含必要條件的相關資訊。 請確定您在伺服器上安裝 Azure Feature Pack 之前安裝 SQL Server，或當您將套件部署至伺服器上的 SSIS 目錄資料庫 (SSISDB) 時，Feature Pack 中的元件可能無法使用。

## <a name="components-in-the-feature-pack"></a>Feature Pack 中的元件
-   連接管理員

    -   [Azure Data Lake Analytics Connection Manager](connection-manager/azure-data-lake-analytics-connection-manager.md)

    -   [Azure Data Lake Store 連線管理員](../integration-services/connection-manager/azure-data-lake-store-connection-manager.md)
    
    -   [Azure HDInsight 連線管理員](../integration-services/connection-manager/azure-hdinsight-connection-manager.md)

    -   [Azure Resource Manager 連線管理員](../integration-services/connection-manager/azure-resource-manager-connection-manager.md)
    
    -   [Azure 儲存體連線管理員](../integration-services/connection-manager/azure-storage-connection-manager.md)

    -   [Azure 訂用帳戶連線管理員](../integration-services/connection-manager/azure-subscription-connection-manager.md)
    
-   工作

    -   [Azure Blob 下載工作](../integration-services/control-flow/azure-blob-download-task.md)

    -   [Azure Blob 上傳工作](../integration-services/control-flow/azure-blob-upload-task.md)

    -   [Azure Data Lake Analytics 工作](control-flow/azure-data-lake-analytics-task.md)

    -   [Azure Data Lake Store 檔案系統工作](../integration-services/control-flow/azure-data-lake-store-file-system-task.md)

    -   [Azure HDInsight 建立叢集工作](../integration-services/control-flow/azure-hdinsight-create-cluster-task.md)

    -   [Azure HDInsight 刪除叢集工作](../integration-services/control-flow/azure-hdinsight-delete-cluster-task.md)
    
    -   [Azure HDInsight Hive 工作](../integration-services/control-flow/azure-hdinsight-hive-task.md)

    -   [Azure HDInsight Pig 工作](../integration-services/control-flow/azure-hdinsight-pig-task.md)

    -   [Azure SQL DW 上傳工作](../integration-services/control-flow/azure-sql-dw-upload-task.md)

    -   [彈性檔案工作](../integration-services/control-flow/flexible-file-task.md)

-   資料流程元件

    -   [Azure Blob 來源](../integration-services/data-flow/azure-blob-source.md)

    -   [Azure Blob 目的地](../integration-services/data-flow/azure-blob-destination.md)
    
    -   [Azure Data Lake Store 來源](../integration-services/data-flow/azure-data-lake-store-source.md)
    
    -   [Azure Data Lake Store 目的地](../integration-services/data-flow/azure-data-lake-store-destination.md)

    -   [彈性檔案來源](../integration-services/data-flow/flexible-file-source.md)

    -   [彈性檔案目的地](../integration-services/data-flow/flexible-file-destination.md)

-   Azure Blob、Azure Data Lake Store 和 Data Lake Storage Gen2 檔案列舉程式。 請參閱 [Foreach 迴圈容器](../integration-services/control-flow/foreach-loop-container.md)

## <a name="scenario-processing-big-data"></a>案例：處理巨量資料
 您可以使用 Azure 連接器來完成下列巨量資料處理工作：

1.  使用 Azure Blob 上傳工作，將輸入資料上傳至 Azure Blob 儲存體。

2.  使用 Azure HDInsight 建立叢集工作，建立 Azure HDInsight 叢集。 如果您要使用自己的叢集，這是選擇性步驟。

3.  使用 Azure HDInsight 登錄區工作或 Azure HDInsight Pig 工作，在 Azure HDInsight 叢集上叫用 Pig 或登錄區工作。

4.  如果在步驟 2 中建立了隨選 HDInsight 叢集，在使用過後，可使用 Azure HDInsight 刪除叢集工作來刪除該 HDInsight 叢集。

5.  使用 Azure HDInsight Blob 下載工作，從 Azure Blob 儲存體下載 Pig/登錄區輸出資料。

![SSIS-AzureConnector-BigDataScenario](../integration-services/media/ssis-azureconnector-bigdatascenario.png)
 
## <a name="scenario-managing-data-in-the-cloud"></a>案例：管理雲端中的資料
 您可以使用 SSIS 封裝中的 Azure Blob 目的地，將輸出資料寫入 Azure Blob 儲存體，或者使用 Azure Blob 來源，從 Azure Blob 儲存體讀取資料。

![SSIS-AzureConnector-CloudArchive-1](../integration-services/media/ssis-azureconnector-cloudarchive-1.png)
 
 ![SSIS-AzureConnector-CloudArchive-2](../integration-services/media/ssis-azureconnector-cloudarchive-2.png)

 您可以搭配 Azure Blob 列舉程式使用 Foreach 迴圈容器，來處理多個 Bob 檔案中的資料。

![SSIS-AzureConnector-CloudArchive-3](../integration-services/media/ssis-azureconnector-cloudarchive-3.png)
  
