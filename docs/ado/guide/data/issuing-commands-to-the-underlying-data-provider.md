---
title: "發出命令至基礎資料提供者 |Microsoft 文件"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shape commands [ADO]
- underlying providers [ADO]
- data shaping [ADO], commands
ms.assetid: d6001863-7733-4c32-817f-081e48587fa1
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a144e0130fec6d62ee55ea68001901815a29fef9
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="issuing-commands-to-the-underlying-data-provider"></a>發出命令至基礎資料提供者
任何不是以圖形的命令傳遞給資料提供者。 這相當於發出圖形中的命令格式為"SHAPE {提供者命令}"。 這些命令執行*不*必須產生**資料錄集**。 比方說，「 形狀 {卸除資料表 MyTable} 是完全有效圖形命令，假設此資料提供者支援卸除資料表。  
  
 這項功能可讓一般提供者命令和圖形的命令，來共用相同的連線和交易。  
  
## <a name="see-also"></a>另請參閱  
 [資料成形範例](../../../ado/guide/data/data-shaping-example.md)   
 [型式圖形文法](../../../ado/guide/data/formal-shape-grammar.md)   
 [在一般的圖形命令](../../../ado/guide/data/shape-commands-in-general.md)

