---
title: SQLGetTypeInfo （Access 驅動程式） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLGetTypeInfo
- SQLGetTypeInfo function [ODBC], Access Driver
ms.assetid: a28b16eb-ca36-4297-9297-ecd7c107a84e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 788f0b8c69636ad9bf93de73632abc911a0fb0e3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67898758"
---
# <a name="sqlgettypeinfo-access-driver"></a>SQLGetTypeInfo (Access 驅動程式)
> [!NOTE]  
>  本主題提供存取驅動程式特有的資訊。 如需此函式的一般資訊，請參閱底下的適當主題[ODBC API 參考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
 產生的資料表中所傳回的型別 (TYPE_NAME) 名稱**SQLGetTypeInfo**會是最常用的資料來源的名稱。  
  
 SQL_ALL_EXCEPT_LIKE 就會傳回可搜尋的資料行中位元組、 計數器、 Double、 單一、 長時間，以及 Short 資料類型。 （LIKE 功能可藉由將值轉換成使用 ODBC 標準的轉換函式，然後執行比較的字元。）
