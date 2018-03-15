---
title: SHUTDOWN (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SHUTDOWN_TSQL
- SHUTDOWN
dev_langs:
- TSQL
helpviewer_keywords:
- SQL Server, stopping
- shutting down SQL Server
- SHUTDOWN statement
- stopping SQL Server
- immediately stopping SQL Server
ms.assetid: c8b03ff9-688c-4fe8-86e8-bd6bd401c9a4
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: df8ef0a3cfe0ac4adb6f45bddb0bef650fea6ff3
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="shutdown-transact-sql"></a>SHUTDOWN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  立即停止 SQL Server。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
SHUTDOWN [ WITH NOWAIT ]   
```  
  
## <a name="arguments"></a>引數  
 WITH NOWAIT  
 選擇性。 在不執行每個資料庫之檢查點的情況下，關閉 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 在嘗試終止所有使用者處理序之後，結束 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 當重新啟動伺服器時，會執行未完成的交易之回復作業。  
  
## <a name="remarks"></a>Remarks  
 除非使用 WITHNOWAIT 選項，否則，SHUTDOWN 會利用下列方式來關閉 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]：  
  
1.  停用登入 (**sysadmin** 和 **serveradmin** 固定伺服器角色的成員除外)。  
  
    > [!NOTE]  
    >  若要顯示所有目前使用者的清單，請執行 **sp_who**。  
  
2.  等待目前在執行中的 Transact-SQL 陳述式或預存程序完成。 若要顯示所有作用中處理序和鎖定的清單，請分別執行 **sp_who** 和 **sp_lock**。  
  
3.  在每個資料庫中插入檢查點。  
  
 使用 SHUTDOWN 陳述式會在 **sysadmin** 固定伺服器角色的成員重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，將所需的自動復原工作量縮減到最小。  
  
 您也可以利用其他工具和方法來停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 所有這些工具和方法都會在所有資料庫中發出一個檢查點。 您可以從資料快取記憶體中清除已認可的資料，再停止伺服器：  
  
-   使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員。  
  
-   從預設執行個體的命令提示字元執行 **net stop mssqlserver**，或從具名執行個體的命令提示字元執行 **net stop mssql$***instancename*。  
  
-   使用 [控制台] 中的 [服務]。  
  
 如果 **sqlservr.exe** 是從命令提示字元啟動的，按 CTRL+C 就會關閉 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 不過，按 CTRL+C 不會插入檢查點。  
  
> [!NOTE]  
>  使用這些方法的任一種來停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，會將 `SERVICE_CONTROL_STOP` 訊息傳給 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
## <a name="permissions"></a>Permissions  
 SHUTDOWN 權限會指派給 **sysadmin** 和 **serveradmin** 固定伺服器角色的成員，且無法轉讓。  
  
## <a name="see-also"></a>另請參閱  
 [CHECKPOINT &#40;Transact-SQL&#41;](../../t-sql/language-elements/checkpoint-transact-sql.md)   
 [sp_lock &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-lock-transact-sql.md)   
 [sp_who &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)   
 [sqlservr 應用程式](../../tools/sqlservr-application.md)   
 [啟動、停止、暫停、繼續、重新啟動 Database Engine、SQL Server Agent 或 SQL Server Browser 服務](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
  
