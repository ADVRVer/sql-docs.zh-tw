---
title: 分析平台系統的文件 | Microsoft Docs
description: Microsoft Analytics Platform System (APS) 是專為資料倉儲和巨量資料分析而設計的資料平台，可提供深層資料整合、高速查詢處理、高擴充性儲存體和端對端商業智慧方案的簡易維護。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/18/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: bc8765d0bc8fe4b5b9ab3b4bcc98ce940f99400c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "63181742"
---
# <a name="microsoft-analytics-platform-system"></a>Microsoft Analytics Platform System

Microsoft Analytics Platform System (APS) 是專為資料倉儲和巨量資料分析而設計的資料平台，可提供深層資料整合、高速查詢處理、高擴充性儲存體和端對端商業智慧方案的簡易維護。

![設備架構](media/architecture-high-level.png "設備架構")

Analytics Platform System 裝載了 SQL Server 平行資料倉儲 (PDW)，這是一款用來執行大量平行處理 (MPP) 資料倉儲的軟體。

PolyBase 技術結合了關聯式 PDW 資料與來自多種來源的 Hadoop 資料，包括 Windows Server 上的 Hortonworks、Linux 上的 Hortonworks、Linux 上的 Cloudera、HDInsight 的 Windows Azure Blob 儲存體。 這些進階的資料整合能力，加上深層整合的商業智慧工具，可讓 Analytics Platform System 傳回整合式的分析，藉此讓企業決策者制定出更縝密和更富有洞察力的商業決策。

Analytics Platform System 會以設備形式運送至您的資料中心，其配備專為執行多個工作負載預先安裝與預先設定的硬體和軟體。 當您購買 Analytics Platform System 時，可根據業務需求購買適用於 PDW 的計算節點。

Analytics Platform System 不僅快速、可擴充，並設計有高備援與高可用性功能，是值得您託付最關鍵業務資料的可靠平台。 Analytics Platform System 的設計宗旨是簡潔單純，因此您可以輕鬆學習與進行管理。 PDW 的 PolyBase 技術適用於分析 Hadoop 資料，並深度整合商業智慧工具，是建立端對端解決方案的完整平台。

## <a name="parallel-data-warehouse-software-designed-for-massively-parallel-processing"></a>平行處理資料倉儲軟體，專為大量平行處理而設計

您可將 PDW 作為端對端商業智慧方案的核心關聯式資料倉儲元件。 透過 PDW 的大量平行處理 (MPP) 設計，查詢完成的速度通常比建置於對稱式多重處理 (SMP) 資料庫管理系統上的傳統資料倉儲快 50 倍。

> [!NOTE]
> 速度快 50 倍意味著原本數小時的查詢只需要幾分鐘就能完成，而需要數分鐘的查詢則只需要幾秒鐘時間。 這個突破性的效能可讓商務分析師更快產生更詳細的結果，並輕鬆地執行特定查詢或向下切入詳細資料。 如此一來，您的企業即可更快速制定出更明智的決策。

除了實現突破性的查詢效能，PDW 還可輕鬆提供下列優勢：

- 到任何地方拓展您的資料倉儲從幾 tb 擴充至 6 pb 以上的單一設備將 「 縮放單位 」 新增至您現有的系統中的資料。

- 信任您的資料時，會有您需要因為內建的高備援性和高可用性。

- 解決載入和合併資料的最新資料挑戰。

- 使用 PDW 的高度平行化的 PolyBase 技術整合關聯式資料以供快速分析 Hadoop 資料。

- 您可以使用商業智慧工具，來建立完整的端對端解決方案。

## <a name="next-steps"></a>後續步驟

如需 PDW 優勢的詳細資訊，請參閱 MSDN 上的 [A Breakthrough Platform for Next-Generation Data Warehousing and Big Data Solutions](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/dn520808%28v=msdn.10%29) (下一代資料倉儲和巨量資料解決方案的突破性平台) 白皮書。
