---
title: SqlLocalDB 公用程式 |Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SqlLocalDB utility [SQL Server]
- local database runtime utility
- LocalDB, SqlLocalDB Utility
ms.assetid: d785cdb7-1ea0-4871-bde9-1ae7881190f5
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 368c770520725aa83ccb4852881e4d62d487998d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36035122"
---
# <a name="sqllocaldb-utility"></a>SqlLocalDB 公用程式
  使用`SqlLocalDB`公用程式來建立的執行個體[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssExpCurrent](../includes/ssexpcurrent-md.md)] **LocalDB**。 `SqlLocalDB`公用程式 (SqlLocalDB.exe) 是簡單的命令列工具，讓使用者和開發人員建立及管理的執行個體[!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **LocalDB**。 如需有關如何使用資訊**LocalDB**，請參閱[SQL Server 2014 Express Locald](../database-engine/configure-windows/sql-server-2016-express-localdb.md)。  
  
## <a name="syntax"></a>語法  
  
```  
SqlLocalDB.exe   
{  
      [ create   | c ] <instance-name><instance-version> [-s ]  
    | [ delete   | d ] <instance-name>  
    | [ start    | s ] <instance-name>  
    | [ stop     | p ] <instance-name>  [ -i ] [ -k ]  
    | [ share    | h ] ["<user_SID>" | "<user_account>" ] "<private-name>""<shared-name>"  
    | [ unshare  | u ] "<shared-name>"  
    | [ info     | i ] <instance-name>  
    | [ versions | v ]  
    | [ trace    | t ] [ on | off ]  
    | [ help     | -? ]  
}  
```  
  
## <a name="arguments"></a>引數  
 [ **create** | **c** ] *\<執行個體名稱>* *\<執行個體版本>* [**-s** ]  
 建立 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **LocalDB** 的新執行個體。 `SqlLocalDB` 使用版本[!INCLUDE[ssExpress](../includes/ssexpress-md.md)]所指定的二進位檔*\<執行個體版本 >* 引數。 使用至少一個十進位數的數字格式指定版本號碼。 次要版本號碼 (Service Pack) 為選擇性。 例如，下列兩個版本號碼都可接受：11.0 或 11.0.1186。 電腦上必須安裝指定的版本。 如果未指定，版本號碼會預設新版`SqlLocalDB`公用程式。 加入 **–s** 會啟動新的 **LocalDB**執行個體。  
  
 [ **share** | **h** ]  
 使用指定的共用名稱來共用指定的 **LocalDB** 私用執行個體。 如果省略使用者 SID 或帳戶名稱，會預設為目前的使用者。  
  
 [ **unshared** | **u** ]  
 停止共用指定的 **LocalDB**共用執行個體。  
  
 [ **delete** | **d** ] *\<執行個體名稱>*  
 刪除指定的 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **LocalDB** 執行個體。  
  
 [ **start** | **s** ] "*\<執行個體名稱>*"  
 啟動指定的 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **LocalDB** 執行個體。 當成功的陳述式傳回 **LocalDB**的具名管道位址時。  
  
 [ **stop** | **p** ] *\<instance-name>* [**-i** ] [**-k** ]  
 停止指定的 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **LocalDB** 執行個體。 加入 **– i**要求以關閉此執行個體`NOWAIT`選項。 加入 **–k** 會在未經連絡的情況下終止執行個體處理序。  
  
 [ **info** | **i** ] [ *\<執行個體名稱>* ]  
 列出目前使用者擁有的所有 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **LocalDB** 執行個體。  
  
 *\<執行個體名稱>* 會傳回名稱、版本、狀態 (執行中或已停止)、指定之 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** 執行個體的上次啟動時間，以及 **LocalDB** 的本機管道名稱。  
  
 [ **trace** | **t** ] **on** | **off**  
 **在追蹤**啟用的追蹤`SqlLocalDB`API 呼叫目前的使用者。 **trace off** 停用追蹤。  
  
 **-?**  
 傳回的簡短描述每個`SqlLocalDB`選項。  
  
## <a name="remarks"></a>備註  
 <執行個體名稱> 引數必須遵循 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 識別碼的規則，或者必須以雙引號括住。  
  
 不使用任何引數執行 SqlLocalDB 會傳回說明文字。  
  
 啟動以外的作業只能在屬於目前登入之使用者的執行個體上執行。  
  
## <a name="examples"></a>範例  
  
### <a name="a-creating-an-instance-of-localdb"></a>A. 建立 LocalDB 的執行個體  
 下列範例會使用 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**二進位檔建立名為** 的 `DEPARTMENT` LocalDB [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 執行個體，並啟動此執行個體。  
  
```  
SqlLocalDB.exe create "DEPARTMENT" 12.0 -s  
```  
  
### <a name="b-working-with-a-shared-instance-of-localdb"></a>B. 使用 LocalDB 的共用執行個體  
 使用管理員權限開啟命令提示字元。  
  
```  
SqlLocalDB.exe create "DeptLocalDB"  
SqlLocalDB.exe share "DeptLocalDB" "DeptSharedLocalDB"  
SqlLocalDB.exe start "DeptLocalDB"  
SqlLocalDB.exe info "DeptLocalDB"  
REM The previous statement outputs the Instance pipe name for the next step  
sqlcmd –S np:\\.\pipe\LOCALDB#<use your pipe name>\tsql\query  
CREATE LOGIN NewLogin WITH PASSWORD = 'Passw0rd!!@52';   
GO  
CREATE USER NewLogin;  
GO  
EXIT  
```  
  
 使用 **登入執行以下程式碼以連接到** LocalDB `NewLogin` 的共用執行個體。  
  
```  
sqlcmd –S (localdb)\.\DeptSharedLocalDB -U NewLogin -P Passw0rd!!@52  
```  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server 2014 Express LocalDB](../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
  