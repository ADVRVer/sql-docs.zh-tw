---
title: 驅動程式 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], drivers
- drivers [ODBC]
- drivers [ODBC], about drivers
ms.assetid: d6795d92-877e-44e1-b7d5-2ff2fd3989bd
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1906e61847537d3c89a5f2c3529172a9634713c0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915193"
---
# <a name="drivers"></a>驅動程式
*驅動程式*實作 ODBC API 函式的程式庫。 每一個都是特定 dbms 所特有。例如，Oracle 的驅動程式無法直接存取 Informix DBMS 中的資料。 驅動程式公開功能的基礎 Dbms 中;不需要它們實作不支援的 DBMS 功能。 例如，如果基礎 DBMS 不支援外部聯結中，則兩者都不應該驅動程式。 這僅重大例外狀況是 Dbms 沒有獨立的資料庫引擎、 Xbase，例如驅動程式必須實作至少支援最少量的 SQL 資料庫引擎。  
  
 此章節包含下列主題。  
  
-   [驅動程式工作](../../odbc/reference/driver-tasks.md)  
  
-   [驅動程式架構](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft 提供的 ODBC 驅動程式](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)
