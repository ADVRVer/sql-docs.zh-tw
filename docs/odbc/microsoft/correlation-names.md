---
title: "相互關聯名稱 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- correlation names [ODBC]
- SQL grammar [ODBC], correlation names
ms.assetid: 76c36c6f-f8e1-4ece-a77b-611dde3bdd8a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7f757a0609490c280e2d6acb3679059e7f56dace
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="correlation-names"></a>相互關聯名稱
完全支援相互關聯名稱，包括資料表清單中。 例如，下列字串中 E1 是名為 Emp 資料表相互關聯名稱：  
  
```  
SELECT * FROM Emp E1   
WHERE E1.LastName = 'Smith'  
```
