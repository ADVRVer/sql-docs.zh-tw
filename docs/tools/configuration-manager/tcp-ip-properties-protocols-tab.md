---
title: "TCP/IP 屬性 （通訊協定索引標籤） |Microsoft 文件"
ms.custom: 
ms.date: 08/24/2016
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TCP/IP [SQL Server], configuration options
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
caps.latest.revision: "38"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eacd9f77d0794038ce3d4df00f4af06d8e232e6e
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="tcpip-properties-protocols-tab"></a>TCP/IP 屬性 (通訊協定索引標籤)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]使用**TCP/IP 內容**對話方塊來設定 TCP/IP 通訊協定的選項。 按一下左窗格中的 [TCP/IP]，在詳細資料窗格中顯示個別的 IP 位址組態。  
  
 Microsoft SQL Server 必須重新啟動之後，變更才能生效。  
  
## <a name="options"></a>選項  
 **已啟用**  
 可能的值為 [是] 和 [否]。  
  
 **Keep Alive**  
 指定傳送保持運作封包以確認連接遠端是否仍然可用的間隔 (毫秒)。  
  
 **Listen All**  
 指定 SQL Server 是否將接聽電腦的網路卡所繫結的所有 IP 位址。 如果設為 [否]，請使用每個 IP 位址的屬性對話方塊，分別設定每個 IP 位址。 如果設為 [是]，[IPAll] 屬性方塊的設定將套用到所有 IP 位址。 預設值是 [是]。  
  
 **No Delay**  
 SQL Server 未實作此屬性的變更。  
  
## <a name="see-also"></a>另請參閱  
 [選擇網路通訊協定](https://msdn.microsoft.com/library/ms187892(v=sql.130).aspx)   
 [建立有效的連接字串使用 TCP IP](creating-a-valid-connection-string-using-tcp-ip.md)  
  
  
