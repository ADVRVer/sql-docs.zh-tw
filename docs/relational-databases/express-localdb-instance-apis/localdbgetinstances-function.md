---
title: "LocalDBGetInstances 函數 |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: localdb
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: LocalDBGetInstances
apilocation: sqluserinstance.dll
apitype: DLLExport
ms.assetid: f95a9980-8bc0-426c-8aa1-e2660b6784cf
caps.latest.revision: "13"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 72279150343aafc7f20d368aafcb90f81d8136ec
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="localdbgetinstances-function"></a>LocalDBGetInstances 函數
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]傳回所有的 SQL Server Express LocalDB 執行個體，以指定的版本。  
  
 **標頭檔：** sqlncli.h  
  
## <a name="syntax"></a>語法  
  
```  
#define MAX_LOCALDB_INSTANCE_NAME_LENGTH 128typedef WCHAR TLocalDBInstanceName[MAX_LOCALDB_INSTANCE_NAME_LENGTH + 1];typedef TLocalDBInstanceName* PTLocalDBInstanceName;  
HRESULT LocalDBGetInstances(  
           PTLocalDBInstanceName pInstanceNames,  
           LPDWORD lpdwNumberOfInstances  
);  
```  
  
## <a name="parameters"></a>參數  
 *pInstanceNames*  
 [輸出] 當傳回此函數時，包含使用者工作站上之具名及預設 LocalDB 執行個體的名稱。  
  
 *lpdwNumberOfInstances*  
 [輸入/輸出]輸入時，包含執行個體名稱中的位置數目*pInstanceNames*緩衝區。 輸出時，包含在使用者工作站上找到的 LocalDB 執行個體數目。  
  
## <a name="returns"></a>傳回值  
 S_OK  
 此函數已成功。  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../../relational-databases/express-localdb-error-messages/localdb-error-not-installed.md)  
 SQL Server Express LocalDB 未安裝在電腦上。  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 一個或多個指定的輸入參數無效。  
  
 [LOCALDB_ERROR_INSUFFICIENT_BUFFER](../../relational-databases/express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 輸入緩衝區太短，且未要求截斷。  
  
 [LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG](../../relational-databases/express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 應儲存執行個體的路徑長度超過 MAX_PATH。  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY](../../relational-databases/express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 無法存取執行個體登錄。  
  
 [LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT](../../relational-databases/express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 執行個體組態已損毀。  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 發生意外的錯誤。 請參閱事件記錄檔，以取得詳細資料。  
  
## <a name="remarks"></a>備註  
 如需使用 LocalDB API 的程式碼範例，請參閱[SQL Server Express LocalDB 參考](../../relational-databases/sql-server-express-localdb-reference.md)。  
  
## <a name="see-also"></a>請參閱＜  
 [SQL Server Express LocalDB 標頭和版本資訊](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  
