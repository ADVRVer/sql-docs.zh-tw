---
title: 命令物件概觀 |Microsoft 文件
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- command object [ADO]
ms.assetid: e84a14b1-3c2a-4f7d-a966-9e08a93948df
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cdb2d323b57a63d0ffc84044ece0604571d04164
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="command-object-overview"></a>命令物件概觀
與**命令**物件，您可以執行下列：  
  
-   使用定義的命令 （例如，SQL 陳述式或預存程序） 的可執行檔文字**CommandText**屬性。  
  
-   使用參數化的查詢或預存程序引數定義**參數**物件和**參數**集合。  
  
-   執行命令，並傳回**資料錄集**物件，如果適當，請使用**Execute**方法。  
  
-   使用指定的命令類型**CommandType**屬性，再執行，以最佳化效能。  
  
-   使用指定的命令文字的特定資訊**方言**屬性**命令**物件。  
  
-   控制是否提供者會使用儲存之前執行命令的已備妥 （或編譯） 版本**已準備**屬性。  
  
-   設定提供者等候命令執行所使用的秒數**CommandTimeout**屬性。  
  
-   建立與開啟的連接關聯**命令**物件藉由設定其**ActiveConnection**屬性。  
  
-   設定**名稱**屬性來識別**命令**物件上相關聯的方法為**連接**物件。  
  
-   傳遞**命令**物件**來源**屬性**資料錄集**為了取得資料。  
  
-   傳遞**資料流**包含命令 （例如，XML 命令） 來支援它的提供者的物件。
