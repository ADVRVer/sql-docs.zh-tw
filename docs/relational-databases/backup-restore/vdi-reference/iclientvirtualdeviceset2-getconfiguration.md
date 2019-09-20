---
title: IClientVirtualDeviceSet2::GetConfiguration
titlesuffix: SQL Server VDI reference
description: 本文提供 IClientVirtualDeviceSet2::GetConfiguration 命令的參考。
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5d7d42d081b0494feeb5c2b221575e0d5df1143a
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70847449"
---
# <a name="iclientvirtualdeviceset2getconfiguration-vdi"></a>IClientVirtualDeviceSet2::GetConfiguration (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**GetConfiguration** 函式是用來等候伺服器設定虛擬裝置集。

## <a name="syntax"></a>語法

```c
HRESULT IClientVirtualDeviceSet2::GetConfiguration (
   DWORD         dwTimeOut,
   VDConfig*      pCfg
);
```

## <a name="parameters"></a>參數

*DwTimeOut* 這是逾時值 (以毫秒為單位)。 請使用 INFINITE 以避免逾時。

*pCfg* 成功執行時，這會包含伺服器所選取的設定。 如需詳細資訊，請參閱＜設定＞。

## <a name="return-value"></a>傳回值

|傳回值 | 說明 |
|---|---|
| NOERROR | 已傳回設定。 |
| VD_E_ABORT | 已叫用 SignalAbort。 |
| VD_E_TIMEOUT | 函數逾時。 |

## <a name="remarks"></a>Remarks

此函式會封鎖並處於「可警示」狀態。 成功叫用之後，即可開啟虛擬裝置集中的裝置。

## <a name="next-steps"></a>後續步驟

如需詳細資訊，請參閱 [SQL Server 虛擬裝置介面參考概觀](reference-virtual-device-interface.md)。