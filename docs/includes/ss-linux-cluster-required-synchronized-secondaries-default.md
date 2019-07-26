---
ms.openlocfilehash: 2dc81d434714e0a13912fa6f14e1194df5e5afe3
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2019
ms.locfileid: "68215615"
---
> [!NOTE]
> 當您建立資源時，Pacemaker 資源代理程式之後會定期根據可用性群組的設定，自動設定可用性群組上的 `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` 值。 例如，如果可用性群組有三個同步複本，代理程式會將 `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` 設定為 `1`。 如需詳細資訊和其他設定選項，請參閱[可用性群組設定的高可用性和資料保護](../linux/sql-server-linux-availability-group-ha.md)。 