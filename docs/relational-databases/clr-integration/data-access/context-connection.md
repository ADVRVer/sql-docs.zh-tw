---
title: 內容連接 |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context connections [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- context [CLR integration]
ms.assetid: 67dd1925-d672-4986-a85f-bce4fe832ef7
author: rothja
ms.author: jroth
ms.openlocfilehash: 3b091f515af926fb17cea424b4f8875baf0fa83a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68068426"
---
# <a name="context-connection"></a>內容連接
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  內部資料存取的問題是很常見的案例。 也就是說，您想要存取執行 Commn Language Runtime (CLR) 預存程序或函數所在的同一部伺服器。 其中一個選項是使用**SqlClient**建立連接，指定指向本機伺服器的連接字串，然後開啟連接。」 這需要指定認證以進行登入。 連接與預存程式或函式位於不同的資料庫會話中，它可能會有不同的**SET**選項、位於不同的交易中、看不到您的臨時表等等。 如果 Managed 預存程序或函數程式碼是在 SQL Server 處理序中執行的，則會是因為其他使用者已連接至該伺服器並執行 SQL 陳述式來叫用它。 您可能想要讓預存程式或函數在該連接的內容中執行，連同其交易、 **SET**選項等等。 這就稱為內容連接。  
  
 內容連接可讓您在第一次叫用程式碼的同一內容中執行 Transact-SQL 陳述式。 為了取得內容連接，必須使用 "context connection" 連接字串關鍵字，如下列範例所示：  
  
 [C#]  
  
```  
using(SqlConnection connection = new SqlConnection("context connection=true"))   
{  
    connection.Open();  
    // Use the connection  
}  
```  
  
 [Visual Basic]  
  
```  
Using connection as new SqlConnection("context connection=true")  
    connection.Open()  
    ' Use the connection  
End Using  
  
```  
  
## <a name="in-this-section"></a>本節內容  
 [正常連接與內容連接的比較](../../../relational-databases/clr-integration/data-access/context-connections-vs-regular-connections.md)  
 描述正常連接及內容連接之間的差異。  
  
 [一般和內容連接的限制](../../../relational-databases/clr-integration/data-access/context-connections-and-regular-connections-restrictions.md)  
 描述正常連接及內容連接的限制。  
  
  
