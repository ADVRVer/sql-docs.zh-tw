---
description: 了解資料列鎖定
title: 了解資料列鎖定 | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 63c76a2f-f2b9-461f-8904-acbda0169ac3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 69b04db86ce8784f5f346a4ac0d19b2bedd0e456
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88488011"
---
# <a name="understanding-row-locking"></a>了解資料列鎖定

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 會使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料列鎖定。 這些鎖定會針對同時在資料庫中執行修改的多位使用者實作並行控制。 根據預設，交易和鎖定會針對每一個連接進行管理。 例如，如果應用程式開啟兩個 JDBC 連接，一個連接所取得的鎖定無法與另一個連接共用。 這兩個連接都無法取得會與另一個連接所保留之鎖定產生衝突的鎖定。

> [!NOTE]  
> 如果有使用資料列鎖定，提取緩衝區中的所有資料列都會遭到鎖定，因此，非常大的提取大小設定可能會影響並行。

鎖定的使用是為確保交易完整性與資料庫一致性。 鎖定可防止使用者讀取由其他使用者變更的資料，以及防止多個使用者同時變更相同的資料。 如果沒有使用鎖定，資料庫中的資料可能會變成邏輯上不正確，而且根據該資料執行的查詢可能會產生非預期的結果。

> [!NOTE]  
> 如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之資料列鎖定的詳細資訊，請參閱 [!INCLUDE[ssDE](../../includes/ssde_md.md)] 線上叢書中的＜[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的鎖定＞。

## <a name="see-also"></a>另請參閱

[使用 JDBC 驅動程式管理結果集](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)
