---
title: 安裝非英文語言版本的 SQL Server Management Studio (SSMS) | Microsoft Docs
description: 安裝非英文語言版本的 SQL Server Management Studio (SSMS)
ms.custom: ''
ms.date: 04/25/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6bcc4080d3ee25f22f0bd574258f3be26c331c11
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2019
ms.locfileid: "65093764"
---
# <a name="install-non-english-language-versions-of-sql-server-management-studio-ssms"></a>安裝非英文語言版本的 SQL Server Management Studio (SSMS) 

SSMS 提供數種語言版本，但是當系統地區設定與 SSMS 語言不相符時，SSMS 安裝程式會封鎖電腦上的安裝。

> [!NOTE]
> 本文適用於 SSMS 17.x。 SSMS 18.x 已移除封鎖混合語言安裝，您現在可以在法文版 Windows 上安裝 SSMS 德文版。 如果 OS 語言與 SSMS 語言不相符，請在 [工具] > [選項] > [國際設定] 底下設定想要的語言，否則 SSMS 會顯示英文的 UI。

下列指示會依您的 Windows 版本而有所不同。 下列指示適用於 Windows 10。

## <a name="install-non-english-ssms-on-a-computer-running-an-english-operating-system-os"></a>在執行英文版作業系統 (OS) 的電腦上安裝非英文版 SSMS

1. 針對您希望 SSMS 所使用的語言，安裝此語言的 Windows 語言套件：
   - [設定] > [時間與語言] > [區域與語言] > [新增語言]
2. 現在按一下剛剛安裝的語言，然後選取 [設為預設值]，以便將系統地區設定設為使用先前步驟中所安裝的語言套件。 (安裝 SSMS 之後，您可以將系統地區設定重新設定為英文)。
3. 在作業系統以您所要的語言執行之後，請安裝您想要的 SSMS 語言。 第一次安裝新的 SSMS 語言時，請使用完整的套件。 針對後續安裝，您可以使用升級套件。
4. 執行 SSMS，它應該會以您在先前步驟中所安裝的語言來顯示。
5. 將電腦的系統地區設定重新設定為英文。

## <a name="install-ssms-in-a-language-other-than-the-language-of-the-installed-os"></a>以不同於所安裝作業系統語言版本的語言來安裝 SSMS

1. 針對您希望 SSMS 所使用的語言，安裝此語言的 Windows 語言套件：
   - [設定] > [時間與語言] > [區域與語言] > [新增語言]
2. 現在按一下剛剛安裝的語言，然後選取 [設為預設值]，以便將系統地區設定設為使用先前步驟中所安裝的語言套件。
3. 在作業系統以您所要的語言執行之後，請安裝您想要的 SSMS 語言。 第一次安裝新的 SSMS 語言時，請使用完整的套件。 針對後續安裝，您可以使用升級套件。
4. 針對您想要安裝但不符合已安裝初版 SSMS 語言的每種語言，請安裝對應的 Visual Studio 2015 Shell (獨立模式) 語言套件：
   - 瀏覽至 [https://connect.microsoft.com/VisualStudio/ExtendVS](https://connect.microsoft.com/VisualStudio/ExtendVS) (您可能需要登入並完成「連線註冊」程序)。
   - 下載所需的 Visual Studio 2015 Shell (獨立模式) 語言套件並加以安裝。

   > [!IMPORTANT]
   > 請使用先前的步驟來安裝 Visual Studio 2015 Shell (獨立模式) 語言套件，不要使用 [工具] | [選項] | [國際設定] 上的 [取得其他語言] 連結。

5. 執行 SSMS，並選取您想要使用的語言：
   - [工具] | [選項] | [國際設定]
6. 關閉並重新啟動 SSMS。

## <a name="next-steps"></a>後續步驟

- [教學課程：SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/tutorials/tutorial-sql-server-management-studio)
