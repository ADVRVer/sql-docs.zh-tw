---
title: "了解資料列鎖定 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63c76a2f-f2b9-461f-8904-acbda0169ac3
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7b41b33aa022bc0a62996e09a713f36bbe04e816
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="understanding-row-locking"></a>了解資料列鎖定
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]資料列鎖定。 這些鎖定會針對同時在資料庫中執行修改的多位使用者實作並行控制。 根據預設，交易和鎖定會針對每一個連接進行管理。 例如，如果應用程式開啟兩個 JDBC 連接，一個連接所取得的鎖定無法與另一個連接共用。 這兩個連接都無法取得會與另一個連接所保留之鎖定產生衝突的鎖定。  
  
> [!NOTE]  
>  如果有使用資料列鎖定，提取緩衝區中的所有資料列都會遭到鎖定，因此，非常大的提取大小設定可能會影響並行。  
  
 鎖定的使用是為確保交易完整性與資料庫一致性。 鎖定可防止使用者讀取由其他使用者變更的資料，以及防止多個使用者同時變更相同的資料。 如果沒有使用鎖定，資料庫中的資料可能會變成邏輯上不正確，而且根據該資料執行的查詢可能會產生非預期的結果。  
  
> [!NOTE]  
>  如需有關資料列鎖定的[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]，請參閱 」 中的鎖定[!INCLUDE[ssDE](../../includes/ssde_md.md)]」 中[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]線上叢書 》。  
  
## <a name="see-also"></a>另請參閱  
 [JDBC 驅動程式管理結果集](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)  
  
  
