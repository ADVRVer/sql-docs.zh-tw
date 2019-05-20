---
title: 在 SSIS 套件部署於 Azure 的情況下開啟和儲存檔案 | Microsoft Docs
description: 了解當您將使用本機檔案系統的 SSIS 套件隨即轉移至 Azure 中的 SSIS 時，如何在內部部署與 Azure 中開啟和儲存檔案
ms.date: 06/27/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: integration-services
author: swinarko
ms.author: sawinark
ms.reviewer: douglasl
manager: craigg
ms.openlocfilehash: 4b8bcbbff8641e2fa8fbd83ca0c7f4d4b40fe172
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2019
ms.locfileid: "65720541"
---
# <a name="open-and-save-files-on-premises-and-in-azure-with-ssis-packages-deployed-in-azure"></a>在 SSIS 套件部署於 Azure 的情況下，於內部部署與 Azure 中開啟和儲存檔案

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



本文描述當您將使用本機檔案系統的 SSIS 套件隨即轉移至 Azure 中的 SSIS 時，如何在內部部署與 Azure 中開啟和儲存檔案。

## <a name="save-temporary-files"></a>儲存暫存檔案
如果您需要在單一套件執行期間儲存及處理暫存檔案，套件可以使用目前的工作目錄 (`.`) 或 Azure-SSIS Integration Runtime 節點的暫存資料夾 (`%TEMP%`)。

## <a name="use-on-premises-file-shares"></a>使用內部部署檔案共用
當您將使用本機檔案系統的套件隨即轉移至 Azure 中的 SSIS 時，若要繼續使用**內部部署檔案共用**，請執行下列動作：
1.  將檔案從本機檔案系統轉送至內部部署檔案共用。
2.  將內部部署檔案共用加入 Azure 虛擬網路。
3.  將您的 Azure-SSIS IR 加入相同的虛擬網路。 如需詳細資訊，請參閱[將 Azure-SSIS Integration Runtime 加入虛擬網路](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network)。
4.  透過設定使用 Windows 驗證的存取認證，將您的 Azure-SSIS IR 連線至相同虛擬網路中的內部部署檔案共用。 如需詳細資訊，請參閱[使用 Windows 驗證連線至資料和檔案共用](ssis-azure-connect-with-windows-auth.md)。
5.  將您套件中的本機檔案路徑更新為指向內部部署檔案共用的 UNC 路徑。 例如，將 `C:\abc.txt` 更新為 `\\<on-prem-server-name>\<share-name>\abc.txt`。

## <a name="use-azure-file-shares"></a>使用 Azure 檔案共用
當您將使用本機檔案系統的套件隨即轉移至 Azure 中的 SSIS 時，若要使用 **Azure 檔案服務**，請執行下列動作：
1.  將檔案從本機檔案系統轉送至 Azure 檔案服務。 如需詳細資訊，請參閱 [Azure 檔案服務](https://azure.microsoft.com/services/storage/files/)。
2.  透過設定使用 Windows 驗證的存取認證，將您的 Azure-SSIS IR 連線到 Azure 檔案服務。 如需詳細資訊，請參閱[使用 Windows 驗證連線至資料和檔案共用](ssis-azure-connect-with-windows-auth.md)。
3.  將您套件中的本機檔案路徑更新為指向 Azure 檔案服務的 UNC 路徑。 例如，將 `C:\abc.txt` 更新為 `\\<storage-account-name>.file.core.windows.net\<share-name>\abc.txt`。
