---
title: 將 Windows 設定成接收遠端資料表複製-Parallel Data Warehouse |Microsoft 文件
description: 描述如何購買並設定平行處理資料倉儲之遠端資料表複製功能搭配使用的 InfiniBand 網路連接非應用裝置的 Windows 系統。 Windows 系統將會裝載接收遠端資料表複製從 SQL Server PDW 資料庫的 SQL Server 資料庫。 它是從應用裝置分別購買，並且連線至應用裝置上 InfiniBand 網路。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: ed7122f497b0bdebd893eec75606bbb6382e9a73
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
ms.locfileid: "31538768"
---
# <a name="configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband---parallel-data-warehouse"></a>設定外部 Windows 系統接收遠端資料表的副本使用 InfiniBand-Parallel Data Warehouse
描述如何購買並設定 SQL Server PDW 中之遠端資料表複製功能搭配使用的 InfiniBand 網路連接非應用裝置的 Windows 系統。 Windows 系統將會裝載接收遠端資料表複製從 SQL Server PDW 資料庫的 SQL Server 資料庫。 它是從應用裝置分別購買，並且連線至應用裝置上 InfiniBand 網路。  
  
> [!NOTE]  
> 透過 InfiniBand 網路連線不需要使用遠端資料表副本。 如果乙太網路頻寬符合您的需求，可以完成透過乙太網路連線。  
  
本主題說明設定遠端資料表複製的組態步驟的其中一個。 如需所有設定步驟，請參閱[遠端資料表的副本](remote-table-copy.md)  
  
## <a name="before-you-begin"></a>開始之前  
設定外部的 Windows 系統之前，您必須：  
  
1.  購買，或提供的 Windows 系統將會收到遠端複本。  
  
2.  機架 （如果沒有足夠的空間） 的 Windows 系統控制機架內固定或接近應用裝置，讓您可以將它連接至應用裝置 InfiniBand 網路。  
  
3.  從您的應用裝置的硬體廠商購買 InfiniBand 纜線和 InfiniBand 網路介面卡。 我們建議您購買的容錯功能的兩個連接埠的網路介面卡接收匯出的資料時。 兩個連接埠的網路介面卡建議，但並非必要條件。  
  
## <a name="HowToWindows"></a>設定接收遠端資料表的外部 Windows 系統  
若要設定外部的 Windows 系統，請使用下列步驟：  
  
1.  安裝到 Windows 系統的 InfiniBand 網路介面卡。  
  
2.  連接到主要 InfiniBand 交換器使用 InfiniBand 纜線的控制機架中的 InfiniBand 網路介面卡。  
  
3.  安裝和設定適當的 InfiniBand 網路介面卡的 Windows 驅動程式。  
  
    InfiniBand 適用於 Windows 的驅動程式會由 OpenFabrics 聯盟，InfiniBand 供應商的產業協會開發。  正確的驅動程式可能已發佈 InfiniBand 介面卡。 如果沒有，您可以從 www.openfabrics.org 下載驅動程式。  
  
4.  介面卡上設定每個連接埠的 IP 位址。 SMP 系統必須針對此用途使用靜態 IP 位址的保留位址範圍。 設定第一個連接埠，根據下列參數：  
  
    -   IP 網路位址： 172.16.132.x  
  
    -   IP 子網路遮罩： 255.255.128.0  
  
    -   主機的 IP 範圍： 1-254  
  
    與兩個連接埠的 InfiniBand 網路介面卡，設定第二個連接埠，根據下列參數：  
  
    -   IP 網路位址： 172.16.132.x  
  
    -   IP 子網路遮罩： 255.255.128.0  
  
    -   主機的 IP 範圍： 1-254  
  
5.  如果使用兩個連接埠介面卡，或多個外部的 Windows 系統連線至應用裝置，指派不同的主機數目，每個 IP 子網路內的每個系統。  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
