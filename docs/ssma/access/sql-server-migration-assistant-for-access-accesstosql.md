---
title: SQL Server 移轉小幫手存取 (AccessToSQL) |Microsoft 文件
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-access
ms.custom: ''
ms.date: 08/14/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 40c1eb02-26b2-44ba-969d-6c430c61c281
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: 43b725e800fba4bdb085b03cd0ea183624249b9b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="sql-server-migration-assistant-for-access-accesstosql"></a>存取 (AccessToSQL) 的 SQL Server 移轉小幫手
[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 移轉小幫手 (SSMA) 的存取是一個工具，移轉資料庫從[!INCLUDE[msCoName](../../includes/msconame_md.md)]存取版本 97 到 2010年[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005年 / [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008年 / [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012年 / [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014年 / [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016年 / [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2017 上 Windows 和 Linux （預覽） / [!INCLUDE[msCoName](../../includes/msconame_md.md)] Azure SQL DB。 SSMA for Access 轉換到存取資料庫物件[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]或 Azure SQL 資料庫物件，這些物件至載入[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]或 Azure SQL 中，然後再移轉資料的存取權[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]或 Azure SQL。  
  
這份文件會為您介紹 SSMA for Access，並提供逐步指示，將 Access 資料庫移轉至[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]或 SQL Azure 和移轉之後可能會發生問題的相關資訊。  
  
## <a name="contents"></a>目錄  
  
|章節|Description|  
|-----------|---------------|  
|[SSMA for Access 的新功能](http://msdn.microsoft.com/en-us/a24d3fc0-6911-4bfa-828a-197abf222e02)|列出 SSMA 版本所做的變更。|  
|[安裝 SQL Server 移轉小幫手進行存取](http://msdn.microsoft.com/en-us/dd50eebd-75df-4e0d-8c4d-88b511aae4c7)|列出安裝 SSMA，安裝與授權 SSMA，以及最新版本的連結的程序的必要條件。|  
|[開始使用 SQL Server 移轉小幫手存取&#40;AccessToSQL&#41;](../../ssma/access/getting-started-with-sql-server-migration-assistant-for-access-accesstosql.md)|介紹 SSMA 和它的使用者介面。|  
|[準備移轉的 Access 資料庫](http://msdn.microsoft.com/en-us/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)|描述如何準備要轉換的 Access 資料庫[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SQL Azure。|  
|[將 Access 資料庫移轉至 SQL Server](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)|提供轉換程序和程序中的每個步驟的詳細的資訊的概觀。|  
|[連結到 SQL Server 存取應用程式](http://msdn.microsoft.com/en-us/82374ad2-7737-4164-a489-13261ba393d4)|描述如何使用您現有的 Access 應用程式搭配[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]。|  
|[使用者介面參考](http://msdn.microsoft.com/en-us/af24c303-4a41-449b-9c86-d6558a97e839)|包含 SSMA 對話方塊中的文件。|  
|[使用 SSMA for Access 主控台](http://msdn.microsoft.com/en-us/ef94e843-9f88-45a2-86c4-a0af268738c4)|包含 SSMA 主控台應用程式上的文件|  
|[取得 SSMA 協助進行存取](http://go.microsoft.com/fwlink/?LinkID=708538&clcid=0x409)|提供取得其他協助的相關資訊。|  
  
