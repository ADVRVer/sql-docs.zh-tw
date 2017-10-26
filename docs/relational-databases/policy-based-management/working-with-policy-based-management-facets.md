---
title: "使用原則式管理 Facets | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- viewing Policy-Based Management facets
- facets [Policy-Based Management], copying
- facets [Policy-Based Management], viewing
- copying Policy-Based Management facets
ms.assetid: 88d025c4-07c2-4e4d-8634-204249a8c82c
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8e7ea0859fb39ea23886b650a71b9f818de76c72
ms.contentlocale: zh-tw
ms.lasthandoff: 06/22/2017

---
# <a name="working-with-policy-based-management-facets"></a>使用原則式管理 Facet
  原則式管理 Facet 是一組與所需管理區域相關的邏輯屬性。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 包含數個預先定義的 Facet。 例如，介面區組態 Facet 會將預設關閉的功能定義成屬性。  
  
 當您管理許多相似的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 環境時，可以在其中一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體內設定 Facet、將此 Facet 的狀態複製到檔案，然後將該檔案當作原則匯入到另一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中。 當此狀態已經轉換成原則時，該原則就可以套用至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的其他執行個體、執行個體物件、資料庫或資料庫物件。  
  
 此主題描述如何將 Facet 的狀態複製到 XML 檔。  
  
##  <a name="BeforeYouBegin"></a> Permissions  
 本主題中的程序需要 msdb 資料庫的 PolicyAdministratorRole 角色成員資格。  
  
## <a name="viewing-and-copying-facet-states"></a>檢視和複製 Facet 狀態  
 [檢視 SQL Server 物件的原則式管理 Facet](../../relational-databases/policy-based-management/view-the-policy-based-management-facets-on-a-sql-server-object.md)  
  
 [將原則式管理 Facet 狀態複製到 XML 檔案](../../relational-databases/policy-based-management/copy-a-policy-based-management-facet-state-to-an-xml-file.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用原則式管理來管理伺服器](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  

