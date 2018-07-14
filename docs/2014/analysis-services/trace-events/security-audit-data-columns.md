---
title: 安全性稽核資料行 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Security Audit event category [SQL Server]
ms.assetid: fac1a7f9-5961-4f4b-bb04-847616b505d7
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e0decf6588f44b6026608254fa1a196a310e37ad
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37171559"
---
# <a name="security-audit-data-columns"></a>安全性稽核資料行
  安全性稽核事件類別目錄有下列的事件類別：  
  
||||  
|-|-|-|  
|**事件識別碼**|**事件名稱**|**事件描述**|  
|1|稽核登入|收集自啟動追蹤後的所有新連接事件，例如當用戶端要求連接到執行 SQL Server 執行個體的伺服器時。|  
|2|稽核登出|收集自啟動追蹤後的所有新中斷連接事件，例如當用戶端發出中斷連接命令時。|  
|4|稽核伺服器的啟動和停止|記錄服務關閉、啟動與暫停活動。|  
|18|稽核物件權限事件|記錄物件權限之變更。|  
|19|稽核管理作業事件|記錄伺服器備份/還原/同步處理/附加/卸離/影像載入/影像儲存。|  
  
 下表列出每一個這類事件類別的資料行。  
  
## <a name="audit-login"></a>稽核登入  
  
|||||  
|-|-|-|-|  
|**資料行名稱**|**資料行識別碼**|**資料行類型**|**資料行描述**|  
|EventClass|0|1|事件類別用於將事件分類。|  
|CurrentTime|2|5|事件的開始時間 (如果可以取得的話)。 篩選所需的格式為 'YYYY-MM-DD' 與 'YYYY-MM-DD HH:MM:SS'。|  
|StartTime|3|5|事件的開始時間 (如果可以取得的話)。 篩選所需的格式為 'YYYY-MM-DD' 與 'YYYY-MM-DD HH:MM:SS'。|  
|Severity|22|1|例外狀況的嚴重性層級。|  
|成功|23|1|1 = 成功。 0 = 失敗 (例如，1 表示權限檢查成功，而 0 表示該檢查失敗)。|  
|錯誤|24|1|給定事件的錯誤號碼。|  
|ConnectionID|25|1|唯一的連接識別碼。|  
|NTUserName|32|8|Windows 使用者名稱。|  
|NTDomainName|33|8|使用者所隸屬的 Windows 網域。|  
|ClientHostName|35|8|執行用戶端的電腦名稱。 這個資料行會在用戶端提供主機名稱時填入。|  
|ClientProcessID|36|1|用戶端應用程式的處理序識別碼。|  
|ApplicationName|37|8|建立伺服器連接的用戶端應用程式名稱。 這個資料行會填入應用程式所傳送的值，而非程式的顯示名稱。|  
|NTCanonicalUserName|40|8|標準格式的使用者名稱。 例如，engineering.microsoft.com/software/someone。|  
|ServerName|43|8|產生事件的伺服器名稱。|  
  
## <a name="audit-logout"></a>稽核登出  
  
|**資料行名稱**|**資料行識別碼**|**資料行類型**|**資料行描述**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|事件類別用於將事件分類。|  
|CurrentTime|2|5|事件的開始時間 (如果可以取得的話)。 篩選所需的格式為 'YYYY-MM-DD' 與 'YYYY-MM-DD HH:MM:SS'。|  
|EndTime|4|5|事件結束的時間。 此資料行不會因啟動的事件類別 (如 SQL:BatchStarting 或 SP:Starting) 而擴展。 篩選所需的格式為 'YYYY-MM-DD' 與 'YYYY-MM-DD HH:MM:SS'。|  
|Duration|5|2|事件所花費的時間量 (以毫秒為單位)。|  
|CPUTime|6|2|事件所用的 CPU 時間 (以毫秒為單位)。|  
|成功|23|1|1 = 成功。 0 = 失敗 (例如，1 表示權限檢查成功，而 0 表示該檢查失敗)。|  
|ConnectionID|25|1|唯一的連接識別碼。|  
|NTUserName|32|8|Windows 使用者名稱。|  
|NTDomainName|33|8|使用者所隸屬的 Windows 網域。|  
|ClientHostName|35|8|執行用戶端的電腦名稱。 這個資料行會在用戶端提供主機名稱時填入。|  
|ClientProcessID|36|1|用戶端應用程式的處理序識別碼。|  
|ApplicationName|37|8|建立伺服器連接的用戶端應用程式名稱。 這個資料行會填入應用程式所傳送的值，而非程式的顯示名稱。|  
|NTCanonicalUserName|40|8|標準格式的使用者名稱。 例如，engineering.microsoft.com/software/someone。|  
|ServerName|43|8|產生事件的伺服器名稱。|  
  
## <a name="audit-server-starts-and-stops"></a>稽核伺服器的啟動和停止  
  
|**資料行名稱**|**資料行識別碼**|**資料行類型**|**資料行描述**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|事件類別用於將事件分類。|  
|EventSubclass|1|1|事件子類別提供有關每個事件類別的額外資訊：<br /><br /> 1：執行個體關閉<br /><br /> 2：執行個體已啟動<br /><br /> 3：執行個體暫停<br /><br /> 4：執行個體繼續|  
|CurrentTime|2|5|事件的開始時間 (如果可以取得的話)。 篩選所需的格式為 'YYYY-MM-DD' 與 'YYYY-MM-DD HH:MM:SS'。|  
|Severity|22|1|例外狀況的嚴重性層級。|  
|成功|23|1|1 = 成功。 0 = 失敗 (例如，1 表示權限檢查成功，而 0 表示該檢查失敗)。|  
|錯誤|24|1|給定事件的錯誤號碼。|  
|TextData|42|9|與事件相關的文字資料。|  
|ServerName|43|8|產生事件的伺服器名稱。|  
  
## <a name="audit-object-permission-event"></a>稽核物件權限事件  
  
|**資料行名稱**|**資料行識別碼**|**資料行類型**|**資料行描述**|  
|---------------------|-------------------|---------------------|----------------------------|  
|ObjectID|11|8|物件識別碼 (請注意這是一個字串)。|  
|ObjectType|12|1|物件類型。|  
|ObjectName|13|8|物件名稱。|  
|ObjectPath|14|8|物件路徑。 以物件的父系開頭之父系清單 (以逗號分隔)。|  
|ObjectReference|15|8|物件參考。 針對所有父系使用標記來描述物件，編碼成 XML。|  
|Severity|22|1|例外狀況的嚴重性層級。|  
|成功|23|1|1 = 成功。 0 = 失敗 (例如，1 表示權限檢查成功，而 0 表示該檢查失敗)。|  
|錯誤|24|1|給定事件的錯誤號碼。|  
|ConnectionID|25|1|唯一的連接識別碼。|  
|DatabaseName|28|8|正在執行使用者之陳述式的資料庫名稱。|  
|NTUserName|32|8|Windows 使用者名稱。|  
|NTDomainName|33|8|使用者所隸屬的 Windows 網域。|  
|ClientHostName|35|8|執行用戶端的電腦名稱。 這個資料行會在用戶端提供主機名稱時填入。|  
|ClientProcessID|36|1|用戶端應用程式的處理序識別碼。|  
|ApplicationName|37|8|建立伺服器連接的用戶端應用程式名稱。 這個資料行會填入應用程式所傳送的值，而非程式的顯示名稱。|  
|SessionID|39|8|工作階段 GUID。|  
|NTCanonicalUserName|40|8|標準格式的使用者名稱。 例如，engineering.microsoft.com/software/someone。|  
|SPID|41|1|伺服器處理序識別碼。 這可唯一識別出使用者工作階段， 直接對應到 XML/A 所使用的工作階段 GUID。|  
|TextData|42|9|與事件相關的文字資料。|  
|ServerName|43|8|產生事件的伺服器名稱。|  
  
## <a name="audit-admin-operations-event"></a>稽核管理作業事件  
  
|**資料行名稱**|**資料行識別碼**|**資料行類型**|**資料行描述**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventSubclass|1|1|事件子類別提供有關每個事件類別的額外資訊：<br /><br /> 1： 備份<br /><br /> 2： 還原<br /><br /> 3： 同步處理<br /><br /> 4： 卸離<br /><br /> 5： 附加<br /><br /> 6: imageLoad<br /><br /> 7: ImageSave|  
|Severity|22|1|例外狀況的嚴重性層級。|  
|成功|23|1|1 = 成功。 0 = 失敗 (例如，1 表示權限檢查成功，而 0 表示該檢查失敗)。|  
|錯誤|24|1|給定事件的錯誤號碼。|  
|ConnectionID|25|1|唯一的連接識別碼。|  
|DatabaseName|28|8|正在執行使用者之陳述式的資料庫名稱。|  
|NTUserName|32|8|Windows 使用者名稱。|  
|NTDomainName|33|8|使用者所隸屬的 Windows 網域。|  
|ClientHostName|35|8|執行用戶端的電腦名稱。 這個資料行會在用戶端提供主機名稱時填入。|  
|ClientProcessID|36|1|用戶端應用程式的處理序識別碼。|  
|ApplicationName|37|8|建立伺服器連接的用戶端應用程式名稱。 這個資料行會填入應用程式所傳送的值，而非程式的顯示名稱。|  
|SessionID|39|8|工作階段 GUID。|  
|NTCanonicalUserName|40|8|標準格式的使用者名稱。 例如，engineering.microsoft.com/software/someone。|  
|SPID|41|1|伺服器處理序識別碼。 這可唯一識別出使用者工作階段， 直接對應到 XML/A 所使用的工作階段 GUID。|  
|TextData|42|9|與事件相關的文字資料。|  
|ServerName|43|8|產生事件的伺服器名稱。|  
  
## <a name="see-also"></a>另請參閱  
 [安全性稽核事件類別目錄](security-audit-event-category.md)  
  
  
