---
title: "啟用資源管理員 | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: resource-governor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Resource Governor, enabling
ms.assetid: 4d17af53-cf11-4ce4-aab4-deda94a49836
caps.latest.revision: "12"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 193efa564c134682bfe8bc8d95387efa6ab73767
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="enable-resource-governor"></a>啟用資源管理員
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] 預設會關閉 Resource Governor。 您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 Transact-SQL 啟用資源管理員。  
  
-   **開始之前：**  [限制事項](#LimitationsRestrictions)、 [權限](#Permissions)  
  
-   **使用下列項目啟用資源管理員：**  [物件總管](#RGOnObjEx)、 [資源管理員屬性](#RGOnProp)、 [Transact-SQL](#RGOnTSQL)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
 啟用資源管理員會產生下列結果：  
  
-   系統會針對新的連接執行分類函數，以便將其工作負載指派給工作負載群組。  
  
-   系統會接受並強制執行資源管理員組態中指定的資源限制。  
  
-   啟用資源管理員之前存在的要求會受到停用資源管理員時所做的任何組態變更影響。  
  
###  <a name="LimitationsRestrictions"></a> 限制事項  
 在使用者交易中時，您無法使用 **ALTER RESOURCE GOVERNOR** 陳述式啟用資源管理員。  
  
###  <a name="Permissions"></a> 權限  
 啟用資源管理員需要 CONTROL SERVER 權限。  
  
##  <a name="RGOnObjEx"></a> 使用物件總管啟用資源管理員  
 **若要使用物件總管啟用資源管理員**  
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，開啟 [物件總管]，然後遞迴地向下展開 **[管理]** 節點至 **[資源管理員]**。  
  
2.  以滑鼠右鍵按一下 [資源管理員]，然後按一下 [啟用]。  
  
##  <a name="RGOnProp"></a> 使用資源管理員屬性啟用資源管理員  
 **若要使用資源管理員屬性頁面來啟用資源管理員**  
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，開啟 [物件總管]，然後遞迴地向下展開 **[管理]** 節點至 **[資源管理員]**。  
  
2.  以滑鼠右鍵按一下 [資源管理員]，然後按一下 [屬性]，這會開啟 [資源管理員屬性] 頁面。  
  
3.  按一下 **[啟用資源管理員]** 核取方塊，然後按一下 **[確定]**。  
  
##  <a name="RGOnTSQL"></a> 使用 Transact-SQL 啟用資源管理員  
 **若要使用 Transact-SQL 啟用資源管理員**  
  
1.  執行 **ALTER RESOURCE GOVERNOR RECONFIGURE** 陳述式。  
  
### <a name="example-transact-sql"></a>範例 (Transact-SQL)  
 下列範例會啟用資源管理員。  
  
```  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [[資源管理員]](../../relational-databases/resource-governor/resource-governor.md)   
 [停用資源管理員](../../relational-databases/resource-governor/disable-resource-governor.md)   
 [資源管理員資源集區](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [資源管理員工作負載群組](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [資源管理員分類函數](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
