---
title: 教學課程：準備伺服器進行複寫 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: ce30a095-2975-4387-9377-94a461ac78ee
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8e82c71834a2d41a7620f549bc6335fa15df84bf
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2018
ms.locfileid: "52813990"
---
# <a name="tutorial-preparing-the-server-for-replication"></a>教學課程：準備伺服器進行複寫
  在設定複寫拓撲之前，規劃安全性是很重要的步驟。 此教學課程為您示範：如何讓複寫拓撲有更強固的保護，以及如何設定散發，這是複寫資料的第一步。 您必須完成此教學課程，才能進行任何其他教學課程。  
  
> [!NOTE]  
>  若要在伺服器之間安全地複寫資料，必須實作 [複寫安全性最佳做法](security/replication-security-best-practices.md)中的所有建議。  
  
## <a name="what-you-will-learn"></a>學習內容  
 在此教學課程中，您將學習如何準備伺服器，以便在最低權限下安全地執行複寫。 第 1 課示範如何建立用來執行複寫代理程式的 Windows 服務帳戶。 第 2 課示範如何設定用來產生及儲存發行集快照集的資料夾。 第 3 課示範如何設定散發及設定權限。  
  
## <a name="requirements"></a>需求  
 此教學課程是特別提供給熟悉基本資料庫作業但只稍微涉獵複寫作業的使用者。  
  
 若要使用這個教學課程，系統上必須已安裝下列元件：  
  
-   [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 與 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫。 為了加強安全性，依預設，不會安裝範例資料庫。  
  
 **完成這個教學課程的估計時間：30 分鐘。**  
  
## <a name="lessons-in-this-tutorial"></a>本教學課程中的課程  
  
-   [第 1 課：建立 Windows 帳戶的複寫](lesson-1-creating-windows-accounts-for-replication.md)  
  
-   [第 2 課：準備快照集資料夾](lesson-2-preparing-the-snapshot-folder.md)  
  
-   [第 3 課：設定散發](lesson-3-configuring-distribution.md)  
  
 [開始教學課程](lesson-1-creating-windows-accounts-for-replication.md)  
  
## <a name="see-also"></a>另請參閱  
 [[設定散發]](configure-distribution.md)   
 [安全性與保護 &#40;複寫&#41;](security/security-and-protection-replication.md)  
  
  
