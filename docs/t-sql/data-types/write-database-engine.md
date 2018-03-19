---
title: "Write (資料庫引擎) | Microsoft Docs"
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Write_TSQL
- Write
dev_langs:
- TSQL
helpviewer_keywords:
- Write [Database Engine]
ms.assetid: 7c554334-d2d9-4eae-a4ae-097aa4020e1a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 11980f26c4af4a2dabb57e5cce242d7e89028d16
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="write-database-engine"></a>Write (Database Engine)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Write 會寫出 **SqlHierarchyId** 的二進位表示法到傳入的 **BinaryWriter**。 Write 無法使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 呼叫。 請改用 CAST 或 CONVERT。
  
## <a name="syntax"></a>語法  
  
```sql
void Write( BinaryWriter w )   
```  
  
## <a name="arguments"></a>引數  
*w*  
此 **hierarchyid** 節點的二進位表示法寫出的 **BinaryWriter** 物件。
  
## <a name="return-types"></a>傳回類型  
**CLR 傳回型別：void**
  
## <a name="remarks"></a>Remarks  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會在需要的時候於內部使用 Write，例如從 **hierarchyid** 資料行載入資料時。 在 **hierarchyid** 和 **varbinary** 之間進行轉換時，也會在內部呼叫 Write。
  
## <a name="examples"></a>範例  
  
```sql
MemoryStream stream = new MemoryStream();  
BinaryWriter bw = new BinaryWriter(stream);  
hid.Write(bw);  
byte[] encoding = stream.ToArray();  
  
```  
  
## <a name="see-also"></a>另請參閱
[Read &#40;資料庫引擎&#41;](../../t-sql/data-types/read-database-engine.md)  
[ToString &#40;資料庫引擎&#41;](../../t-sql/data-types/tostring-database-engine.md)  
[CAST 和 CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Hierarchyid 資料類型方法參考](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)
  
  
