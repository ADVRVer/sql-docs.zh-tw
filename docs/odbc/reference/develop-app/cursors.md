---
description: ODBC)  (資料指標
title: ODBC)  (資料指標 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- forward-only cursors [ODBC]
- scrollable cursors [ODBC]
- cursors [ODBC], about cursors
- cursors [ODBC]
- fetches [ODBC], cursors
- result sets [ODBC], fetching
- block cursors [ODBC]
ms.assetid: 0b114352-3c63-4d33-9220-182ede90e4aa
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 10dbd2517c29bcd02d1d39abe0b2caec1bf03312
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429400"
---
# <a name="odbc-cursors"></a>ODBC 資料指標
應用程式會使用資料 *指標*提取資料。 資料指標與結果集不同：結果集是符合特定搜尋條件的資料列集，而資料指標則是將這些資料列傳回給應用程式的軟體。 當它套用至資料庫時，名稱資料 *指標* 可能源自電腦終端機上的閃爍游標。 就像該資料指標表示螢幕上目前的位置，以及輸入的單字接下來的位置，結果集上的資料指標會指出結果集內目前的位置，以及接下來會傳回的資料列。  
  
 ODBC 中的資料指標模型是以內嵌 SQL 中的資料指標模型為基礎。 這些模型之間有一個值得注意的差異，就是開啟資料指標的方式。 在內嵌 SQL 中，必須先明確宣告和開啟資料指標，才能使用它。 在 ODBC 中，當執行建立結果集的語句時，就會隱含地開啟資料指標。 當資料指標開啟時，它會放在結果集的第一個資料列之前。 在內嵌的 SQL 和 ODBC 中，資料指標必須在應用程式完成使用之後關閉。  
  
 不同的資料指標有不同的特性。 最常見的資料指標類型（稱為順向資料 *指標）* 只能向前移動結果集。 若要返回前一個資料列，應用程式必須關閉並重新開啟資料指標，然後從結果集的開頭讀取資料列，直到到達所需的資料列為止。 順向資料指標可提供快速的機制，以透過結果集進行單一傳遞。  
  
 順向資料指標較不適合以螢幕為基礎的應用程式，使用者會在其中向後和向前滾動資料。 這類應用程式可以使用順向資料指標，方法是讀取結果集一次、在本機快取資料，以及自行執行滾動。 不過，這只適用于少量的資料。 更好的解決方法是使用可滾動的資料 *指標，* 它會提供對結果集的隨機存取。 這類應用程式也可以使用所謂的*區塊資料指標*，一次提取一個以上的資料列來提高效能。 如需區塊資料指標的詳細資訊，請參閱 [使用區塊資料指標](../../../odbc/reference/develop-app/using-block-cursors.md)。  
  
 順向資料指標是 ODBC 中的預設資料指標類型，會在下列各節中討論。 如需區塊資料指標和可滾動資料指標的詳細資訊，請參閱 [區塊資料指標](../../../odbc/reference/develop-app/block-cursors.md) 和可 [滾動](../../../odbc/reference/develop-app/scrollable-cursors.md)的資料指標。  
  
> [!IMPORTANT]  
>  藉由明確呼叫 **SQLEndTran** 或以自動認可模式運作，來認可或回復交易，會導致某些資料來源關閉連接上所有語句的所有資料指標。 如需詳細資訊，請參閱 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) 函數描述中的 SQL_CURSOR_COMMIT_BEHAVIOR 和 SQL_CURSOR_ROLLBACK_BEHAVIOR 屬性。
