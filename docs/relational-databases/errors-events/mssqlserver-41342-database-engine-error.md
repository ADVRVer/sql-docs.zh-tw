---
title: MSSQLSERVER_41342 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 41342 (Database Engine error)
ms.assetid: 28270d98-c543-4e7d-b40c-2200e38dce1c
caps.latest.revision: "8"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3d3dc1d6bff5855b5aff6bbd36d08bcde3ccc828
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver41342"></a>MSSQLSERVER_41342
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|事件識別碼|41342|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|HK_HW_NOT_SUPPORTED|  
|訊息文字|系統上的處理器型號不支援建立 *construct*。 此錯誤通常會在舊型處理器上發生。 如需支援型號的資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》。|  
  
## <a name="explanation"></a>說明  
記憶體最佳化資料表需要支援在 128 位元值上進行不可部分完成的比較與交換作業的處理器型號，這動作需要組件指令 CMPXCHG16B。 某些舊版 AMD 處理器模型不支援 CMPXCHG16B 指令。 此外，某些虛擬化環境預設為不啟用這個指令。  
  
## <a name="user-action"></a>使用者動作  
升級處理器。 如果您的處理器支援該指令，而且您是在虛擬機器上執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，請變更組態以支援指令 CMPXCHG16B。  
  
## <a name="see-also"></a>另請參閱  
[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
