---
title: Database Mail XPs 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 11/27/2018
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Database Mail XPs option
- Database Mail [SQL Server], enabling
ms.assetid: e22c4e63-1792-473b-af11-14a7931ca9ed
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: f350a5027957acba7e9e8689b8650bb545368030
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "66767920"
---
# <a name="database-mail-xps-server-configuration-option"></a>Database Mail XP 伺服器組態選項

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

使用 [DatabaseMail XP]  選項，可在此伺服器上啟用 Database Mail。 可能的值為：  
  
- `0`:無法使用 Database Mail (預設值)。  
  
- `1`:可以使用 Database Mail。  
  
 設定立即生效，伺服器不必停止再重新啟動。  
  
 啟用 Database Mail 後，您必須設定 Database Mail 主機資料庫來使用 Database Mail。  
  
 使用 [Database Mail 設定精靈]  設定 Database Mail，可啟用 `msdb` 資料庫中的 Database Mail 擴充預存程序。 如果您使用 [Database Mail 設定精靈]  ，就不需使用以下的 `sp_configure` 範例。  
  
 將 [Database Mail XP]  選項設為 `0`，會使 Database Mail 無法啟動。 如果 Database Mail 在該選項設為 `0` 時仍在執行中，則會繼續執行並傳送郵件，直到 `DatabaseMailExeMinimumLifeTime` 選項所設定的時間才會閒置。  
  
## <a name="examples"></a>範例
 下列範例會啟用 Database Mail 擴充預存程序。  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Database Mail XPs', 1;  
GO  
RECONFIGURE  
GO  
```  

下列範例會啟用 Database Mail 擴充預存程序 (如果尚未啟用)。

```sql
IF EXISTS (
    SELECT 1 FROM sys.configurations 
    WHERE NAME = 'Database Mail XPs' AND VALUE = 0)
BEGIN
  PRINT 'Enabling Database Mail XPs'
  EXEC sp_configure 'show advanced options', 1;  
  RECONFIGURE
  EXEC sp_configure 'Database Mail XPs', 1;  
  RECONFIGURE  
END
```

## <a name="see-also"></a>另請參閱
[Database Mail](../../relational-databases/database-mail/database-mail.md)  
