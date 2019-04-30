---
title: EditModeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EditModeEnum
helpviewer_keywords:
- EditModeEnum enumeration [ADO]
ms.assetid: 45d54b6e-db2c-4553-9fd0-528147d6da2f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 34583128e3da1bec00003fe194d3387783815275
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63181107"
---
# <a name="editmodeenum"></a>EditModeEnum
指定編輯一筆記錄的狀態。  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|**adEditNone**|0|表示未編輯的作業正在進行中。|  
|**adEditInProgress**|1|指出目前記錄中的資料已修改但尚未儲存。|  
|**adEditAdd**|2|指出[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)呼叫的方法，並複製緩衝區中目前的記錄是尚未儲存在資料庫中的新記錄。|  
|**adEditDelete**|4|指出目前資料錄已被刪除。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 對等項目  
 封裝： **com.ms.wfc.data**  
  
|常數|  
|--------------|  
|AdoEnums.EditMode.NONE|  
|AdoEnums.EditMode.INPROGRESS|  
|AdoEnums.EditMode.ADD|  
|AdoEnums.EditMode.DELETE|  
  
## <a name="applies-to"></a>適用於  
 [EditMode 屬性](../../../ado/reference/ado-api/editmode-property.md)
