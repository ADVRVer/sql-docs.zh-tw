---
title: CERT_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CERT_ID
- CERT_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- identification numbers [SQL Server], certificates
- CERT_ID function
- IDs [SQL Server], certificates
- certificates [SQL Server], IDs
ms.assetid: 59cc06f5-272e-4936-8afe-afba7aba8eea
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: ee18027e5c6c916f1ab3d0ca9c6bb501822c1d3b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="certid-transact-sql"></a>CERT_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

此函式會傳回憑證的識別碼值。
  
![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>語法  
  
```sql
Cert_ID ( 'cert_name' )  
```  
  
## <a name="arguments"></a>引數  
**'** *cert_name* **'**  

資料庫中憑證的名稱。
  
## <a name="return-types"></a>傳回類型
 **int**  
  
## <a name="remarks"></a>Remarks  
[sys.certificates](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md) 目錄檢視會顯示憑證名稱。
  
## <a name="permissions"></a>Permissions  
需要憑證的適當權限，並且需要呼叫端尚未拒絕憑證的 VIEW DEFINITION 權限。 如需憑證權限的詳細資訊，請參閱 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md#permissions)。
  
## <a name="examples"></a>範例  
此範例會傳回名為 `ABerglundCert3` 之憑證的識別碼。
  
```sql
SELECT Cert_ID('ABerglundCert3');  
GO  
```  
  
## <a name="see-also"></a>另請參閱
[sys.certificates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)  
[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)  
[加密階層](../../relational-databases/security/encryption/encryption-hierarchy.md)
  
  
