---
title: 使用 XSINIL 參數為 NULL 值產生項目 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, null values
- null values [SQL Server], XML
- ELEMENTS directive
- XSINIL parameter
ms.assetid: 2dbc4e48-1cae-4d83-b371-3265da9687cc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d056959f5e05d3de79fa81d33331390f4decb49a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63205612"
---
# <a name="generate-elements-for-null-values-with-the-xsinil-parameter"></a>使用 XSINIL 參數為 NULL 值產生元素
  **ELEMENTS** 指示詞可建構 XML，在其中每個資料行值都對應到 XML 中的元素。 若資料行值為 NULL，則不會加入任何元素。 若在 ELEMENTS 指示詞上指定選擇性的 **XSINIL** 參數，您可以要求也為 NULL 值建立元素。 在此情況下，對於每個 NULL 資料行值，會傳回一個 **xsi:nil** 屬性設定成 TRUE 的元素。  
  
## <a name="see-also"></a>另請參閱  
 [使用 FOR XML 的 RAW 模式](use-raw-mode-with-for-xml.md)  
  
  
