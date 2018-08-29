---
title: 用戶端通訊協定 - 具名管道屬性 ([通訊協定] 索引標籤) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server], connecting to
- Named Pipes [SQL Server], default pipe
- client protocols [SQL Server]
ms.assetid: 30fbae62-2f2e-4d36-9c6e-3444fff68781
caps.latest.revision: 23
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: fa9108c526fc957a77938200a881535cf2afafa9
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2018
ms.locfileid: "42784385"
---
# <a name="client-protocols---named-pipes-properties-protocol-tab"></a>用戶端通訊協定 - 具名管道內容 (通訊協定索引標籤)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  在「 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員」中，使用 **[Named Pipes 內容]** 對話方塊的 **[通訊協定]** 索引標籤來檢視或修改預設管道的描述。 若要連接到其他管道，請在 **[預設管道]** 方塊內輸入管道名稱。 如需有關連接字串的詳細資訊，請參閱＜ [Creating a Valid Connection String Using Named Pipes](http://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)＞。  
  
## <a name="options"></a>選項。  
 **[預設管道]**  
 指定「具名管道網路」程式庫嘗試連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的目標執行個體時要使用的預設管道。 根據預設， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會接聽： `\\.\pipe\sql\query`  
  
 若要連接到預設管道，請輸入 `sql\query`  
  
 **已啟用**  
 可能的值為 [是] 和 [否]。  
  
## <a name="see-also"></a>另請參閱  
 [選擇網路通訊協定](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)  
  
  
