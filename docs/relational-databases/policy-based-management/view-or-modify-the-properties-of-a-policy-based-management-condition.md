---
title: 檢視或修改原則式管理條件的屬性
description: 了解如何使用 SQL Server Management Studio (SSMS) 或 Transact-SQL (T-SQL) 來檢視或修改原則式管理條件的屬性。
ms.custom: ''
ms.date: 10/05/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view policy conditions
- Policy-Based Management, modify policy conditions
ms.assetid: 890d7384-8444-4767-bb6f-f5debb155747
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: b4948f353ea34ff40ace9b10f1ef4815c4e3fd1d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773082"
---
# <a name="view-or-modify-the-properties-of-a-policy-based-management-condition"></a>檢視或修改原則式管理條件的屬性
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中檢視或修改原則式管理條件的屬性。  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> 開始之前  
  

  
####  <a name="permissions"></a><a name="Permissions"></a> 權限  
 需要 msdb 資料庫中 PolicyAdministratorRole 角色的成員資格。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-view-or-modify-a-conditions-properties"></a>若要檢視或修改條件的屬性  
  
1.  在 **[物件總管]** 中，按一下加號，展開包含您想要檢視或修改之條件的伺服器。  
  
2.  按一下加號展開 **[管理]** 資料夾。  
  
3.  按一下加號展開 **[原則管理]** 。  
  
4.  按一下加號展開 **[條件]** 資料夾。  
  
5.  以滑鼠右鍵按一下您想要檢視或編輯的條件，然後選取 [屬性]  。 如需有關 [開啟條件 - _條件名稱_] 對話方塊中可用選項的詳細資訊，請參閱[建立新條件或開啟條件對話方塊，一般頁面](../../relational-databases/policy-based-management/create-new-condition-or-open-condition-dialog-box-general-page.md)、[開啟條件對話方塊，相依原則頁面](../../relational-databases/policy-based-management/open-condition-dialog-box-dependent-policies-page.md)、[建立新條件或開啟條件對話方塊，描述頁面](../../relational-databases/policy-based-management/create-new-condition-or-open-condition-dialog-box-description-page.md)，以及[進階編輯 &#40;條件&#41; 對話方塊](../../relational-databases/policy-based-management/advanced-edit-condition-dialog-box.md)。  
  
6.  完成後，請按一下 **[確定]** 。  

##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-view-a-conditions-properties"></a>若要檢視條件的屬性  
  
1.  在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。  
  
2.  在標準列上，按一下 **[新增查詢]** 。  
  
3.  複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。  
  
    ```  
    USE msdb;  
    GO  
    SELECT name,  
       description,  
       facet,  
       expression,  
       is_name_condition,  
       obj_name  
    FROM syspolicy_conditions;  
    GO  
  
    ```  
  
 如需詳細資訊，請參閱 [syspolicy_conditions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syspolicy-conditions-transact-sql.md)。  
  
  
