---
title: Filestream 存取層級伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], access level
- filestream access level
ms.assetid: b88f6ff2-795e-4730-bfb8-dbc6a958f2ad
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 90b4ec97a3ab31c93e92219b96724b75d7f86425
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "62782253"
---
# <a name="filestream-access-level-server-configuration-option"></a>檔案資料流存取層級伺服器組態選項
  您可以使用 filestream_access_level 選項來變更這個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的 FILESTREAM 存取層級。  
  
> [!NOTE]  
>  您必須先針對 FILESTREAM 啟用 Windows 管理設定，然後這個選項才會生效。 當您安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員時，可以啟用這些設定。  
  
|值|定義|  
|-----------|----------------|  
|0|針對這個執行個體停用 FILESTREAM 支援。|  
|1|針對 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存取啟用 FILESTREAM。|  
|2|針對 [!INCLUDE[tsql](../../includes/tsql-md.md)] 和 Win32 資料流存取啟用 FILESTREAM。|  
  
## <a name="see-also"></a>另請參閱  
 [Database Engine 組態 - Filestream](../../sql-server/install/database-engine-configuration-filestream.md)   
 [啟用及設定 FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md)  
  
  
