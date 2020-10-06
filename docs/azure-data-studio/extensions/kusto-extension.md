---
title: 適用於 Azure Data Studio 的 Kusto (KQL) 延伸模組
description: 本文說明如何使用 Azure Data Studio 來連線及查詢 Azure 資料總管叢集。
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: jukoesma
ms.custom: ''
ms.date: 09/22/2020
ms.openlocfilehash: 2ffe3945f8dd7e8c0ce9cf504c09622ca1a20331
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725187"
---
# <a name="kusto-kql-extension-for-azure-data-studio-preview"></a>適用於 Azure Data Studio 的 Kusto (KQL) 延伸模組 (預覽)

適用於 [Azure Data Studio](../what-is.md) 的 Kusto (KQL) 延伸模組可讓您連線及查詢 [Azure 資料總管](/azure/data-explorer/data-explorer-overview)叢集。

使用者可撰寫和執行 KQL 查詢，以及使用 [Kusto 核心](../notebooks/notebooks-kusto-kernel.md)搭配 IntelliSense 來撰寫筆記本。

藉由在 Azure Data Studio 中啟用原生 Kusto (KQL) 體驗，資料工程師、資料科學家和資料分析師即可快速觀察 Azure 資料總管中所儲存大量資料的趨勢和異常狀況。

此延伸模組目前為預覽狀態。

## <a name="prerequisites"></a>必要條件

如果您沒有 Azure 訂用帳戶，請在開始前建立[免費 Azure 帳戶](https://azure.microsoft.com/free/)。

還需要下列必要條件：

- [已安裝 Azure Data Studio](../download-azure-data-studio.md)。
- [Azure 資料總管叢集和資料庫](/azure/data-explorer/create-cluster-database-portal)。

## <a name="install-the-kusto-kql-extension"></a>安裝 Kusto (KQL) 延伸模組

若要在 Azure Data Studio 中安裝 Kusto (KQL) 延伸模組，請遵循下列步驟。

1. 在 Azure Data Studio 中開啟延伸模組管理員。 您可以選取延伸模組圖示，或在 [檢視] 功能表中選取 [延伸模組]。

2. 在搜尋列中鍵入 Kusto。

3. 選取 [Kusto (KQL)] 延伸模組並檢視其詳細資料。

4. 選取 [安裝]。

:::image type="content" source="media/kusto-extension/kusto-extension-icon.png" alt-text="Kusto 延伸模組":::

## <a name="how-to-connect-to-an-azure-data-explorer-cluster"></a>如何連線至 Azure 資料總管叢集

### <a name="find-your-azure-data-explorer-cluster"></a>尋找您的 Azure 資料總管叢集

在 [Azure 入口網站](https://ms.portal.azure.com/#home)中尋找您的 Azure 資料總管叢集，然後尋找叢集的 URI。

:::image type="content" source="media/kusto-extension/kusto-extension-adx-cluster-uri.png" alt-text="Kusto 延伸模組":::

不過，您可以立即開始使用 *help.kusto.windows.net* 叢集。

在本文中，我們會使用來自 help.kusto.windows.net 叢集的資料作為範例。

### <a name="connection-details"></a>連線詳細資料

若要設定所要連線的 Azure 資料總管叢集，請遵循下列步驟。

1. 從 [連線] 窗格中選取 [新增連線]。

2. 填入 [連線詳細資料] 資訊。
    1. 針對 [連線類型]，選取 [Kusto]。
    2. 針對 [叢集]，輸入您的 Azure 資料總管叢集。

        > [!Note]
        > 輸入叢集名稱時，請勿包含 `https://` 前置詞或尾端 `/`。

    3. 針對 [驗證類型]，使用預設值：Azure Active Directory - 與 MFA 帳戶通用。
    4. 針對 [帳戶]，使用您的帳戶資訊。
    5. 針對 [資料庫]，使用預設值。
    6. 針對 [伺服器群組]，使用預設值。
        1. 您可以使用此欄位在特定群組中組織伺服器。
    7. 將 [名稱 (選擇性)] 保留空白。
        1. 您可以使用此欄位來為您的伺服器提供別名。

    :::image type="content" source="media/kusto-extension/kusto-extension-connection-details.png" alt-text="Kusto 延伸模組":::

## <a name="how-to-query-an-azure-data-explorer-database-in-azure-data-studio"></a>如何在 Azure Data Studio 中查詢 Azure 資料總管資料庫

既然您已設定 Azure 資料總管叢集的連線，即可使用 Kusto (KQL) 來查詢您的資料庫。

若要建立新的查詢索引標籤，您可以選取 [檔案] > [新增查詢]、使用 Ctrl + N，或以滑鼠右鍵按一下資料庫，然後選取 [新增查詢]。

開啟新的查詢索引標籤後，請輸入您的 Kusto 查詢。

以下是一些 KQL 查詢的範例：

```kusto
StormEvents
| limit 1000
```

```kusto
StormEvents
| where EventType == "Waterspout"
```

如需有關撰寫 KQL 查詢的詳細資訊，請瀏覽[撰寫Azure 資料總管的查詢](/azure/data-explorer/write-queries#overview-of-the-query-language)

## <a name="view-extension-settings"></a>檢視延伸模組設定

若要變更 Kusto 延伸模組的設定，請遵循下列步驟。

1. 在 Azure Data Studio 中開啟延伸模組管理員。 您可以選取延伸模組圖示，或在 [檢視] 功能表中選取 [延伸模組]。

2. 尋找 [Kusto (KQL)] 延伸模組。

3. 選取 [管理]**** 圖示。

4. 選取 [延伸模組設定] 圖示。

延伸模組設定看起來像這樣：

:::image type="content" source="media/kusto-extension/kusto-extension-settings.png" alt-text="Kusto 延伸模組":::

## <a name="sanddance-visualization"></a>SandDance 視覺效果

Azure Data Studio 中的 [SandDance 延伸模組](../sanddance-extension.md)與 Kusto (KQL) 延伸模組將豐富的互動式視覺效果整合在一起。 從 KQL 查詢結果集，選取 [視覺化檢視] 按鈕以啟動 [SandDance](https://sanddance.js.org/)。

:::image type="content" source="media/kusto-extension/kusto-extension-sanddance-demo.gif" alt-text="Kusto 延伸模組":::

## <a name="known-issues"></a>已知問題

| 詳細資料 | 因應措施 |
|---------|------------|
| [Kusto 連線 Viewlet 在重載之後無法運作](https://github.com/microsoft/azuredatastudio/issues/12475)。 | N/A |
| [無法自動重新連線](https://github.com/microsoft/azuredatastudio/issues/11830)。 | 中斷 Azure 資料總管叢集的連線並重新連線。 |
| [重新整理 Kusto 叢集似乎無法正確地重新連線](https://github.com/microsoft/azuredatastudio/issues/11824)。 | 中斷 Azure 資料總管叢集的連線並重新連線。 |
| [連線至叢集應會顯示叢集儀表板，而不是資料庫](https://github.com/microsoft/azuredatastudio/issues/12549) | N/A |
| 針對 Azure 資料叢集資料庫中的每個資料表，只能使用 [選取前 1000 個] 的選項，而不是 [取用 10 個]。 | N/A |

您可以提出[功能要求](https://github.com/microsoft/azuredatastudio/issues/new?assignees=&labels=&template=feature_request.md&title=)，以提供意見反應給產品小組。  
您可以提出[錯誤 (bug)](https://github.com/microsoft/azuredatastudio/issues/new?assignees=&labels=&template=bug_report.md&title=)，以提供意見反應給產品小組。

## <a name="next-steps"></a>下一步

- [建立並執行 Kusto 筆記本](../notebooks/notebooks-kusto-kernel.md)
- [Azure Data Studio 中的 kqlmagic 筆記本](../notebooks/notebooks-kqlmagic.md)
- [SQL 對 Kusto 的功能提要](/azure/data-explorer/kusto/query/sqlcheatsheet)
- [什麼是 Azure 資料總管？](/azure/data-explorer/data-explorer-overview)
- [使用 SandDance 視覺效果](https://sanddance.js.org/)
