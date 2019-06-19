---
title: 更新資料 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data updates [ADO], about data updates
- updating data [ADO], about updating data
ms.assetid: 6508e4e9-e33a-4dad-b340-5d632fd78a91
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8ea95b7d34f1395f6322d9a6ad6a0229bb8c7e45
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704562"
---
# <a name="updating-data"></a>更新資料
更新行為和功能主要是依據更新模式 （鎖定型別）、 資料指標類型，以及資料指標位置。  
  
 使用**更新**方法來儲存您對目前記錄的任何變更**資料錄集**物件，因為呼叫**AddNew**方法或變更任何欄位值在現有的記錄。 **資料錄集**物件必須支援更新。  
  
 如果**Recordset**物件支援的批次更新，直到您呼叫，在本機，您可以快取讓一或多個記錄的多個變更**UpdateBatch**方法。 如果您正在編輯目前的記錄，或加入新的記錄，當您呼叫**UpdateBatch**方法，ADO 會自動會呼叫**更新**方法，將任何暫止的變更儲存至目前的記錄之前傳輸批次的變更提供者。  
  
 目前的記錄會保留目前之後呼叫**更新**或是**UpdateBatch**方法。  
  
 此章節包含下列主題。  
  
-   [即時模式](../../../ado/guide/data/immediate-mode.md)  
  
-   [批次模式](../../../ado/guide/data/batch-mode.md)  
  
-   [交易處理](../../../ado/guide/data/transaction-processing.md)
