---
title: 全域設定 （記錄） (DB2ToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: d314a2ca-ea2e-46e0-ae5e-8774841da91b
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 7d632b040a5124d73470ce825af91e254866a0ae
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63299223"
---
# <a name="global-settings-logging-db2tosql"></a>全域設定 （記錄） (DB2ToSQL)
使用**全域設定**對話方塊來指定 SSMA 的記錄設定。 一般而言，您會在與產品支援人員合作時，才變更這些設定。  
  
若要存取此對話方塊中，在**工具**功能表上，選取**全域設定**，然後按一下 **記錄**在左窗格底部的按鈕。  
  
## <a name="options"></a>選項。  
**訊息層級**  
底下有下列選項**訊息層級**:  
  
|選項|描述|  
|----------|---------------|  
|**[所有類別目錄]**|用來設定下列選項的所有的記錄層級。|  
|**Collector**|會收集有關來源結構描述的中繼資料，並將它儲存至專案。|  
|**Converter**|將來源資料庫物件，例如資料表和預存程序的結構轉換成對應[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]結構。|  
|**資料遷移程式**|將資料從來源資料庫移轉[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。|  
|**格式器**|產生的指令碼轉換子的子元件[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]結構描述。|  
|**圖形化使用者介面**|當您使用 SSMA 工具時出現的訊息。|  
|**連結器**|解析的 SQL 識別項，並提供其他元件的資訊。|  
|**其他**|不在任何其他分類中的所有訊息。|  
|**Parser**|剖析來源結構描述。|  
|**同步器**|載入來源資料庫物件[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。|  
|**TreeConverter**|將來源中繼資料中的物件轉換[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中繼資料。|  
|**軟體測試人員**|使用 SSMA 測試人員時，會出現的訊息。|  
  
每個選項底下**訊息層級**，設定其中一個下列的記錄層級的 SSMA:  
  
|||  
|-|-|  
|**嚴重錯誤**|僅嚴重的錯誤訊息寫入記錄檔。|  
|**錯誤**|錯誤和嚴重錯誤訊息寫入記錄檔。|  
|**警告**|寫入記錄檔的警告、 錯誤和嚴重的錯誤訊息。|  
|**Info**|寫入記錄檔的資訊、 警告、 錯誤和嚴重的錯誤訊息。|  
|**偵錯**|寫入所有的訊息，包括偵錯訊息，記錄檔。|  
  
**記錄檔路徑**  
檔案路徑和名稱的 SSMA 記錄檔。 若要指定不同的名稱，按一下目前路徑，然後按一下 瀏覽 (**...**) 按鈕。  
  
**記錄檔大小**  
記錄檔，以 kb 為單位的大小上限。 最小的大小為 10 KB。 預設大小為 10240 KB。  
  
**記錄檔的總數**  
當一個記錄檔填滿時，SSMA 會重新命名記錄檔，並啟動一個新。 使用此設定，指定要保留的記錄檔的數目上限。 最小值為 2。  
  
