---
title: 建立使用者定義的事件
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent alerts, user-defined events
- user-defined events [SQL Server]
- multiple language support [SQL Server], alerts
- languages [SQL Server], alerts
- severity levels [SQL Server]
- global considerations [SQL Server], alerts
- events [SQL Server], user-defined
- SQL Server Agent alerts, multiple-language environments
- alerts [SQL Server], user-defined events
- alerts [SQL Server], multiple-language environments
- custom events [SQL Server Agent]
- international considerations [SQL Server], alerts
ms.assetid: 03d71a35-97fa-4bba-aa9a-23ac9c9cf879
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6bf58d9838b0ea596d448b8fdb3672d487215972
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "75245825"
---
# <a name="create-a-user-defined-event"></a>建立使用者定義的事件
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database 受控執行個體](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)目前支援多數 (但非全部) 的 SQL Server Agent 功能。 如需詳細資料，請參閱 [Azure SQL Database 受控執行個體與 SQL Server 之間的 T-SQL 差異](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)。

若要監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預先定義之事件以外的其他事件，您可以建立使用者自訂的事件。 您也可以指派嚴重性層級到每個使用者自訂事件。  
  
> [!NOTE]  
> 使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 時，請針對每個使用者自訂事件訊息選取 [寫入 Windows 應用程式事件記錄]  選項，以確保該訊息會被記錄下來。 根據預設，發生嚴重性低於 19 的使用者自訂訊息時，不會將這些訊息傳送到 [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows 應用程式記錄。 因此，嚴重性低於 19 的使用者自訂訊息不會觸發 SQL Server Agent 警示。  
  
使用者自訂事件必須有唯一的訊息編號。 使用者自訂事件的訊息編號必須大於 50,000。 您可以使用多種語言來定義事件訊息。 但是，必須有 **En-US** 錯誤訊息，才能新增其他語言的訊息。  
  
如果您管理多重語言的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 環境，請使用每個支援的語言建立使用者定義的訊息。 例如，如果您正建立將使用在英文與德文伺服器上的新事件訊息，請為兩者使用相同的訊息編號，但為每個指派不同的語言。  
  
下列工作提供如何建立使用者自訂事件與回應事件之警示的相關資訊：  
  
**若要以訊息編號為基礎建立警示**  
  
-   [Transact-SQL](../../ssms/agent/create-an-alert-using-an-error-number.md)  
  
-   [Transact-SQL](https://msdn.microsoft.com/d9b41853-e22d-4813-a79f-57efb4511f09)  
  
**若要以嚴重性層級為基礎建立警示**  
  
-   [Transact-SQL](../../ssms/agent/create-an-alert-using-severity-level.md)  
  
-   [Transact-SQL](https://msdn.microsoft.com/d9b41853-e22d-4813-a79f-57efb4511f09)  
  
**若要定義對警示的回應**  
  
-   [Transact-SQL](../../ssms/agent/define-the-response-to-an-alert-sql-server-management-studio.md)  
  
-   [Transact-SQL](https://msdn.microsoft.com/0525e0a2-ed0b-4e69-8a4c-a9e3e3622fbd)  
  
**若要建立使用者自訂的事件錯誤訊息**  
  
-   [Transact-SQL](https://msdn.microsoft.com/54746d30-f944-40e5-a707-f2d9be0fb9eb)  
  
**若要修改使用者自訂的事件錯誤訊息**  
  
-   [Transact-SQL](https://msdn.microsoft.com/1b28f280-8ef9-48e9-bd99-ec14d79abaca)  
  
**若要刪除使用者自訂的事件錯誤訊息**  
  
-   [Transact-SQL](https://msdn.microsoft.com/17287a15-cdde-43d1-bb18-9f920bc15db8)  
  
**若要停用或重新啟動警示**  
  
-   [Transact-SQL](../../ssms/agent/disable-or-reactivate-an-alert.md)  
  
-   [Transact-SQL](https://msdn.microsoft.com/4bbaeaab-8aca-4c9e-abc1-82ce73090bd3)  
  
## <a name="see-also"></a>另請參閱  
[sp_update_alert (Transact-SQL)](https://msdn.microsoft.com/4bbaeaab-8aca-4c9e-abc1-82ce73090bd3)  
  
