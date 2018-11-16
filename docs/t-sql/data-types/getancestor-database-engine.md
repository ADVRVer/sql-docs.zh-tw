---
title: GetAncestor (資料庫引擎) | Microsoft Docs
ms.custom: ''
ms.date: 7/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- GetAncestor_TSQL
- GetAncestor
dev_langs:
- TSQL
helpviewer_keywords:
- GetAncestor [Database Engine]
ms.assetid: b96a986f-d5e4-4034-8013-de7974594ee9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 89442e4d787c66ed76e6c2db3ff9539a14156782
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51699246"
---
# <a name="getancestor-database-engine"></a>GetAncestor (Database Engine)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

傳回 **hierarchyid**，代表 *this* 的第 *n* 個上階。
  
## <a name="syntax"></a>語法  
  
```sql
-- Transact-SQL syntax  
child.GetAncestor ( n )   
```  
  
```sql
-- CLR syntax  
SqlHierarchyId GetAncestor ( int n )  
```  
  
## <a name="arguments"></a>引數  
*n*  
**int**，代表要在階層中向上移動的層級數目。
  
## <a name="return-types"></a>傳回型
**SQL Server 傳回型別：hierarchyid**
  
**CLR 傳回型別：SqlHierarchyId**
  
## <a name="remarks"></a>Remarks  
用來測試輸出中的每個節點是否都具有目前的節點當做位於指定之層級的上階。
  
如果傳遞大於 [GetLevel()](../../t-sql/data-types/getlevel-database-engine.md) 的數字，就會傳回 NULL。
  
如果傳遞了負數，則會引發例外狀況。
  
## <a name="examples"></a>範例  
  
### <a name="a-finding-the-child-nodes-of-a-parent"></a>A. 尋找父系的子節點  
`GetAncestor(1)` 會傳回具有 `david0` 當做其直接上階 (其父系) 的員工。 下列範例會使用 `GetAncestor(1)`。
  
```sql
DECLARE @CurrentEmployee hierarchyid  
SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\david0'  
  
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetAncestor(1) = @CurrentEmployee ;  
```  
  
### <a name="b-returning-the-grandchildren-of-a-parent"></a>B. 傳回父系的孫系  
`GetAncestor(2)` 會傳回在階層中位於目前節點下面兩個層級的員工。 這些就是目前節點的孫系。 下列範例會使用 `GetAncestor(2)`。
  
```sql
DECLARE @CurrentEmployee hierarchyid  
SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\ken0'  
  
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetAncestor(2) = @CurrentEmployee ;  
```  
  
### <a name="c-returning-the-current-row"></a>C. 傳回目前的資料列  
若要使用 `GetAncestor(0)` 來傳回目前的節點，請執行下列程式碼。
  
```sql
DECLARE @CurrentEmployee hierarchyid  
SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\david0'  
  
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetAncestor(0) = @CurrentEmployee ;  
```  
  
### <a name="d-returning-a-hierarchy-level-if-a-table-is-not-present"></a>D. 如果資料表不存在便傳回階層層級  
`GetAncestor` 會傳回階層中的選取層級，即使資料表不存在也一樣。 例如，下列程式碼會指定目前的員工，並且傳回目前員工之上階的 `hierarchyid`，但是沒有資料表的參考。
  
```sql
DECLARE @CurrentEmployee hierarchyid ;  
DECLARE @TargetEmployee hierarchyid ;  
SELECT @CurrentEmployee = '/2/3/1.2/5/3/' ;  
SELECT @TargetEmployee = @CurrentEmployee.GetAncestor(2) ;  
SELECT @TargetEmployee.ToString(), @TargetEmployee ;  
```  
  
### <a name="e-calling-a-common-language-runtime-method"></a>E. 呼叫 Common Language Runtime 方法  
下列程式碼片段會呼叫 `GetAncestor()` 方法。
  
```sql
this.GetAncestor(1)  
```  
  
## <a name="see-also"></a>另請參閱
[IsDescendantOf &#40;資料庫引擎&#41;](../../t-sql/data-types/isdescendantof-database-engine.md)  
[Hierarchyid 資料類型方法參考](https://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[階層式資料 &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  
