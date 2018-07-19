---
title: 使用原則式管理 Facets | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- viewing Policy-Based Management facets
- facets [Policy-Based Management], copying
- facets [Policy-Based Management], viewing
- copying Policy-Based Management facets
ms.assetid: 88d025c4-07c2-4e4d-8634-204249a8c82c
caps.latest.revision: 29
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8b2b7217faed4a594c83a7eca6927a24733ac353
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37272594"
---
# <a name="working-with-policy-based-management-facets"></a>使用原則式管理 Facet
  原則式管理 Facet 是一組與所需管理區域相關的邏輯屬性。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 包含數個預先定義的 Facet。 例如，介面區組態 Facet 會將預設關閉的功能定義成屬性。  
  
 當您管理許多相似的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 環境時，可以在其中一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體內設定 Facet、將此 Facet 的狀態複製到檔案，然後將該檔案當作原則匯入到另一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中。 當此狀態已經轉換成原則時，該原則就可以套用至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的其他執行個體、執行個體物件、資料庫或資料庫物件。  
  
 此主題描述如何將 Facet 的狀態複製到 XML 檔。  
  
##  <a name="BeforeYouBegin"></a> Permissions  
 本主題中的程序需要 msdb 資料庫的 PolicyAdministratorRole 角色成員資格。  
  
## <a name="viewing-and-copying-facet-states"></a>檢視和複製 Facet 狀態  
 [檢視 SQL Server 物件的原則式管理 Facet](view-the-policy-based-management-facets-on-a-sql-server-object.md)  
  
 [將原則式管理 Facet 狀態複製到 XML 檔案](copy-a-policy-based-management-facet-state-to-an-xml-file.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用原則式管理來管理伺服器](administer-servers-by-using-policy-based-management.md)  
  
  
