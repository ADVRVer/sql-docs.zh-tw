---
title: 設定 SQL Server 升級的重新執行
description: 在資料庫測試助理中設定重新執行
ms.custom: seo-lt-2019
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: ajaykar
ms.reviewer: mathoma
ms.openlocfilehash: b58233e40e27908f0bc8b03a95455216de2c119c
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056725"
---
# <a name="configure-replay-in-database-experimentation-assistant"></a>在資料庫測試助理中設定重新執行

資料庫測試助理（DEA）會使用 SQL Server 安裝的 Distributed Replay 工具，針對已升級的測試環境重新執行已捕獲的追蹤。 我們建議您先使用小型的追蹤檔案執行測試回合，再進行完整重新執行，以確保能正確地重新執行查詢。

## <a name="distributed-replay-requirements"></a>Distributed Replay 需求

- 需要額外的78% 硬碟空間，才能在 Distributed Replay 控制器電腦上建立 IRF 檔案。
- 200 MB 或 512 MB 是理想的追蹤變換大小，用來捕獲生產或效能追蹤。   
- Distributed Replay 控制器和用戶端電腦的最小 CPU 和 RAM 需求是具有 3.5 GB RAM 的單核心 CPU。
- 重新執行時間需要大約1.55 倍長的時間，因為有一個控制器和四個子機器用來重新執行生產追蹤。
- 如果您使用「已發行」版本的「生產」和「效能追蹤定義」檔案，而「效能追蹤定義」篩選出一個感關注的資料庫追蹤，則分析會顯示**效能追蹤**大小大約大於「**生產追蹤**」大小的15倍。

## <a name="set-up-a-virtual-network-or-domain"></a>設定虛擬網路或網域

Distributed Replay 要求您在電腦之間使用共同的帳戶。 基於這項需求，基於安全性理由，建議您在虛擬網路或網域控制的網路上執行 Distributed Replay：

- 在環境中建立控制器和用戶端電腦。
- 請確定控制器和用戶端電腦可以透過網路 ping 彼此。
- Distributed Replay 用戶端電腦必須連接到執行 SQL Server 的重新執行目的電腦。

## <a name="set-up-the-controller-service"></a>設定控制器服務

若要設定控制器服務：

1. 使用 SQL Server 安裝程式安裝 Distributed Replay 控制器。 如果您略過設定 Distributed Replay 控制器的 [SQL Server 安裝程式嚮導] 步驟，您可以透過設定檔設置控制器。 在一般安裝中，設定檔位於 C:\Program Files （x86） \Microsoft SQL Server\<版本\>\Tools\DReplayController\DReplayController.config。
1. Distributed Replay 控制器記錄檔位於 C:\Program Files （x86） \Microsoft SQL Server\<版本\>\Tools\DReplayController\Log。
1. 開啟 services.msc，並移至**SQL Server Distributed Replay 控制器**服務。
1. 以滑鼠右鍵按一下服務，然後選取 [**屬性**]。 將服務帳戶設定為在網路中控制器和用戶端電腦通用的帳戶。
1. 選取 **[確定]** 以關閉 [**屬性**] 視窗。
1. 從 services.msc 重新開機**SQL Server Distributed Replay 控制器**服務。 您也可以在命令列中執行下列命令，以重新開機服務：<br/>
   `NET STOP "SQL Server Distributed Replay Controller"`<br/>
   `NET START "SQL Server Distributed Replay Controller"`
1. 如需更多設定選項，請參閱[Configure Distributed Replay](https://docs.microsoft.com/sql/tools/distributed-replay/configure-distributed-replay)。

## <a name="configure-dcom"></a>設定 DCOM

只有在控制器電腦上才需要此設定。

1. 開啟 dcomcnfg.exe。
1. 展開 [**元件服務**] > [**電腦** > **我的電腦** > **DCOM Config**]。
1. 在 [ **DCOM Config**] 底下，以滑鼠右鍵按一下 [ **DReplayController**]，然後選取 [**屬性**]。
1. 選取 **[安全性]** 索引標籤。
1. 在 [**啟動和啟用許可權**] 底下，選取 [**自訂**]，然後選取 [**編輯**]。
1. 新增即將開始重新執行的使用者。 授與使用者本機啟動和本機啟用許可權。 如果使用者計畫要從遠端啟動或啟用，請提供使用者遠端啟動和遠端啟用許可權。
1. 選取 **[確定]** 以認可變更並返回 [**安全性**] 索引標籤。
1. 在 [**存取權限**] 底下，選取 [**自訂**]，然後選取 [**編輯**]。
1. 新增即將開始重新執行的使用者。 授與使用者本機存取權限。 如果使用者打算從遠端存取控制器服務，請授與使用者遠端存取許可權。
1. 選取 **[確定]** 以認可變更並返回 [**安全性**] 索引標籤。
1. 選取 **[確定]** 以認可變更。
1. 從 services.msc 重新開機 SQL Server Distributed Replay 控制器服務。 您也可以在命令列中執行下列命令，以重新開機服務：<br/>
   `NET STOP "SQL Server Distributed Replay Controller"`<br/>
   `NET START "SQL Server Distributed Replay Controller"`

## <a name="set-up-the-client-service"></a>設定用戶端服務

設定用戶端服務之前，請先使用網路工具（例如 ping）來確認控制器和用戶端機器可以通訊。

1. 使用 SQL Server 安裝程式安裝 Distributed Replay 用戶端。
1. 開啟 services.msc，並移至 SQL Server Distributed Replay 用戶端服務。
1. 以滑鼠右鍵按一下服務，然後選取 [**屬性**]。 將服務帳戶設定為網路中控制器和用戶端電腦通用的帳戶。
1. 選取 **[確定]** 以關閉 [**屬性**] 視窗。 如果您略過 [SQL Server 安裝程式] 步驟來設定 Distributed Replay 用戶端，您可以透過設定檔進行設定。 在一般安裝中，設定檔位於 C:\Program Files （x86） \Microsoft SQL Server\<版本\>\Tools\DReplayClient\DReplayClient.config。
1. 請確定 Dreplayclient.exe 檔案包含控制器電腦的名稱，做為註冊的控制器。
1.  從 services.msc 重新開機 SQL Server Distributed Replay 用戶端服務。 您也可以從命令列執行下列命令，以重新開機服務：<br/>
    `NET STOP "SQL Server Distributed Replay Client"`<br/>
    `NET START "SQL Server Distributed Replay Client"`
1. Distributed Replay 控制器記錄檔位於 C:\Program Files （x86） \Microsoft SQL Server\<版本\>\Tools\DReplayClient\Log。 這些記錄會指出用戶端是否可以向控制器註冊其本身。
1. 如果設定成功，記錄檔會顯示「已向控制器註冊 < 控制器名稱\>」訊息。
1. 如需更多設定選項，請參閱[Configure Distributed Replay](https://docs.microsoft.com/sql/tools/distributed-replay/configure-distributed-replay)。

## <a name="set-up-distributed-replay-administration-tools"></a>設定 Distributed Replay 管理工具

您可以使用 Distributed Replay 管理工具，快速測試 Distributed Replay 是否在環境中正常運作。 在有多個用戶端機器向控制器註冊的環境中，測試設定會特別有用。 您可能需要安裝 SQL Server Management Studio （SSMS）才能取得管理工具。

1. 移至 SSMS 安裝位置，並尋找 Distributed Replay 管理工具 dreplay 和其相依元件。
1. 開啟 [命令提示字元] 視窗，然後執行 `dreplay.exe status -f 1`。
1. 如果上述所有步驟都成功，主控台輸出會指出控制器可以看到其用戶端處於 `READY` 狀態。

## <a name="configure-the-firewall-for-remote-distributed-replay-access"></a>設定遠端 Distributed Replay 存取的防火牆

遠端存取 Distributed Replay 需要開啟在網域或虛擬網路內可見的埠。

1. 開啟 [具有**Advanced Security**的**Windows 防火牆**]。
1. 移至 [**輸入規則**]。
1. 建立 program C:\Program Files （x86） \Microsoft SQL Server\<版本\>\Tools\DReplayController\DReplayController.exe. 的新輸入防火牆規則
1. 允許 DReplayController 的所有埠的網域層級存取，以便能夠從遠端與控制器服務進行通訊。
1. 儲存規則。

## <a name="set-up-target-computers"></a>設定目的電腦

執行 A/B 測試或實驗需要兩次重新執行。 也就是說，在遷移案例中，您可能需要 SQL Server 安裝的兩個個別實例。 

您也可以在同一部電腦上安裝兩個版本的 SQL Server 實例。 有一點要注意的是，當重新執行正在進行時，就會完全隔離實例。

每次重新執行時都必須執行下列步驟：

1. 還原資料庫的備份。
1. 提供用戶端服務帳戶使用者的許可權，以存取 SQL Server 實例下的資料庫。 需要許可權，才能在 SQL Server 實例上執行查詢。
1. 開始重新執行。

## <a name="next-steps"></a>後續的步驟

- 若要瞭解如何在已升級的測試環境中重新執行已捕獲的追蹤，請參閱[replay trace](database-experimentation-assistant-replay-trace.md)。

- 如需 DEA 和示範的19分鐘簡介，請觀看下列影片：

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
