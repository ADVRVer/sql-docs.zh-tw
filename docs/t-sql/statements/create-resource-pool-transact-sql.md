---
title: CREATE RESOURCE POOL (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CREATE RESOURCE POOL
- RESOURCE POOL
- CREATE_RESOURCE_POOL_TSQL
- RESOURCE_POOL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE RESOURCE POOL
ms.assetid: 82712505-c6f9-4a65-a469-f029b5a2d6cd
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 22f087361a987dd423623650ea95d8d749265439
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2018
ms.locfileid: "52538936"
---
# <a name="create-resource-pool-transact-sql"></a>CREATE RESOURCE POOL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中建立資源管理員資源集區。 資源集區代表資料庫引擎執行個體的實體資源 (記憶體、CPU 和 IO) 子集。 資源管理員可讓資料庫管理員在資源集區間散發伺服器資源，最多可達 64 個集區。 並非每個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本中都可使用資源管理員。 如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本支援的功能清單，請參閱 [SQL Server 2016 版本支援的功能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)。  
  
## <a name="syntax"></a>語法  
  
```  
CREATE RESOURCE POOL pool_name  
[ WITH  
    (  
        [ MIN_CPU_PERCENT = value ]  
        [ [ , ] MAX_CPU_PERCENT = value ]   
        [ [ , ] CAP_CPU_PERCENT = value ]   
        [ [ , ] AFFINITY {SCHEDULER =  
                  AUTO 
                | ( <scheduler_range_spec> )   
                | NUMANODE = ( <NUMA_node_range_spec> )
                } ]   
        [ [ , ] MIN_MEMORY_PERCENT = value ]  
        [ [ , ] MAX_MEMORY_PERCENT = value ]  
        [ [ , ] MIN_IOPS_PER_VOLUME = value ]  
        [ [ , ] MAX_IOPS_PER_VOLUME = value ]  
    )   
]  
[;]  
  
<scheduler_range_spec> ::=  
{ SCHED_ID | SCHED_ID TO SCHED_ID }[,...n]  
  
<NUMA_node_range_spec> ::=  
{ NUMA_node_ID | NUMA_node_ID TO NUMA_node_ID }[,...n]  
```  
  
## <a name="arguments"></a>引數  
 *pool_name*  
 這是資源集區的使用者定義名稱。 *pool_name* 是英數字元，最多可有 128 個字元，而且在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體內必須是唯一的，並須符合[識別碼](../../relational-databases/databases/database-identifiers.md)的規則。  
  
 MIN_CPU_PERCENT =*value*  
 當 CPU 出現競爭時，為在資源集區中的所有要求，指定保證平均 CPU 頻寬。 *value* 是預設值為 0 的整數。 允許的 *value* 範圍從 0 至 100。  
  
 MAX_CPU_PERCENT =*value*  
 當出現 CPU 競爭時，指定所有要求在資源集區中將會接收的最大平均 CPU 頻寬。 *value* 是整數，預設值為 100。 允許的 *value* 範圍從 1 至 100。  
  
 CAP_CPU_PERCENT =*value*  
 **適用於**： [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
 指定資源集區中所有要求都將接收的 CPU 頻寬硬體上限。 將最大 CPU 頻寬層級限制為指定的值。 *value* 是整數，預設值為 100。 允許的 *value* 範圍從 1 至 100。  
  
 AFFINITY {SCHEDULER = AUTO | ( \<scheduler_range_spec> ) | NUMANODE = (\<NUMA_node_range_spec>)} **適用於**：[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
 將資源集區附加至特定排程器。 預設值是 AUTO。  
  
 AFFINITY SCHEDULER = **(** \<scheduler_range_spec>**)** 會將資源集區對應至給定識別碼所識別的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 排程。 這些識別碼會對應至 [sys.dm_os_schedulers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md) 中 scheduler_id 資料行的值。 
  
 當您使用 AFFINITY NUMANODE = **(** \<NUMA_node_range_spec> **)** 時，資源集區會與對應至對應給定 NUMA 節點或節點範圍之實體 CPU 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 排程器相似化。 您可以使用下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢探索實體 NUMA 組態與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 排程器識別碼之間的對應。 
  
```  
SELECT osn.memory_node_id AS [numa_node_id], sc.cpu_id, sc.scheduler_id  
FROM sys.dm_os_nodes AS osn  
INNER JOIN sys.dm_os_schedulers AS sc   
    ON osn.node_id = sc.parent_node_id   
    AND sc.scheduler_id < 1048576;  
```  
  
 MIN_MEMORY_PERCENT =*value*  
 指定為此資源集區所保留的最小記憶體數量 (不與其他資源集區共享)。 *value* 是預設值為 0 的整數。允許的 *value* 範圍從 0 到 100。  
  
 MAX_MEMORY_PERCENT =*value*  
 指定在此資源集區中，可供要求所用的伺服器記憶體總量。 *value* 是整數，預設值為 100。 允許的 *value* 範圍從 1 至 100。  
  
 MIN_IOPS_PER_VOLUME =*value*  
 **適用於**： [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
 指定要為資源集區保留之每個磁碟區的每秒 I/O 作業數 (IOPS) 最小值。 允許的 *value* 範圍從 0 至 2^31-1 (2,147,483,647)。 指定 0 表示集區沒有最小臨界值。 預設值是 0。  
  
 MAX_IOPS_PER_VOLUME =*value*  
 **適用於**： [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
 指定要允許資源集區使用之每個磁碟區的每秒 I/O 作業數 (IOPS) 最大值。 允許的 *value* 範圍從 0 至 2^31-1 (2,147,483,647)。 指定 0 可為集區設定無限的臨界值。 預設值是 0。  
  
 如果集區的 MAX_IOPS_PER_VOLUME 設定為 0，則完全不會管制集區，且即使其他集區設定 MIN_IOPS_PER_VOLUME，該集區也會保留系統中的所有 IOPS。 在此情況下，如果您希望此集區受 IO 管制，建議您將此集區的 MAX_IOPS_PER_VOLUME 值設定為較高的數字 (例如最大值 2^31-1)。  
  
## <a name="remarks"></a>Remarks  
 MIN_IOPS_PER_VOLUME 和 MAX_IOPS_PER_VOLUME 指定每秒讀取數或寫入數的最小值和最大值。 這可以是任何規模的讀取或寫入，並不表示最小或最大輸送量。  
  
 MAX_CPU_PERCENT 和 MAX_MEMORY_PERCENT 的值必須分別大於或等於 MIN_CPU_PERCENT 和 MIN_MEMORY_PERCENT 的值。  
  
 CAP_CPU_PERCENT 與 MAX_CPU_PERCENT 不同之處在於，與集區相關聯的工作負載可以使用高於 MAX_CPU_PERCENT 值 (如果有的話) 但不高於 CAP_CPU_PERCENT 值的 CPU 容量。  
  
 每個相似化元件 (排程器或 NUMA 節點) 的 CPU 百分比總計不應該超過 100%。  
  
## <a name="permissions"></a>[權限]  
 需要 CONTROL SERVER 權限。  
  
## <a name="examples"></a>範例  
 下列範例將示範如何建立名為 `bigPool` 的資源集區。 這個集區會使用資源管理員的預設設定。  
  
```  
CREATE RESOURCE POOL bigPool;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
 下列範例將 `CAP_CPU_PERCENT` 的硬體上限設為 30%，並將 `AFFINITY SCHEDULER` 的範圍設為 0 到 63 和 128 到 191。 
  
**適用於**： [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
```  
CREATE RESOURCE POOL PoolAdmin  
WITH (  
     MIN_CPU_PERCENT = 10,  
     MAX_CPU_PERCENT = 20,  
     CAP_CPU_PERCENT = 30,  
     AFFINITY SCHEDULER = (0 TO 63, 128 TO 191),  
     MIN_MEMORY_PERCENT = 5,  
     MAX_MEMORY_PERCENT = 15  
      );  
  
```  
  
 下列範例將 `MIN_IOPS_PER_VOLUME` 設為 \<some value>，並將 `MAX_IOPS_PER_VOLUME` 設為 \<some value>。 這些值會控管可用於資源集區的實體 I/O 讀取和寫入作業。  
  
**適用於**： [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
```  
CREATE RESOURCE POOL PoolAdmin  
WITH (  
    MIN_IOPS_PER_VOLUME = 20,  
    MAX_IOPS_PER_VOLUME = 100  
      );  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-workload-group-transact-sql.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)   
 [資源管理員資源集區](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [建立資源集區](../../relational-databases/resource-governor/create-a-resource-pool.md)  
  
  

