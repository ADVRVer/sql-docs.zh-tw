---
title: Ado.net 的 SQL Server 同處理序特定擴充 |Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [CLR integration]
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], in-process extensions
- in-process data access providers [CLR integration]
- extensions [CLR integration]
ms.assetid: 781b812e-eb14-472a-85fa-aa4cdb929bee
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b72ecf75f7c696e21fc14e73b42d1d192320679e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36033288"
---
# <a name="sql-server-in-process-specific-extensions-to-adonet"></a>ADO.NET 的 SQL Server 同處理序特定擴充
  ADO.NET 有四個專門用於同處理序的主要功能擴充。 下列主題將詳細說明這些擴充功能。  
  
## <a name="in-this-section"></a>本節內容  
 [SqlContext 物件](sqlcontext-object.md)  
 此類別會摘要執行 Managed 程式碼同處理序之 SQL Server 常式呼叫者的內容，藉以存取其他延伸模組。  
  
 [SqlPipe 物件](sqlpipe-object.md)  
 此類別包含可將表格式結果和訊息傳送到用戶端的常式。  
  
 [SqlTriggerContext 物件](sqltriggercontext-object.md)  
 此類別提供執行觸發程序之內容的相關資訊。  
  
 [SqlDataRecord 物件](sqldatarecord-object.md)  
 SqlDataRecord 類別會要求單一資料列的資料及其相關的中繼資料，並允許預存程序將自訂結果集傳回用戶端。  
  
  