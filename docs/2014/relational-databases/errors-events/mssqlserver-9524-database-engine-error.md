---
title: MSSQLSERVER_9524 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9524 (Database Engine error)
ms.assetid: 12da7931-e124-4466-889c-046f1b7b7bfd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 16f5876211a987dff593721310ee31667d428b81
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "62761660"
---
# <a name="mssqlserver_9524"></a>MSSQLSERVER_9524
    
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|9254|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|XMLERR_INVALID_COLUMNSET_XML|  
|訊息文字|提供的 XML 內容不符合疏鬆資料行集所需的 XML 格式。|  
  
## <a name="explanation"></a>說明  
 嘗試修改資料行集。 資料行集的 XML 內容必須符合資料行集的格式限制。 資料行集的一般格式如下：  
  
 `<column_name_1>value1</column_name_1><column_name_2>value2</column_name_2>...`  
  
 如需有關資料行集的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜使用資料行集＞主題。  
  
## <a name="user-action"></a>使用者動作  
 更正陳述式內資料行集的 XML 格式。  
  
  
