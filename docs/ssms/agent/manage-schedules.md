---
title: 管理排程
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.manageschedules.f1
ms.assetid: f56c0736-dccc-41d2-afcf-71344aff143a
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 91521d9e78bdc91b7e05cbb66b5788950d497561
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "75251106"
---
# <a name="manage-schedules"></a>管理排程
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database 受控執行個體](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)目前支援多數 (但非全部) 的 SQL Server Agent 功能。 如需詳細資料，請參閱 [Azure SQL Database 受控執行個體與 SQL Server 之間的 T-SQL 差異](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)。

讓您能夠檢視及變更 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業排程的屬性。  
  
## <a name="options"></a>選項。  
**可用的排程**  
列出此使用者可以使用的排程。 請注意，作業和排程的擁有者必須相同。 所以此清單只會包含作業之擁有者所擁有的排程。  
  
**名稱**  
顯示排程名稱。  
  
**已啟用**  
選取此選項來啟用排程。  
  
**說明**  
描述排程執行作業所用的條件。  
  
**排程中的作業**  
列出附加至排程的作業編號。 按一下某個編號以檢視該作業的屬性。  
  
**新增**  
按一下此按鈕來建立新排程。  
  
**刪除**  
按一下此按鈕來刪除選取的排程。  
  
**屬性**  
按一下此按鈕來變更所選取排程的屬性。  
  
## <a name="see-also"></a>另請參閱  
[建立及附加排程至作業](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
  
