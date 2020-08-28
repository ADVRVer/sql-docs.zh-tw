---
description: 準備和執行命令
title: 準備和執行命令 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Command object [ADO], preparing and executing commands
ms.assetid: 7448d9ee-7f4b-47e3-be54-2df8c9bbac32
author: rothja
ms.author: jroth
ms.openlocfilehash: 8a4265124c2f86870d84ee703d228d5a760c4735
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2020
ms.locfileid: "88979989"
---
# <a name="preparing-and-executing-commands"></a>準備和執行命令
命令是對提供者發出的指示，可針對基礎資料來源執行某些作業。 例如，SQL 語句是 Microsoft SQL Data Provider 的命令。 在 ADO 中，命令通常是以 **命令** 物件來表示，雖然簡單的命令也可以透過 **連接** 或 **記錄集** 物件來發出。  
  
 您可以使用 **命令** 物件，從提供者要求任何支援的作業類型（假設提供者可以正確地解讀命令字串）。 資料提供者的常見作業是查詢資料庫，並傳回記錄 **集** 物件中的記錄，這可以視為容器來保存結果，以及用來查看結果的工具。 和許多 ADO 物件一樣，視提供者的功能而定，某些 **命令** 物件集合、方法或屬性可能會在參考時產生錯誤。  
  
 除了使用**命令**物件之外，您還可以在**連接**物件上使用**Execute**方法，或在**記錄集**物件上使用**Open**方法來發出命令並執行它。 但是，如果您需要在程式碼中重複使用命令，或需要使用命令傳遞詳細的參數資訊，則應該使用 **command** 物件。 本節稍後將詳細說明這些案例。  
  
> [!NOTE]
>  如果提供者支援，某些 **命令**可將結果集當作二進位資料流程或單一 **記錄** （而不是 **記錄集**）傳回。 此外，某些 **命令**不會在所有 (（例如 SQL Update 查詢) ）傳回任何結果集。 本節將涵蓋最常見的案例，不過：執行以**記錄集**物件的形式傳回結果的**命令**。 如需將結果傳回至 **記錄**或 **串流**s 的詳細資訊，請參閱 [記錄和資料流程](../../../ado/guide/data/records-and-streams.md)。  
  
 此章節包含下列主題。  
  
-   [Command 物件概觀](../../../ado/guide/data/command-object-overview.md)  
  
-   [建立和執行簡單的命令](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Command 物件參數](../../../ado/guide/data/command-object-parameters.md)  
  
-   [使用命令呼叫預存程序](../../../ado/guide/data/calling-a-stored-procedure-with-a-command.md)  
  
-   [在連線物件上呼叫預存程式做為方法](../../../ado/guide/data/calling-a-stored-procedure-as-a-method-on-a-connection-object.md)  
  
-   [具名命令](../../../ado/guide/data/named-commands.md)  
  
-   [傳遞參數給具名命令](../../../ado/guide/data/passing-parameters-to-a-named-command.md)
