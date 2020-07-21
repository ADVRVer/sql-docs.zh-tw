---
title: MSSQLSERVER_360 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 360 (Database Engine error)
ms.assetid: e2b7c1b2-3679-4206-9b25-6bd55ef96a2c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 21534d6cd1499634b5d93c7140b4f8f47b3e242b
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551543"
---
# <a name="mssqlserver_360"></a>MSSQLSERVER_360
    
## <a name="details"></a>詳細資料  
  
|屬性|值|  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|360|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|DML_UPDATE_SPARSE_AND_COLSET|  
|訊息文字|INSERT、UPDATE 或 MERGE 陳述式的目標資料行清單中不可以同時包含疏鬆資料行和內含疏鬆資料行的資料行集。 請重寫陳述式，以包含疏鬆資料行或資料行集，而非同時包含兩者。|  
  
## <a name="explanation"></a>說明  
 資料行集是不具類型的 XML 表示，可將資料表的某些資料行結合到結構化輸出中。 嘗試修改此資料行集以及此資料行集中所含的資料行，造成兩個項目參考相同的資料行。  
  
## <a name="user-action"></a>使用者動作  
 請重寫陳述式，以包含對此資料行或資料行集的參考，但不要將這兩個參考同時包含在陳述式內。  
  
  
