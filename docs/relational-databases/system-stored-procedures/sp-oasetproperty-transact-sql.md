---
title: sp_OASetProperty (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_OASetProperty
- sp_OASetProperty_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OASetProperty
ms.assetid: 0fe7d554-6b67-4d55-9d3e-4096802c47f8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d2d3cc319a99c9e1b157e5b6bc06cabea2dd19a7
ms.sourcegitcommit: 603d5ef9b45c2f111d36d11864dc032917e4a321
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65450079"
---
# <a name="spoasetproperty-transact-sql"></a>sp_OASetProperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  將 OLE 物件的屬性設為新值。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_OASetProperty objecttoken , propertyname , newvalue [ , index... ]  
```  
  
## <a name="arguments"></a>引數  
 *objecttoken*  
 先前所建立之 OLE 物件的物件 token **sp_OACreate**。  
  
 *propertyname*  
 這是要設為新值的 OLE 物件屬性名稱。  
  
 *newvalue*  
 這是屬性的新值，必須是適當資料類型的值。  
  
 *index*  
 這是一個索引參數。 如果指定， *index*必須是適當的資料類型的值。  
  
 部份屬性有參數。 這些屬性稱為索引屬性，參數稱為索引參數。 一個屬性可以有多個索引參數。  
  
> [!NOTE]  
>  這個預存程序的參數是依照位置來指定，而不是名稱。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或非零數字 (失敗)，這個數字是 OLE Automation 物件所傳回之 HRESULT 的整數值。  
  
 如需有關 HRESULT 傳回碼的詳細資訊，請參閱 < [OLE Automation 傳回碼與錯誤資訊](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md)。  
  
## <a name="permissions"></a>Permissions  
 需要的成員資格**sysadmin**固定伺服器角色，或直接執行這個預存程序權限。 `Ole Automation Procedures` 組態必須是**啟用**使用 OLE Automation 與相關的任何系統程序。  
  
## <a name="examples"></a>範例  
 下列範例會設定`HostName`屬性 (先前建立**SQLServer**物件) 為新值。  
  
```  
EXEC @hr = sp_OASetProperty @object, 'HostName', 'Gizmo';  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END'  
```  
  
## <a name="see-also"></a>另請參閱  
 [OLE Automation 預存程序&#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [OLE Automation 範例指令碼](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
