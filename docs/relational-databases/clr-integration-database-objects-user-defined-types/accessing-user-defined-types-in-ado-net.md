---
title: "存取 ADO.NET 中的使用者定義型別 |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- UDTs [CLR integration], ADO.NET
- user-defined types [CLR integration], ADO.NET
ms.assetid: 4b0d876c-8066-490e-8e18-327c0e942b19
caps.latest.revision: "12"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 267f7513c3cc7342106b04232c137ffdd1621cf9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="accessing-user-defined-types-in-adonet"></a>存取 ADO.NET 中的使用者定義型別
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]使用任何支援的語言撰寫使用者定義型別 (Udt) [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework common language runtime (CLR) 會產生可驗證的程式碼。 這包含 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# 和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic。 UDT 允許在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中儲存物件及自訂資料結構。 資料會做為 .NET Framework 類別或結構的公用成員而公開，行為可使用類別或結構的方法來定義。 UDT 可用做資料表的資料行定義中的變數[!INCLUDE[tsql](../../includes/tsql-md.md)]批次，或做為引數的[!INCLUDE[tsql](../../includes/tsql-md.md)]函式或預存程序。  
  
 在 ADO.NET 中， **System.Data.SqlClient**提供者會以下列方式公開 Udt:  
  
-   透過**System.Data.SqlClient.SqlDataReader**當做物件。  
  
-   透過**SqlDataReader**做為未經處理位元組。  
  
-   做為參數的**System.Data.SqlClient.SqlParameter**物件。  
  
## <a name="in-this-section"></a>本節內容  
 [擷取 UDT 資料](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-retrieving-udt-data.md)  
 說明如何擷取 UDT 資料及如何指定參數。  
  
 [使用 Dataadapter 更新 UDT 資料行](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 描述如何使用中的 Udt**資料集**以及如何更新 UDT 資料使用**Dataadapter**。  
  
## <a name="see-also"></a>請參閱＜  
 [CLR 使用者定義型別](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
  
  
