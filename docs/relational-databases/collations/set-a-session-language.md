---
title: 設定工作階段語言 | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [SQL Server], international considerations
- globalization [SQL Server], sessions
- time [SQL Server]
- sessions [SQL Server], languages
- international considerations [SQL Server], sessions
- dates [SQL Server], session languages
- global considerations [SQL Server], sessions
- client-side session language
- time [SQL Server], session languages
- messages [SQL Server], international considerations
- server-side session language
ms.assetid: de7f2c90-8f4f-4cfc-94cc-4933a7fd2bde
caps.latest.revision: 39
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3c8c0b723c1b61eee76d825e5dbdf7f0f4bf5d4f
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "43078026"
---
# <a name="set-a-session-language"></a>設定工作階段語言
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  工作階段語言可根據語言和文化喜好設定，用來設定在伺服器顯示下列元素的方式：  
  
-   錯誤訊息與其他系統訊息所使用的語言。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援所有系統錯誤字串及訊息的多個複本，而支援語言即為所提供之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 語言版本的所有語言。 您可以利用 [sys.messages](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md) 目錄檢視來檢視這些訊息。 在您安裝當地語系化版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，會將這些系統訊息翻譯成您所安裝的語言版本。 依預設，您也會取得美國英文版的這些訊息。 此外，您也可以使用 [sp_addmessage](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)，新增以特定語言顯示的使用者自訂訊息。  
  
-   日期和時間資料的格式。  
  
-   星期日期和月份的名稱，其中包括縮寫。  
  
-   星期的第一天。  
  
-   貨幣資料。  
  
 工作階段設定可以使用 33 種語言。 如需語言的清單，請參閱＜ [sys.syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)＞。  
  
## <a name="setting-the-session-language-from-the-server"></a>從伺服器設定工作階段語言  
 若要從伺服器端設定工作階段語言，請使用 [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md)。  
  
## <a name="setting-the-session-language-from-the-client"></a>從用戶端設定工作階段語言  
 您可以利用 OLE DB、ODBC 或 ADO.NET，在用戶端設定工作階段語言。 如果是 OLE DB，請使用 SSPROP_INIT_CURRENTLANGUAGE 屬性。 如需詳細資訊，請參閱 [初始化和授權屬性](../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)。  
  
 如果是 ODBC，請使用 Language 關鍵字。 如需詳細資訊，請參閱 [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md)。  
  
 如果是 ADO.NET，請使用 **ConnectionString** 物件的 **Current Language** 參數。 如需詳細資訊，請參閱 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Data Access Components (MDAC) 軟體開發套件 (SDK) 文件集。  
  
  
