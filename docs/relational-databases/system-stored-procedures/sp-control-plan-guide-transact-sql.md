---
title: sp_control_plan_guide (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_control_plan_guide
- sp_control_plan_guide_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_control_plan_guide
ms.assetid: c96d43d5-6507-4d66-b3f5-f44c0617cb5c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5801a38e22a0c638e9daee1e448158941499b19f
ms.sourcegitcommit: 78e32562f9c1fbf2e50d3be645941d4aa457e31f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54100783"
---
# <a name="spcontrolplanguide-transact-sql"></a>sp_control_plan_guide (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  卸除、啟用或停用計畫指南。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_control_plan_guide [ @operation = ] N'<control_option>'  
  [ , [ @name = ] N'plan_guide_name' ]  
  
<control_option>::=  
{   
    DROP   
  | DROP ALL  
  | DISABLE  
  | DISABLE ALL  
  | ENABLE   
  | ENABLE ALL  
}  
```  
  
## <a name="arguments"></a>引數  
 **N'** _plan_guide_name_ **'**  
 指定要卸除、啟用或停用的計畫指南。 *plan_guide_name*會解析為目前的資料庫。 如果未指定， *plan_guide_name*預設值為 NULL。  
  
 DROP  
 卸除所指定的計畫指南*plan_guide_name*。 在卸除計畫指南之後，未來執行先前符合計畫指南的查詢時，不會受計畫指南的影響。  
  
 DROP ALL  
 卸除目前資料庫中的所有計畫指南。 **N'**_plan_guide_name_無法指定 DROP ALL 時指定。  
  
 DISABLE  
 停用所指定的計畫指南*plan_guide_name*。 在停用計畫指南之後，未來執行先前符合計畫指南的查詢時，不會受計畫指南的影響。  
  
 DISABLE ALL  
 停用目前資料庫中的所有計畫指南。 **N'**_plan_guide_name_不能指定當指定 DISABLE ALL。  
  
 ENABLE  
 可讓所指定的計畫指南*plan_guide_name*。 計畫指南在啟用之後，可以符合適合的查詢。 依預設，在建立計畫指南時，會啟用計畫指南。  
  
 ENABLE ALL  
 啟用目前資料庫中的所有計畫指南。 **N'**_plan_guide_name_**'** 不能指定當指定 ENABLE ALL。  
  
## <a name="remarks"></a>備註  
 試圖卸除或修改計畫指南所參考的函數、預存程序或 DML 觸發程序，不論是已啟用或已停用，都會造成錯誤。  
  
 停用已停用的計畫指南，或啟用已啟用的計畫指南，都沒有作用，執行時也不會發生錯誤。  
  
 不是每個版本都可使用計劃指南[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本支援的功能清單，請參閱 [SQL Server 2016 版本和支援的功能](../../sql-server/editions-and-supported-features-for-sql-server-2016.md)。 不過，您可以執行**sp_control_plan_guide** DROP 或 DROP ALL 選項，在任何版本的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
## <a name="permissions"></a>Permissions  
 若要執行**sp_control_plan_guide**上的類型 OBJECT 的計畫指南 (建立指定 **@type ='** 物件 **'** ) 需要在物件上的 ALTER 權限，計畫指南所參考。 所有其他計畫指南都需要 ALTER DATABASE 權限。  
  
## <a name="examples"></a>範例  
  
### <a name="a-enabling-disabling-and-dropping-a-plan-guide"></a>A. 啟用、停用和卸除計畫指南  
 下列範例會建立一份計畫指南，以及停用、啟用再卸除這份計畫指南。  
  
```  
--Create a procedure on which to define the plan guide.  
IF OBJECT_ID(N'Sales.GetSalesOrderByCountry', N'P') IS NOT NULL  
    DROP PROCEDURE Sales.GetSalesOrderByCountry;  
GO  
CREATE PROCEDURE Sales.GetSalesOrderByCountry   
    (@Country nvarchar(60))  
AS  
BEGIN  
    SELECT *  
    FROM Sales.SalesOrderHeader AS h   
    INNER JOIN Sales.Customer AS c ON h.CustomerID = c.CustomerID  
    INNER JOIN Sales.SalesTerritory AS t ON c.TerritoryID = t.TerritoryID  
    WHERE t.CountryRegionCode = @Country;  
END  
GO  
--Create the plan guide.  
EXEC sp_create_plan_guide N'Guide3',  
    N'SELECT *  
    FROM Sales.SalesOrderHeader AS h   
    INNER JOIN Sales.Customer AS c ON h.CustomerID = c.CustomerID  
    INNER JOIN Sales.SalesTerritory AS t ON c.TerritoryID = t.TerritoryID  
    WHERE t.CountryRegionCode = @Country',  
    N'OBJECT',  
    N'Sales.GetSalesOrderByCountry',  
    NULL,  
    N'OPTION (OPTIMIZE FOR (@Country = N''US''))';  
GO  
--Disable the plan guide.  
EXEC sp_control_plan_guide N'DISABLE', N'Guide3';  
GO  
--Enable the plan guide.  
EXEC sp_control_plan_guide N'ENABLE', N'Guide3';  
GO  
--Drop the plan guide.  
EXEC sp_control_plan_guide N'DROP', N'Guide3';  
```  
  
### <a name="b-disabling-all-plan-guides-in-the-current-database"></a>B. 停用目前資料庫中的所有計畫指南  
 下列範例會停用 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫的所有計畫指南。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_control_plan_guide N'DISABLE ALL';  
```  
  
## <a name="see-also"></a>另請參閱  
 [Database Engine 預存程序&#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sys.plan_guides &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-plan-guides-transact-sql.md)   
 [計畫指南](../../relational-databases/performance/plan-guides.md)  
  
  
