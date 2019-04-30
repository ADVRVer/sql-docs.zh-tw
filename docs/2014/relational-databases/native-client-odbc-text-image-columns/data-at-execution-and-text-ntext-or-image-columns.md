---
title: 執行資料和 Text、 ntext 或 Image 資料行 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- data-at-execution
- ODBC data-at-execution
- image columns [ODBC]
ms.assetid: 67ffb1a6-f38d-4712-ba64-96bdd41ec2b2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e7c57cf6444e5833b6deee0dcae36d71b7a6430
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63195124"
---
# <a name="data-at-execution-and-text-ntext-or-image-columns"></a>資料執行中和 Text、ntext 或 Image 資料行
  ODBC 資料執行中是一種功能，可讓應用程式針對繫結的資料行或參數使用相當大量的資料。 擷取非常大時**文字**， **ntext**，或**映像**資料行，應用程式可能無法只配置大型緩衝區、 資料行繫結到緩衝區，並擷取資料列。 更新非常大時**文字**， **ntext**，或**映像**資料行，應用程式可能無法只配置大型緩衝區、 將它繫結至在 SQL 中的參數標記陳述式，然後執行陳述式。 在這些情況下，應用程式必須使用[SQLGetData](../native-client-odbc-api/sqlgetdata.md)或是[SQLPutData](../native-client-odbc-api/sqlputdata.md)具有其資料在執行選項。  
  
## <a name="see-also"></a>另請參閱  
 [管理 Text 和 Image 資料行](managing-text-and-image-columns.md)  
  
  
