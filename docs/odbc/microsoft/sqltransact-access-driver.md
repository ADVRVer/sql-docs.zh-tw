---
title: SQLTransact （Access 驅動程式） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLTransact
- SQLTransact function [ODBC], Access Driver
ms.assetid: 892b79c7-9e20-4d1f-bc60-d4b25694ca25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b0cb17ed043a6b533b007769b9cbb28652d06e6f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47719609"
---
# <a name="sqltransact-access-driver"></a>SQLTransact (Access 驅動程式)
> [!NOTE]  
>  本主題提供存取驅動程式特有的資訊。 如需此函式的一般資訊，請參閱底下的適當主題[ODBC API 參考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
 使用 Microsoft Access 驅動程式時，支援 SQL_COMMIT 和 SQL_ROLLBACK 為了*fType*呼叫中的引數**SQLTransact**。  
  
 如果您在認可程序期間發生失敗，可以使用 [修復資料庫] 選項，在 Microsoft Access 驅動程式安裝程式，或透過 REPAIR_DB 關鍵字，在使用修復受影響的資料庫**SQLConfigDataSource**函式。
