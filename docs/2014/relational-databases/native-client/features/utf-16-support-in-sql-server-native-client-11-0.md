---
title: SQL Server Native Client 11.0 中的 utf-16 支援 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59079427bc0a8e1c62bf9b3590073e35ac2ed6b1
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423517"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>SQL Server Native Client 11.0 中的 UTF-16 支援
  從開始[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]，如果繫結資料行結果或輸出參數時，會提供固定長度的緩衝區，而且如果`wchar`終止字元成為 surrogate 字組中，高 surrogate 字碼指標之前，而且如果寫入緩衝區的字元下一步`wchar`字元是低 surrogate 字碼指標，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]原生用戶端不會新增至緩衝區的高 surrogate 字碼指標。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Native Client 功能](sql-server-native-client-features.md)  
  
  
