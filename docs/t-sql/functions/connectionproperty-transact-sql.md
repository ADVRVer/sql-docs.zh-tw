---
title: CONNECTIONPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CONNECTIONPROPERTY_TSQL
- CONNECTIONPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- CONNECTIONPROPERTY statement
ms.assetid: 6bd9ccae-af77-4a05-b97f-f8ab41cfde42
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 95c95ad472c5b5d4cb5420fa3b0da8f88053c0c5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="connectionproperty-transact-sql"></a>CONNECTIONPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

針對傳入要求的唯一連接，傳回連接屬性的相關資訊。
  
![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>語法  
  
```sql
CONNECTIONPROPERTY ( property )  
```  
  
## <a name="arguments"></a>引數  
*property*  
連接的屬性。 *property* 可以是下列值之一。
  
|ReplTest1|資料類型|描述|  
|---|---|---|
|net_transport|**nvarchar(40)**|傳回這項連接所用的實體傳輸通訊協定。 不可為 Null。<br /><br /> 傳回值為：**HTTP**、**具名管道**、**工作階段****共用記憶體**、**SSL**、**TCP**，和 **VIA**。<br /><br /> 注意：當連線啟用 Multiple Active Result Set (MARS) 而且啟用連線共用之後，一律會傳回**工作階段**。|  
|protocol_type|**nvarchar(40)**|傳回裝載的通訊協定類型。 它目前會區分 TDS (TSQL) 和 SOAP。 可為 Null。|  
|auth_scheme|**nvarchar(40)**|傳回連線的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證配置。 驗證配置為 Windows 驗證 (NTLM、KERBEROS、DIGEST、BASIC、NEGOTIATE) 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證。 不可為 Null。|  
|local_net_address|**varchar(48)**|傳回這項連接之目標伺服器的 IP 位址。 只適用於使用 TCP 傳輸提供者的連接。 可為 Null。|  
|local_tcp_port|**int**|如果這項連接是使用 TCP 傳輸的連接，傳回這項連接的目標伺服器 TCP 埠。 可為 Null。|  
|client_net_address|**varchar(48)**|要求連接到此伺服器之用戶端的位址。 可為 Null。|  
|physical_net_transport|**nvarchar(40)**|傳回這項連接所用的實體傳輸通訊協定。 當連接啟用 Multiple Active Result Set (MARS) 時準確。|  
|\<任何其他字串>||如果輸入無效，則會傳回 NULL。|  
  
## <a name="remarks"></a>Remarks  
**local_net_address** 和 **local_tcp_port** 會在 [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] 中傳回 NULL。
  
傳回的值與針對 [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md) 動態管理檢視中對應資料行所顯示的選項相同。 例如：
  
```sql
SELECT   
ConnectionProperty('net_transport') AS 'Net transport',   
ConnectionProperty('protocol_type') AS 'Protocol type';  
```  
  
## <a name="see-also"></a>另請參閱
[sys.dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
[sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)
  
  
