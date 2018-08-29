---
title: 驗證使用者輸入 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8aa867b0-e6f0-49eb-93d3-817ae2ed8f77
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f3ace5642893edd76684abfe82cb687630a1798
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784181"
---
# <a name="validating-user-input"></a>驗證使用者輸入

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

當您建構存取資料的應用程式時，您應該假設所有使用者輸入都是惡意的，直到經過證明為止。 如果無法證明，這可能會讓您的應用程式容易受到攻擊。 可能發生的其中一種攻擊類型稱為 SQL 插入式攻擊，其中惡意程式碼會新增至稍後傳遞到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體進行剖析與執行的字串。 若要避免這類型的攻擊，您應該搭配參數 (如有可能) 使用預存程序，並永遠驗證使用者輸入。

在用戶端程式碼中驗證使用者輸入相當重要，如此您不會浪費與伺服器的往返。 在伺服器上驗證預存程序的參數以捕捉無效的輸入以及略過用戶端驗證的輸入也同等重要。

如需 SQL 插入式攻擊以及如何避免 SQL 插入式攻擊的詳細資訊，請參閱 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書中的＜SQL 插入式攻擊＞。 如需驗證預存程序參數的詳細資訊，請參閱 [!INCLUDE[ssDE](../../includes/ssde_md.md)] 線上叢書中的＜預存程序 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])＞以及從屬主題。

## <a name="see-also"></a>另請參閱

[保護 JDBC Driver 應用程式](../../connect/jdbc/securing-jdbc-driver-applications.md)
