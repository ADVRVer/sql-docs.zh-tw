---
title: 查詢擴充預存程式
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], querying
ms.assetid: e02348e6-dba6-438a-98b6-684244bb034d
author: rothja
ms.author: jroth
ms.custom: seo-dt-2019
ms.openlocfilehash: 875d4f252058d442c91915eb69784507c39b2e94
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "74095949"
---
# <a name="querying-extended-stored-procedures-installed-in-sql-server"></a>查詢 SQL Server 中安裝的擴充預存程序
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  
  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 請改用 CLR 整合。  
  
 已驗證的使用者可以藉由執行 sp_helpextendedproc 系統程式，顯示目前定義的擴充預存程式，以及每個所屬的 DLL 名稱。 **** [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 例如，下列範例會傳回**xp_hello**所屬的 DLL：  
  
```  
sp_helpextendedproc 'xp_hello'  
```  
  
 如果在未指定擴充預存程式的情況下執行**sp_helpextendedproc** ，則會顯示所有擴充預存程式及其 dll。  
  
> [!IMPORTANT]  
>  只會針對已登入之使用者所擁有或擁有權限的那些擴充預存程序傳回資訊。 只有**系統管理員（sysadmin** ）固定伺服器角色和**db_owner**、 **db_securityadmin**和**db_ddladmin**固定資料庫角色的成員，才能夠查看所有擴充預存程式的資訊。  
  
## <a name="see-also"></a>另請參閱  
 [sp_helpextendedproc &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [sp_addextendedproc &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
  
  
