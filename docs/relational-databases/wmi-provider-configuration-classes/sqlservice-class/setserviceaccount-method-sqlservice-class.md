---
title: SetServiceAccount 方法（SqlService）
ms.custom: seo-lt-2019
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetServiceAccount Method (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetServiceAccount method
ms.assetid: d5782892-e9d8-4d48-92af-b3afe9610f84
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b500ca0f879430f0e5655348bdeebda0e0921292
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "73660902"
---
# <a name="setserviceaccount-method-sqlservice-class"></a>SetServiceAccount 方法 (SqlService 類別)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  嘗試變更服務執行個體執行時所使用的使用者名稱和密碼。  
  
## <a name="syntax"></a>語法  
  
```  
  
object.SetServiceAccount(ServiceStartName , ServiceStartPassword)  
```  
  
## <a name="parts"></a>組件  
 *目標*  
 表示此服務的 [SqlService 類別](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) 物件。  
  
#### <a name="parameters"></a>參數  
 *ServiceStartName*  
 指定此服務執行時所使用之帳戶名稱的字串值。 根據服務類型而定，此帳戶名稱可能是 DomainName\Username 的格式。 當它執行時，將會使用兩種格式的其中一種來記錄服務處理序：  
  
-   如果帳戶屬於內建網域，可以指定 \Username。  
  
-   如果指定了 Null，服務就會以**LocalSystem**帳戶的身分登入。  
  
 若是核心或系統層級的驅動程式， *StartName*會包含驅動程式物件名稱（\FileSystem\Rdr 或 \driver\xns)），以供 i/o 系統用來載入設備磁碟機。 如果指定了 NULL，將會根據類似 DWDOM\Admin 的服務名稱，使用 I/O 系統所建立的預設物件名稱來執行驅動程式。  
  
 *ServiceStartPassword*  
 字串值，指定*StartName*參數中帳戶名稱的密碼。 如果您不要變更密碼，請指定 NULL。 如果此服務沒有密碼，請指定空字串。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 **Uint32**值，如果已成功修改服務，則為0，如果不支援要求則為1。 任何其他數字表示發生錯誤。  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
