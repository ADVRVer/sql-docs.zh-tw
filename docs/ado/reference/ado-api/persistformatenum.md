---
description: PersistFormatEnum
title: PersistFormatEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PersistFormatEnum
helpviewer_keywords:
- PersistFormatEnum enumeration [ADO]
ms.assetid: ebe1a2ab-e9f1-43a2-8f94-b190c9613d70
author: rothja
ms.author: jroth
ms.openlocfilehash: c8c4f917b9c2874e945a3ff523c0d6593386a619
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990079"
---
# <a name="persistformatenum"></a>PersistFormatEnum
指定儲存 [記錄集](./recordset-object-ado.md)的格式。  
  
|持續性|值|描述|  
|--------------|-----------|-----------------|  
|**adPersistADTG**|0|指出 Microsoft Advanced Data TableGram (ADTG) 格式。|  
|**adPersistADO**|1|指出將使用 ADO 本身的可延伸標記語言 (XML)  (XML) 格式。 這個值與 adPersistXML 相同，且包含以提供回溯相容性。|  
|**adPersistXML**|1|指出可延伸標記語言 (XML)  (XML) 格式。|  
|**adPersistProviderSpecific**|2|指出提供者將會使用自己的格式來保存 **記錄集** 。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 相等  
 封裝： **.com. 資料**  
  
|持續性|  
|--------------|  
|AdoEnums.PersistFormat.ADTG|  
|AdoEnums.PersistFormat.XML|  
  
## <a name="applies-to"></a>套用至  
 [Save 方法](./save-method.md)