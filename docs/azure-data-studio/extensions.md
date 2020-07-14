---
title: 新增延伸模組
description: 將延伸模組市集中的延伸模組新增至 Azure Data Studio
ms.prod: azure-data-studio
ms.technology: ''
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, maghan, sstein
ms.custom: seodec18
ms.date: 10/03/2019
ms.openlocfilehash: 7e74d0dd7b904cba5b332eb20163c96237ac6d6e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774624"
---
# <a name="extend-the-functionality-of-azure-data-studio"></a>擴充 Azure Data Studio 的功能

Azure Data Studio 中的延伸模組提供一種簡單方式，讓您將更多功能新增至基底 Azure Data Studio 安裝。

延伸模組是由 Azure Data Studio 小組 (Microsoft) 及協力廠商社群 (您！) 提供。 如需建立延伸模組的詳細資訊，請參閱[延伸模組撰寫](extension-authoring.md)。

## <a name="add-azure-data-studio-extensions"></a>新增 Azure Data Studio 延伸模組

1. 透過選取 [延伸模組] 圖示或透過選取 [檢視] 功能表中的 [延伸模組]，以存取可用的延伸模組。

    ![延伸模組管理員圖示](media/extensions/extension-manager-icon.png)

    您也可以按下 `Ctrl+Shift+X` (Windows/Linux) 或 `Command+Shift+X` (Mac) 以快速存取延伸模組管理員。

2. 選取可用的延伸模組，檢視詳細資料。
    ![延伸模組詳細資料](media/extensions/extension-details.png)

3. 選取您想要的延伸模組並加以**安裝**。

4. 安裝之後，請**重新載入**以在 Azure Data Studio 中啟用延伸模組 (只有在第一次安裝延伸模組時才需要)。

若無法存取 Azure Data Studio 上的延伸模組管理員，您可以在我們的 [GitHub Wiki](https://github.com/microsoft/azuredatastudio/wiki/List-of-Extensions) \(英文\) 下載延伸模組。


## <a name="access-installed-azure-data-studio-extensions"></a>存取已安裝的 Azure Data Studio 延伸模組

每個延伸模組都會以不同方式強化您在 Azure Data Studio 中的體驗。 因此，延伸模組的進入點可能會有所不同。 請參閱已安裝延伸模組的個別文件，以取得安裝後如何存取其功能的資訊。
