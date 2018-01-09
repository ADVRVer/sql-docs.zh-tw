---
title: "資料表值參數資料轉換和其他錯誤和警告 |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-table-valued-parameters
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), data conversion
- table-valued parameters (ODBC), error messages
ms.assetid: edd45234-59dc-4338-94fc-330e820cc248
caps.latest.revision: "13"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ef6e42cf00bc8b9b697590d5ebad971fd16a6b97
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2018
---
# <a name="table-valued-parameter-data-conversion-and-other-errors-and-warnings"></a>資料表值參數資料轉換及其他錯誤和警告
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  資料表值參數資料行值可以在用戶端和伺服器資料類型之間轉換，其轉換方式與其他資料行和參數值相同。 因為資料表值參數可以包含多個資料行和多個資料列，所以能夠識別發生錯誤的實際值是很重要的一件事。  
  
 當資料表值參數資料行中偵測到錯誤或警告時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 將會產生診斷記錄。 錯誤訊息將會包含資料表值參數的參數編號，加上資料行序數和資料列號碼。 應用程式可以使用診斷記錄中的診斷欄位 SQL_DIAG_SS_TABLE_COLUMN_NUMBER 和 SQL_DIAG_SS_TABLE_ROW_NUMBER，以判斷哪些值與錯誤和警告有關。 這些診斷欄位會在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 和更新版本中提供。  
  
 診斷記錄的 SQLSTATE 和訊息元件將會在所有其他層面符合現有的 ODBC 行為。 也就是說，除了參數、資料列和資料行識別資訊以外，錯誤訊息的資料表值參數值會與非資料表值參數的值相同。  
  
## <a name="see-also"></a>請參閱  
 [資料表值參數 &#40; ODBC &#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
