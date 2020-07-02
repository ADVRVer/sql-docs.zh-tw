---
title: LocalDBStartTracing 函式 |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apiname:
- LocalDBStartTracing
apilocation:
- sqluserinstance.dll
apitype: DLLExport
ms.assetid: c7b83833-6d2a-4a06-9cb7-42767bed52c6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1ece276dca136aaa5f21f9fdc1ab16ffad9ba2d7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765208"
---
# <a name="localdbstarttracing-function"></a>LocalDBStartTracing 函數
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  針對目前 Windows 使用者擁有的所有 SQL Server Express LocalDB 執行個體啟用 API 呼叫的追蹤。  
  
 **標頭檔：** sqlncli。h  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT LocalDBStartTracing();  
```  
  
## <a name="returns"></a>傳回  
 S_OK  
 此函數已成功。  
  
 [LOCALDB_ERROR_XEVENT_FAILED](../../relational-databases/express-localdb-error-messages/localdb-error-xevent-failed.md)  
 無法啟動 LocalDB 執行個體 API 內的 XEvent 引擎。  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 發生意外錯誤。 請參閱事件記錄檔，以取得詳細資料。  
  
## <a name="remarks"></a>備註  
 如需使用 LocalDB API 的程式碼範例，請參閱[SQL Server Express Localdb 參考](../../relational-databases/sql-server-express-localdb-reference.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Express LocalDB 標頭和版本資訊](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  
