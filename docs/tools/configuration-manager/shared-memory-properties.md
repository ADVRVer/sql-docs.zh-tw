---
title: 共用記憶體屬性 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- shared memory [SQL Server]
ms.assetid: dc1704da-eacd-4d26-b529-c996f958ca4b
caps.latest.revision: 21
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: 48cf75a64fea6b82b5417b57e431fa347d867c9d
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2018
ms.locfileid: "42786459"
---
# <a name="shared-memory-properties"></a>共用記憶體屬性
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  您可以使用 [共用記憶體屬性] 對話方塊上的 [通訊協定] 頁面來檢視與啟用共用記憶體通訊協定。 共用記憶體是使用上最簡單的通訊協定，而且不用設定任何設定。 因為使用共用記憶體通訊協定的用戶端，只能連接到在相同電腦上執行的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，所以不適用於大部分資料庫活動。 當您懷疑其他通訊協定的設定不正確時，請使用共用記憶體通訊協定進行疑難排解。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 必須重新啟動下列項目，才能啟用或停用通訊協定。  
  
## <a name="options"></a>選項。  
 **已啟用**  
 可能的值為 [是] 和 [否]。 根據預設，已啟用共用記憶體通訊協定。  
  
## <a name="see-also"></a>另請參閱  
 [選擇網路通訊協定](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)   
 [使用共用記憶體通訊協定建立有效的連接字串](../../tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
  
