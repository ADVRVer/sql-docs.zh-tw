---
title: 透過網際網路的複寫 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Web publishing [SQL Server replication], about Web publishing
- Web publishing [SQL Server replication]
- Internet [SQL Server replication]
- Internet [SQL Server replication], publishing
ms.assetid: 04e7f4ed-e244-4bbe-ba12-09c33abea09e
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: c5a1244ed340dcfd4794c14635d570530b88f5d9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85716725"
---
# <a name="replication-over-the-internet"></a>透過網際網路的複寫
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  透過網際網路複寫資料，可讓遠端、離線使用者在需要時使用網際網路連線存取資料。 使用下列方式，透過網際網路複寫資料：  
  
-   虛擬私人網路 (VPN)。 如需詳細資訊，請參閱[使用 VPN 透過網際網路發行資料](../../relational-databases/replication/publish-data-over-the-internet-using-vpn.md)。  
  
-   合併式複寫的 Web 同步處理選項。 如需詳細資訊，請參閱＜ [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md)＞。  
  
 所有類型的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 複寫都可以透過 VPN 複寫資料，但是您若是使用合併式複寫，則應考慮 Web 同步處理。  
  
  
