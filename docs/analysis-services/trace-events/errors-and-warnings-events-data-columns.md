---
title: 錯誤和警告事件資料行 |Microsoft 文件
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 84a1f21e5556efcf64e1ff1b7c6d5ab2208d1038
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="errors-and-warnings-events-data-columns"></a>錯誤和警告事件資料行
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  安全性稽核事件類別目錄含有下列事件類別：  
  
-   錯誤類別  
  
 下表列出此事件類別的資料行。  
  
## <a name="error-event-classdata-columns"></a>錯誤事件類別—資料行  
  
|**資料行名稱**|**資料行識別碼**|**資料行類型**|**資料行描述**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|事件類別用於將事件分類。|  
|StartTime|3|5|包含事件開始的時間 (如果有的話)。 篩選所需的格式為 'YYYY-MM-DD' 與 'YYYY-MM-DD HH:MM:SS'。|  
|SessionType|8|8|包含造成錯誤之實體的類型。|  
|Severity|22|1|包含與錯誤事件相關聯之例外狀況的嚴重性層級。 值為：<br /><br /> 0 = 成功<br /><br /> 1 = 參考資訊<br /><br /> 2 = 警告<br /><br /> 3 = 錯誤|  
|成功|23|1|包含錯誤事件的成功或失敗。 值為：<br /><br /> 0 = 失敗<br /><br /> 1 = 成功|  
|錯誤|24|1|包含與錯誤事件相關聯之錯誤的錯誤號碼。|  
|ConnectionID|25|1|包含與錯誤事件相關聯的唯一連接識別碼。|  
|DatabaseName|28|8|包含發生錯誤事件的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體名稱。|  
|NTUserName|32|8|包含與錯誤事件相關聯的 Windows 使用者名稱。|  
|NTDomainName|33|8|包含與登入事件相關聯的 Windows 網域帳戶。|  
|ClientHostName|35|8|包含執行用戶端的電腦名稱。 這個資料行會在用戶端提供主機名稱時填入。|  
|ClientProcessID|36|1|包含用戶端應用程式的處理序識別碼。|  
|ApplicationName|37|8|包含建立伺服器之連接的用戶端應用程式名稱。 這個資料行會填入應用程式所傳送的值，而非程式的顯示名稱。|  
|SessionID|39|8|包含伺服器處理序識別碼 (SPID)，它會唯一識別與錯誤事件相關聯的使用者工作階段。 SPID 直接對應至 XML for Analysis (XMLA) 使用的工作階段 GUID。|  
|SPID|41|1|包含伺服器處理序識別碼 (SPID)，它會唯一識別與錯誤事件相關聯的使用者工作階段。 SPID 直接對應至 XML for Analysis (XMLA) 使用的工作階段 GUID。|  
|TextData|42|9|包含與錯誤事件相關聯的文字資料。|  
|ServerName|43|8|包含發生錯誤事件的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 伺服器執行個體名稱。|  
  
## <a name="see-also"></a>另請參閱  
 [安全性稽核事件類別目錄](../../analysis-services/trace-events/security-audit-event-category.md)  
  
  
