---
title: "LocalDBStartTracing 函數 |Microsoft 文件"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: localdb
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- LocalDBStartTracing
apilocation:
- sqluserinstance.dll
apitype: DLLExport
ms.assetid: c7b83833-6d2a-4a06-9cb7-42767bed52c6
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 68f22dcef8c1ee775a89e15fd449f521736cf5a0
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2018
---
# <a name="localdbstarttracing-function"></a>LocalDBStartTracing 函數
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  針對目前 Windows 使用者擁有的所有 SQL Server Express LocalDB 執行個體啟用 API 呼叫的追蹤。  
  
 **標頭檔：** sqlncli.h  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT LocalDBStartTracing();  
```  
  
## <a name="returns"></a>傳回值  
 S_OK  
 此函數已成功。  
  
 [LOCALDB_ERROR_XEVENT_FAILED](../../relational-databases/express-localdb-error-messages/localdb-error-xevent-failed.md)  
 無法啟動 LocalDB 執行個體 API 內的 XEvent 引擎。  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 發生意外的錯誤。 請參閱事件記錄檔，以取得詳細資料。  
  
## <a name="remarks"></a>備註  
 如需使用 LocalDB API 的程式碼範例，請參閱[SQL Server Express LocalDB 參考](../../relational-databases/sql-server-express-localdb-reference.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Express LocalDB 標頭和版本資訊](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  
