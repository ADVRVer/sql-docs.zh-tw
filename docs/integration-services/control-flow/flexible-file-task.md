---
title: 彈性檔案工作 | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPEXTFILETASK.F1
- SQL14.DTS.DESIGNER.AFPEXTFILETASK.F1
author: janinezhang
ms.author: janinez
ms.openlocfilehash: cc95201ec856d5e7daa998c7de52b91981af5552
ms.sourcegitcommit: 2efb0fa21ff8093384c1df21f0e8910db15ef931
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2019
ms.locfileid: "68316633"
---
# <a name="flexible-file-task"></a>彈性檔案工作

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

彈性檔案工作讓使用者能夠在各種支援的儲存體服務上執行檔案作業。
以下為目前支援的儲存體服務：

- 本機檔案系統
- [Azure Blob 儲存體](https://azure.microsoft.com/services/storage/blobs/)
- [Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction) \(部分機器翻譯\)

彈性檔案工作是 [SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md) 的元件。

若要將彈性檔案工作新增至套件，請將它從 SSIS 工具箱拖曳至設計師畫布。 接著，按兩下該工作，或以滑鼠右鍵按一下該工作並選取 [編輯]  ，以開啟 [彈性檔案工作編輯器]  對話方塊。

**作業**屬性會指定要執行的檔案作業。
目前僅支援**複製**作業。

目前已針對**複製**作業提供下列屬性。

- **SourceConnectionType：** 指定來源連線管理員類型。
- **SourceConnection：** 指定來源連線管理員。
- **SourceFolderPath：** 指定來源資料夾路徑。
- **SourceFileName：** 指定來源檔案名稱。 如果保留空白，將會複製來源資料夾。
- **SearchRecursively：** 指定是否要以遞迴方式複製子資料夾。
- **DestinationConnectionType：** 指定目的地連線管理員類型。
- **DestinationConnection：** 指定目的地連線管理員。
- **DestinationFolderPath：** 指定目的地資料夾路徑。
- **DestinationFileName：** 指定目的地檔案名稱。

***服務主體權限設定的注意事項***

若要讓**測試連線**正常執行 (Blob 儲存體或 Data Lake Storage Gen2)，則應將服務主體至少指派給儲存體帳戶的**儲存體 Blob 資料讀取者**角色。
此操作可透過 [RBAC](https://docs.microsoft.com/azure/storage/common/storage-auth-aad-rbac-portal#assign-rbac-roles-using-the-azure-portal) 完成。

針對 Blob 儲存體，指派至少**儲存體 Blob 資料讀取者**和**儲存體 Blob 資料參與者**角色來分別授與讀取和寫入權限。

針對 Data Lake Storage Gen2，權限由 RBAC 和 [ACL](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-how-to-set-permissions-storage-explorer) 決定。
請注意，ACL 會使用應用程式註冊服務主體的物件識別碼 (OID) 進行設定，如[此處](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-access-control#how-do-i-set-acls-correctly-for-a-service-principal)所詳述。
這不同於與 RBAC 設定搭配使用的應用程式 (用戶端) 識別碼。
當安全性主體透過內建角色或自訂角色獲得 RBAC 資料權限時，在要求授權時會先評估這些權限。
如果要求作業是由安全性主體的 RBAC 指派授權，則會立即解決授權，且不會執行任何額外的 ACL 檢查。
或者，如果安全性主體不具有 RBAC 指派，或要求作業不符合指派的權限，則會執行 ACL 檢查來判斷安全性主體是否已獲授權執行要求作業。

- 針對讀取權限，請至少授與**執行**權限 (從來源檔案系統開始)，以及所要複製檔案的**讀取**權限。 或者，使用 RBAC 至少授與**儲存體 Blob 資料讀取者**角色。
- 針對寫入權限，請至少授與**執行**權限 (從接收檔案系統開始)，以及接收資料夾的**寫入**權限。 或者，使用 RBAC 至少授與**儲存體 Blob 資料參與者**角色。

如需詳細資料，請參閱[這篇](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-access-control)文章。
