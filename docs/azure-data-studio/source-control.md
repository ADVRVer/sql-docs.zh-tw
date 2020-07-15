---
title: 原始檔控制
description: 了解如何在 Azure Data Studio 中設定原始檔控制
ms.prod: azure-data-studio
ms.technology: ''
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: c4f586e355ad31422c75a5abb10a4c7e42f5eda6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85758377"
---
# <a name="source-control-in-azure-data-studio"></a>Azure Data Studio 中的原始檔控制

Azure Data Studio 支援版本/原始檔控制的 Git。

## <a name="git-support-in-azure-data-studio"></a>Azure Data Studio 中的 Git 支援

Azure Data Studio 隨附 Git 原始檔控制管理員 (SCM)，但仍需要[安裝 Git (2.0.0 或更新版本)](https://git-scm.com/download) 才能使用這些功能。 

## <a name="open-an-existing-git-repository"></a>開啟現有的 Git 存放庫

1. 在 [檔案] 功能表下，選取 [開啟資料夾...]
2. 瀏覽至包含 Git 所追蹤檔案的資料夾，然後按一下 [選取資料夾]。 您可以在這裡選取本機存放庫中的子資料夾。

## <a name="initialize-a-new-git-repository"></a>初始化新的 Git 存放庫

1. 選取 [原始檔控制]，然後選取 Git 圖示。

   ![原始檔控制 Git 圖示](media/source-control/source-control.png)

1. 輸入您要初始化為 Git 存放庫的資料夾路徑，然後按 **Enter**。

   ![初始化 Git 存放庫](media/source-control/initialize-git-repository.png)

## <a name="working-with-git-repositories"></a>使用 Git 存放庫

Azure Data Studio 會從 VS Code 繼承其 Git 實作，但目前不支援其他 SCM 提供者。 如需在開啟或初始化存放庫之後使用 Git 的詳細資訊，請參閱 [Git support in VS Code](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support) (VS Code 中的 Git 支援)。

## <a name="additional-resources"></a>其他資源

- [Git 文件](https://git-scm.com/documentation)
