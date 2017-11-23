---
title: "方針和限制的 SQLXML 4.0 |Microsoft 文件"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: SQLXML, about SQLXML
ms.assetid: fe433d30-90a1-421e-85c6-af13294dc18d
caps.latest.revision: "27"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bca1dc1397cd0b74f7c5aef050a7d450d3e6bb8e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="guidelines-and-limitations-of-sqlxml-40"></a>SQLXML 4.0 的指導方針和限制
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]使用 SQLXML 4.0 時，請記住下列：  
  
-   當做查詢結果傳回的 XML 不會針對產生此 XML 的對應結構描述進行驗證。  
  
-   SQLXML 4.0 同時包含與版本無關以及與版本相關的 PROGID。 建議您所有的實際執行應用程式都應該使用與版本相關的 PROGID。 這一點特別重要，因為 SQLXML 4.0 並非完全具有回溯相容性。 當您安裝更新的版本時，使用與版本相關的 PROGID 會防止您的實際執行可能發生的失敗。 在不同的版本之間，程式行為可能會因為各種原因而失敗，例如錯誤修正、可能的設計變更等等。 當您安裝更新的版本時，使用與版本相關的 PROGID 會防止發生非預期的失敗。 如果在您安裝更新的版本時使用與版本相關的 PROGID，您的應用程式將會繼續運作，而不會發生失敗。 如果您決定變更與之前版本相關的 PROGID，並在較新的版本中使用與最近版本相關的 PROGID，您必須先測試應用程式，然後才能實際執行它。 例如，使用與版本無關之 PROGID 的應用程式可能會在以下案例中發生失敗：  
  
     您正在執行使用 SQLXML 4.0 以及與版本無關之 PROGID 的應用程式，而且您決定安裝某個其他軟體程式。 此程式可能會安裝舊版的 SQLXML。 您的應用程式可能會失敗，因為應用程式內與版本無關的 PROGIDS 現在指向舊版的 SQLXML，它不一定擁有您的應用程式所使用的 SQLXML 功能。  
  
-   如果基於任何理由，您不想要使用 SQLXMLOLEDB 提供者，而想改為將 sqloledb 提供者用於 SQLXML 功能設定**SQLXML Version**屬性為"SQLXML.4.0"。  
  
  
