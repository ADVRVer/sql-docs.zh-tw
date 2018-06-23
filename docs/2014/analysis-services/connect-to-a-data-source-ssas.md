---
title: 連接到資料來源 (SSAS) |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.bidtoolset.conndatasource.f1
ms.assetid: 1e2b17e9-092b-4af1-8a58-c52b8fe10ff1
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: f33af08d91f2c8e739c9295daed0ae47563ede51
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36034274"
---
# <a name="connect-to-a-data-source-ssas"></a>連接到資料來源 (SSAS)
  **[資料表匯入精靈]** 的這個頁面可讓您建立與各種資料來源之間的新資料來源連接，例如關聯式資料庫、資料摘要和檔案等資料來源。 若要從 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]存取精靈，請按一下 **[模型]** 功能表上的 **[從資料來源匯入]**。  
  
 若要連接至資料來源，您必須先在機器上安裝適當的提供者。 您必須將適當的提供者安裝在工作空間資料庫伺服器上。 若是 32 位元 (x86) 伺服器，必須安裝 32 位元提供者。 若是 64 位元 (x64) 伺服器，必須安裝 64 位元提供者。  
  
 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 一定是在 32 位元處理程序，不管架構為何。 在 64 位元機器上執行 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 時，如果要安裝資料提供者，您應該注意下列事項：  
  
-   針對支援並行安裝 32 位元和 64 位元提供者的提供者，您必須同時安裝兩個提供者。  
  
-   至於 ACE 提供者，您必須安裝 64 位元版本的提供者。 由於 Office 會自動安裝 ACE 提供者，因此您不應該在裝載工作空間資料庫次無器的 64 位元機器上執行 32 位元版本的 Microsoft Office。  
  
     ACE 提供者用來從文字檔、Excel 檔和 Access 檔匯入。 如果不需要這些資料來源的支援，您可以在執行 64 位元工作空間資料庫伺服器的機器上，執行 32 位元版本的 Microsoft Office。  
  
-   針對不支援並行安裝 32 位元和 64 位元提供者的其他提供者，您必須安裝 32 位元提供者。 如果只有 64 位元機器可以使用，您必須使用遠端機器，並將 64 位元提供者安裝為工作空間資料庫伺服器。  
  
  