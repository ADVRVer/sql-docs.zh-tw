---
title: 變更類型 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], types of changes
- backward compatibility [ODBC], types of changes
ms.assetid: 6a7db81a-20aa-4915-aed8-429711a36f49
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ac4d791bd848369ddeb87209676c65d639506af6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="types-of-changes"></a>類型的變更
在 ODBC 3 中進行三種變更類型。*x* （和 ODBC 的任何版本）。 每一種方式會影響回溯相容性，而且以不同方式處理。 下表詳述這些變更。  
  
|變更類型|Description|  
|--------------------|-----------------|  
|新增功能|這些是 ODBC 3 新功能。*x*，例如-單行繫結或描述元。 只有當應用程式和驅動程式，以及驅動程式管理員 中，第 3 版的這些實 *.x*，因此不會將這些具有回溯相容性。|  
|重複的功能|這些是存在於 ODBC 2 中的功能 *.x*而 ODBC 3.<placeholder>x<。*x*但會在每個不同的方式實作。 函式**SQLAllocHandle**和**SQLAllocStmt**是範例。 回溯相容性問題，這些和其他重複的功能大多由驅動程式管理員中的對應。|  
|行為變更|這些是 ODBC 2 中以不同方式處理的功能 *.x*而 ODBC 3.<placeholder>x<。*x*。 Datetime **#define**是範例。 這些功能是由 ODBC 3 處理。*x*驅動程式為基礎的環境屬性設定。 (請參閱[的行為變更](../../../odbc/reference/develop-app/behavioral-changes.md)如需詳細資訊。)|
