---
title: StartMode 屬性 （SqlService 類別） |Microsoft Docs
ms.custom: ''
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
manager: craigg
ms.openlocfilehash: 79b79347b03eda5540e59b00dd23c26c7c19bd1d
ms.sourcegitcommit: 6c9d35d03c1c349bc82b9ed0878041d976b703c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2018
ms.locfileid: "51214996"
---
# <a name="startmode-property-sqlservice-class"></a>StartMode 屬性 (SqlService 類別)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
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
 值 = 1。 服務開始著手**IoInitSystem**方法。 這個選項只對驅動程式服務有效。  
  
 自動  
 值 = 2。 要由服務控制管理員在系統啟動期間自動啟動的服務。  
  
 手動  
 值 = 3。 要啟動由電腦管理員，當處理程序呼叫的服務**StartService**方法。  
  
 已停用  
 值 = 4。 無法啟動服務。  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [啟動及停止服務](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
