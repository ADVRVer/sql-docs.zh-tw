---
title: SQL 全文檢索篩選精靈啟動器 (SQL Server 設定管理員) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: d0dc03db-5f76-4558-b041-1ac7b9b5bb16
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: 1ca6dc3f6cd15a799d3b110fb446be821de679c9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63137566"
---
# <a name="sql-full-text-filter-daemon-launcher-sql-server-configuration-manager"></a>SQL 全文檢索篩選背景程式啟動器 (SQL Server 組態管理員)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  從 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]開始， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 全文檢索搜尋就會使用 SQL 全文檢索篩選背景程式啟動器 (FDHOST 啟動器) 服務來啟動篩選背景程式主機處理序，以便處理全文檢索搜尋篩選和斷詞。 若要使用全文檢索搜尋，您必須執行這個服務。 FDHOST 啟動器服務是一個與特定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體有關的執行個體感知服務。 FDHOST 啟動器服務會將服務帳戶資訊傳播至啟動的每個篩選背景程式主機處理序。 如需篩選背景程式主機處理序的詳細資訊，請參閱《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜全文檢索搜尋架構＞。  
  
  
