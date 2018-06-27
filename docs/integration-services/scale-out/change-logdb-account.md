---
title: 變更 SSIS Scale Out 記錄的帳戶 | Microsoft Docs
description: 本文描述如何變更 SSIS Scale Out 記錄的使用者帳戶
ms.custom: performance
ms.date: 12/13/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: douglasl
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: craigg
ms.openlocfilehash: 6d2fa1e69ada0fe5e4ef66e01cd5322efbf38516
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2018
ms.locfileid: "35406580"
---
# <a name="change-the-account-for-scale-out-logging"></a>變更 Scale Out 記錄的帳戶
在 Scale Out 中執行 SSIS 套件時，會使用名為 **##MS_SSISLogDBWorkerAgentLogin##** 之自動建立的使用者帳戶將事件訊息記錄到 SSISDB 資料庫中。 此使用者的登入使用 SQL Server 驗證。

如果您想要變更用於 Scale Out 記錄的帳戶，請執行下列動作：

> [!NOTE]
> 如果您使用 Windows 使用者帳戶進行記錄，請使用與執行 Scale Out Worker 服務的帳戶相同的帳戶。 否則，會無法登入 SQL Server。

## <a name="1-create-a-user-for-ssisdb"></a>1.建立 SSISDB 的使用者
如需如何建立資料庫使用者的指示，請參閱[建立資料庫使用者](../../relational-databases/security/authentication-access/create-a-database-user.md)。

## <a name="2-add-the-user-to-the-database-role-ssisclusterworker"></a>2.將使用者新增至資料庫角色 ssis_cluster_worker

如需如何加入資料庫角色的指示，請參閱[加入角色](../../relational-databases/security/authentication-access/join-a-role.md)。

## <a name="3-update-the-logging-information-in-ssisdb"></a>3.更新 SSISDB 中的記錄資訊
呼叫 SQL Server 名稱和連接字串作為參數的預存程序 `[catalog].[update_logdb_info]`，如下列範例所示：

    ```sql
    SET @serverName = CONVERT(sysname, SERVERPROPERTY('servername'))
    SET @connectionString = 'Data Source=' + @serverName + ';Initial Catalog=SSISDB;Integrated Security=SSPI;'
    EXEC [internal].[update_logdb_info] @serverName, @connectionString
    GO
    ```

## <a name="4-restart-the-scale-out-worker-service"></a>4.重新啟動 Scale Out Worker 服務
重新啟動 Scale Out Worker 服務，讓變更生效。

## <a name="next-steps"></a>後續步驟
-   [Integration Services Scale Out Manager](integration-services-ssis-scale-out-manager.md)