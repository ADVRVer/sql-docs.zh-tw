---
title: 管理工具命令列選項
titleSuffix: SQL Server Distributed Replay
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: c01b0ed3-67e4-4561-92d2-a8fbb086aca8
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 08/12/2016
ms.openlocfilehash: 3934cbdd68c89dc519d5855ee255e0ee66b832a7
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/31/2020
ms.locfileid: "75307999"
---
# <a name="administration-tool-command-line-options-distributed-replay-utility"></a>管理工具命令列選項 (Distributed Replay Utility)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 管理工具 **DReplay.exe** 是命令列工具，可與 Distributed Replay Controller 通訊。 您可以使用管理工具來起始、監視及取消控制器上的作業。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示")如需與系統管理工具語法搭配使用的語法慣例詳細資訊，請參閱 [Transact-SQL 語法慣例 &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)。  
  
## <a name="syntax"></a>語法  
  
```  
  
dreplay {preprocess|replay|status|cancel} [options] [-?]}  
  
Usage:  
  
  dreplay preprocess [-m controller] -i input_trace_file  
    -d controller_working_dir [-c config_file] [-f status_interval]  
  
  dreplay replay [-m controller] -d controller_working_dir [-o]  
    [-s target_server] -w clients [-c config_file]  
    [-f status_interval]  
  
  dreplay status [-m controller] [-f status_interval]  
  
  dreplay cancel [-m controller] [-q]   
```  
  
## <a name="remarks"></a>備註  
 您可以使用 **DReplay.exe**發出下列命令列選項：  
  
 **preprocess**  
 起始前置處理階段。 控制器會準備輸入追蹤資料 (您從實際執行環境擷取而來)，以便對目標伺服器重新執行。  
  
 **replay**  
 起始事件重新執行階段。 控制器會分派重新執行資料給指定的用戶端、啟動分散式重新執行，以及同步處理用戶端。 另外，每個選取的用戶端會記錄重新執行活動，並在本機上儲存結果追蹤檔案。  
  
 **status**  
 查詢控制器，並顯示目前狀態。  
  
 **cancel**  
 取消目前正在控制器上執行的作業。  
  
 如需包含命令引數和範例的詳細語法資訊，請參閱下列主題：  
  
-   [前置處理選項 &#40;Distributed Replay 管理工具&#41;](../../tools/distributed-replay/preprocess-option-distributed-replay-administration-tool.md)  
  
-   [重新執行選項 &#40;Distributed Replay 管理工具&#41;](../../tools/distributed-replay/replay-option-distributed-replay-administration-tool.md)  
  
-   [狀態選項 &#40;Distributed Replay 管理工具&#41;](../../tools/distributed-replay/status-option-distributed-replay-administration-tool.md)  
  
-   [取消選項 &#40;Distributed Replay 管理工具&#41;](../../tools/distributed-replay/cancel-option-distributed-replay-administration-tool.md)  
  
 RPC 以 RPC 形式重新執行，而不是以語言事件的形式重新執行。  
  
## <a name="permissions"></a>權限  
 您必須以互動使用者、本機使用者或網域使用者帳戶來執行管理工具。 若要使用本機使用者帳戶，管理工具和控制器必須在同一部電腦上執行。  
  
 如需詳細資訊，請參閱 [Distributed Replay 安全性](../../tools/distributed-replay/distributed-replay-security.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)  
  
  
