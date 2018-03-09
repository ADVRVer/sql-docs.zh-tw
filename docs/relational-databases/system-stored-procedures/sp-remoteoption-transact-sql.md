---
title: "p (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_remoteoption_TSQL
- sp_remoteoption
dev_langs:
- TSQL
helpviewer_keywords:
- sp_remoteoption
ms.assetid: c9a7309b-eab7-4192-a414-e282581af4e5
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4c5670e022bee797cbabb6ec603ca66db79ef2f7
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2017
---
# <a name="spremoteoption-transact-sql"></a>sp_remoteoption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  顯示或變更執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的本機伺服器上所定義的遠端登入選項。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]sp_remoteoption 不變更任何選項，並傳回錯誤訊息。 支援這個項目的目的，只是為了與舊版相容。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_remoteoption [ [ @remoteserver = ] 'remoteserver' ]   
     [ , [ @loginame = ] 'loginame' ]   
     [ , [ @remotename = ] 'remotename' ]   
     [ , [ @optname = ] 'optname' ]   
     [ , [ @optvalue = ] 'optvalue' ]  
```  
  
## <a name="remarks"></a>備註  
 這個預存程序會傳回下列錯誤訊息：  
  
 `The trusted option in remote login mapping is no longer supported.`  
  
## <a name="see-also"></a>請參閱  
 [連結的伺服器 &#40;Database Engine&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md)  
  
  
