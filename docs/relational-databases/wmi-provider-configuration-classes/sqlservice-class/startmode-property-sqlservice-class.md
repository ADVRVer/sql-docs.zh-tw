---
title: StartMode 屬性（SqlService）
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- StartMode Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- StartMode property
ms.assetid: c0c2c7f8-d4ae-44f2-ad8e-aecfcb7c2878
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1adda63135bc85ae2d8a84a8e8744b04144781de
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85662112"
---
# <a name="startmode-property-sqlservice-class"></a>StartMode 屬性 (SqlService 類別)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  取得服務的啟動模式。  
  
## <a name="syntax"></a>語法  
  
```  
  
object.StartMode [= value]  
```  
  
## <a name="parts"></a>組件  
 *object*  
 表示此服務的 [SqlService 類別](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) 物件。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 指定服務模式的 uint32 值。  
  
 它可以是下列其中一個值。  
  
 Boot  
 值 = 0。 由作業系統載入程式啟動的服務。 這個選項只對驅動程式服務有效。  
  
 系統  
 值 = 1。 由**IoInitSystem**方法啟動的服務。 這個選項只對驅動程式服務有效。  
  
 自動  
 值 = 2。 要由服務控制管理員在系統啟動期間自動啟動的服務。  
  
 手動  
 值 = 3。 當進程呼叫**StartService**方法時，要由電腦系統管理員啟動的服務。  
  
 已停用  
 值 = 4。 無法啟動服務。  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
