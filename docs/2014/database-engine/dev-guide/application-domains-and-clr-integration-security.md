---
title: 應用程式定義域和 CLR 整合安全性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- security [CLR integration]
- application domains [CLR integration]
ms.assetid: 54ee904e-e21a-4ee7-b4ad-a6f6f71bd473
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3f2ff171562929a035cb80fed556c954508c5557
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62753770"
---
# <a name="application-domains-and-clr-integration-security"></a>應用程式網域和 CLR 整合安全性
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會載入屬於同一應用程式網域中相同擁有者的組件。 組件可透過在同一應用程式網域中執行的一組組件，使用 .NET Framework Reflection 應用程式開發介面或其他方式在執行時互相發現對方，並能夠以晚期繫結方式呼叫彼此內部。 因為此類呼叫是針對屬於同一擁有者的組件而進行，所以不會檢查這些呼叫的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 權限。 應用程式網域中組件的位置配置設計主要是為達成延展性、安全性及隔離目的，並可能在以後的版本中變更。 因此，您不應依賴透過晚期繫結機制，在同一應用程式網域中尋找組件。  
  
## <a name="see-also"></a>另請參閱  
 [CLR 整合安全性](../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  
