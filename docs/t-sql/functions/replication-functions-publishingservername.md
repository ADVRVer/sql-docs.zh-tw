---
title: PUBLISHINGSERVERNAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- PUBLISHINGSERVERNAME_TSQL
- PUBLISHINGSERVERNAME
dev_langs:
- TSQL
helpviewer_keywords:
- PUBLISHINGSERVERNAME function
- Publishers [SQL Server replication], names
ms.assetid: e7c278e5-ab23-419e-ab3e-3bb20b0636df
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 56c0ccb2379869358fd3470fe5e365a6e6ce5b75
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47767846"
---
# <a name="replication-functions---publishingservername"></a>複寫函式 - PUBLISHINGSERVERNAME
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  針對參與資料庫鏡像工作階段的已發行資料庫，傳回其原始發行者名稱。 這個函數是在發行集資料庫上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 簽發者執行個體端執行。 請使用它來判斷已發行資料庫的原始簽發者。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
PUBLISHINGSERVERNAME()  
```  
  
## <a name="return-types"></a>傳回類型  
 **nvarchar**  
  
## <a name="remarks"></a>Remarks  
 PUBLISHINGSERVERNAME 用於所有類型的複寫中。  
  
 當資料庫鏡像工作階段存在於簽發者和鏡像夥伴執行個體之間的發行集資料庫上時，使用 PUBLISHINGSERVERNAME。  
  
 這個函數必須在發行集資料庫的內容中執行。 當 PUBLISHINGSERVERNAME 執行於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的鏡像伺服器執行個體上的發行集資料庫時，會傳回引發已發行資料庫所在的發行集執行個體名稱。 當這個函數執行於鏡像伺服器執行個體上的未發行資料庫，或是在容錯移轉之後從鏡像伺服器執行個體發行的資料庫，會傳回該鏡像伺服器執行個體的名稱。 當這個函數執行於原始簽發者執行個體時，會傳回簽發者的名稱。  
  
## <a name="see-also"></a>另請參閱  
 [資料庫鏡像和複寫 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)   
 [複寫函式 &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/53702dee-de58-47d5-a552-7f32000f77d4)  
  
  
