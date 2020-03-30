---
title: 轉換類型但不檢查轉換 (SQL Server 匯入和匯出精靈) | Microsoft Docs
ms.custom: ''
ms.date: 01/11/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.impexpwizard.nomappingfile.f1
ms.assetid: 87d9d3e5-477f-4117-a37f-bff53ea3e14d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8a6f07634f9f4a3fba48889391a4bfc9e4e245df
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "71285320"
---
# <a name="convert-types-without-conversion-checking-sql-server-import-and-export-wizard"></a>轉換類型但不檢查轉換 (SQL Server 匯入和匯出精靈)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  選取現有資料表和檢視，以複製或檢視您所提供的查詢之後，[ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈] 可能會顯示 [轉換類型但不檢查轉換]  。 當精靈找不到對應來源和目的地間資料類型所需的一或多個資料類型轉換和對應檔時，就會顯示此頁面。 此頁面包含可協助您了解遺漏項目的資訊。
  
 按一下 [下一步]  繼續進行而不知道資料類型轉換是否會成功。 否則，按一下 [上一步]  變更您的選擇，或是按一下 [取消]  以結束精靈。

## <a name="screen-shot-of-the-convert-types-page"></a>[轉換類型] 頁面的螢幕擷取畫面  
  
下列螢幕擷取畫面會顯示精靈的 [轉換類型但不檢查轉換]  頁面範例。

![轉換類型](../../integration-services/import-export-data/media/convert-types.png)

問題是，精靈找不到對應所選目的地資料類型的對應檔案。

本頁資訊不包含遺漏之對應檔的名稱。 因為精靈不知道指定的資料提供者是否有檔案，所以它無法提供遺漏檔案的名稱。

## <a name="whats-next"></a>下一步  
 按一下 [下一步]  同意繼續進行而不知道資料類型轉換是否會成功之後，下一頁是 [儲存並執行封裝]  。 在此頁面上，您可以指定是否要立即執行複製作業。 根據組態，您也可以儲存精靈所建立的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件，以便在稍後進行自訂並重複使用。 如需詳細資訊，請參閱 [儲存和執行封裝](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md)。  

## <a name="see-also"></a>另請參閱
[SQL Server 匯入及匯出精靈的資料類型對應](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md)
