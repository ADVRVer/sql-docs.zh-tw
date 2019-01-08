---
title: 字元資料的自動轉譯 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], autotranslating character data
- data types [ODBC], autotranslating character data
- ACPs
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- AutoTranslate feature
- ANSI code pages
- character data autotranslation [ODBC]
- autotranslating character data
- SQL Server Native Client ODBC driver, data types
- ODBC data types, autotranslating character data
ms.assetid: 86a8adda-c5ad-477f-870f-cb370c39ee13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5182ab1a72caac4181e50df2199f3e0457d3aaac
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2018
ms.locfileid: "52806590"
---
# <a name="autotranslation-of-character-data"></a>字元資料的自動轉譯
  字元資料，例如 ANSI 字元，利用 SQL_C_CHAR 宣告的變數或資料儲存在[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用**char**， **varchar**，或**文字**資料型別，可以代表只在有限的字元。 每個字元使用一個位元組儲存的字元資料僅能代表 256 個字元。 儲存在 SQL_C_CHAR 變數中的值會使用用戶端電腦的 ANSI 字碼頁 (ACP) 解譯。 使用儲存的值**char**， **varchar**，或**文字**伺服器上的資料類型會使用伺服器的 ACP 進行評估。  
  
 如果伺服器和用戶端有相同的 ACP，則會不有任何問題，在解譯儲存在 SQL_C_CHAR、 值**char**， **varchar**，或**文字**物件。 如果伺服器和用戶端的 acp 不同，則從用戶端的 SQL_C_CHAR 資料可能會解譯為不同的字元，在伺服器上，如果它用於**char**， **varchar**，或**文字**資料行、 變數或參數。 例如，包含值 0xA5 字元位元組會解譯為字元 」 在電腦上使用程式碼頁面 437，會解譯為日圓執行字碼頁 1252年的電腦上簽署 （？）。  
  
 Unicode 資料的每個字元會使用兩個位元組儲存。 Unicode 規格包含所有擴充字元，因此所有電腦都會以相同方式解譯所有 Unicode 字元。  
  
 AutoTranslate 功能[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式會嘗試將用戶端與伺服器之間移動字元資料的字碼頁不同的問題降至最低。 AutoTranslate 可以設定的連接字串中[SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md)中的組態字串[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)，或設定資料來源時[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client ODBC使用 ODBC 管理員驅動程式。  
  
 當 AutoTranslate 設定為"no"時，完成任何轉換，以在用戶端的 SQL_C_CHAR 變數之間移動的資料並**char**， **varchar**，或**文字**資料行、 變數中的參數或[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料庫。 如果資料包含擴充字元，而且用戶端電腦和伺服器電腦的字碼頁不同，則位元模式在兩部電腦上的解譯方式可能會不同。 如果兩部電腦的字碼頁相同，資料將會以相同的方式解譯。  
  
 當 AutoTranslate 設定為 「 是 」 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式會使用 Unicode 轉換在用戶端的 SQL_C_CHAR 變數之間移動的資料並**char**， **varchar**，或**文字**資料行、 變數或參數中的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料庫：  
  
-   從用戶端上的 SQL_C_CHAR 變數傳送資料**char**， **varchar**，或**文字**資料行、 變數或參數中的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料庫，ODBC驅動程式先從 SQL_C_CHAR 轉換，若要使用的用戶端，然後從 Unicode 轉回字元使用伺服器的 ACP ACP 的 Unicode。  
  
-   從傳送資料**char**， **varchar**，或**文字**資料行、 變數或參數中的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]到用戶端上的SQL_C_CHAR變數的資料庫[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式第一次從字元轉換，若要使用的伺服器，然後從 Unicode 轉回 SQL_C_CHAR 使用用戶端的 ACP ACP 的 Unicode。  
  
 由於這些所有轉換由[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式執行，在用戶端，伺服器 ACP 必須是其中一個用戶端電腦上安裝的字碼頁。  
  
 透過 Unicode 進行字元轉換可確保正確轉換同時存在兩個字碼頁上的所有字元。 但是，如果字元存在於其中一個字碼頁，但不存在於另一個字碼頁，則無法在目標字碼頁中表示字元。 例如，字碼頁 1252年擁有註冊的商標符號 （？），，而字碼頁 437 則沒有。  
  
 AutoTranslate 設定在進行下列轉換時沒有作用：  
  
-   字元 SQL_C_CHAR 用戶端變數與 Unicode 之間移動資料**nchar**， **nvarchar**，或**ntext**資料行、 變數或參數中的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料庫。  
  
-   Unicode SQL_C_WCHAR 用戶端變數與字元之間移動資料**char**， **varchar**，或**文字**資料行、 變數或參數中的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料庫。  
  
 從字元移到 Unicode 時，永遠必須轉換資料。  
  
## <a name="see-also"></a>另請參閱  
 [處理結果&#40;ODBC&#41;](processing-results-odbc.md)   
 [定序與 Unicode 支援](../collations/collation-and-unicode-support.md)  
  
  
