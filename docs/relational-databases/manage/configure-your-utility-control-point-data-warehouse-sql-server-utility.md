---
title: 設定公用程式控制點資料倉儲 (SQL Server 公用程式) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: maintenance-plans
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b220877e417151c92134cada14b2179a4f2a7075
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32942933"
---
# <a name="configure-your-utility-control-point-data-warehouse-sql-server-utility"></a>設定公用程式控制點資料倉儲 (SQL Server 公用程式)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 Managed 執行個體所收集的資料會儲存在公用程式管理資料倉儲 (UMDW) 中；UMDW 檔案名稱為 sysutility_mdw。  
  
 您可以設定 UMDW 資料保留週期。 如需詳細資訊，請參閱[公用程式管理 &#40;SQL Server 公用程式&#41;](http://msdn.microsoft.com/library/3e5a00c3-8905-40f0-9ddc-d924df9c2f0d)。  
  
 這一版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 無法設定下列組態設定：  
  
-   UMDW 名稱：Sysutility_mdw。  
  
-   收集組上傳頻率：每隔 15 分鐘。  
  
 UMDW 目錄是可以設定的：\<系統磁碟機>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP 名稱>\MSSQL\Data\\，其中 \<系統磁碟機> 通常是 C:\ 磁碟機。 記錄檔 Sysutility_mdw_\<GUID>_LOG 位於相同的目錄中。  
  
> [!NOTE]  
>  可以使用卸離/附加或 ALTER DATABASE 來變更 UMDW (sysutility_mdw) 檔案的位置。 我們建議使用 ALTER DATABASE。 如需詳細資訊，請參閱 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server 公用程式的功能與工作](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  
