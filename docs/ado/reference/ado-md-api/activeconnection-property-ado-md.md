---
description: ActiveConnection 屬性 (ADO MD)
title: ActiveConnection 屬性 (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ActiveConnection
- Cellset::ActiveConnection
- Catalog::ActiveConnection
helpviewer_keywords:
- ActiveConnection property [ADO MD]
ms.assetid: 2509b32c-a995-4364-9152-d8c83129bdd8
author: rothja
ms.author: jroth
ms.openlocfilehash: 541f6800a440019d210bdf427ab8dafd58acc3b5
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2020
ms.locfileid: "88987639"
---
# <a name="activeconnection-property-ado-md"></a>ActiveConnection 屬性 (ADO MD)
指出目前的儲存格集或目錄目前所屬的 ADO [連接](../ado-api/connection-object-ado.md) 物件。  
  
## <a name="settings-and-return-values"></a>設定和傳回值  
 設定或傳回包含定義連接或**連接**物件之字串的**變數**。 預設值是空的。  
  
## <a name="remarks"></a>備註  
 您可以將此屬性設定為有效的 ADO **連接** 物件或有效的連接字串。 當這個屬性設定為連接字串時，提供者會使用此定義來建立新的 **連接** 物件，並開啟連接。  
  
 如果您使用[open](./open-method-ado-md.md)方法的*ActiveConnection*引數來開啟[儲存格](./cellset-object-ado-md.md)物件， **ActiveConnection**屬性將會繼承引數的值。  
  
 將[目錄](./catalog-object-ado-md.md)物件的**ActiveConnection**屬性設定為**Nothing** ，就不會釋放相關聯的資料，[包括 CubeDefs](./cubedefs-collection-ado-md.md)集合中的資料，以及任何相關的[維度](./dimension-object-ado-md.md) [、階層](./hierarchy-object-ado-md.md)、[層級](./level-object-ado-md.md)和[成員](./member-object-ado-md.md)物件。 關閉用來開啟**目錄**的**連接**物件，其效果與將**ActiveConnection**屬性設定為**Nothing**一樣。  
  
 變更**目錄**物件的**ActiveConnection**屬性所參考之連接的預設資料庫，會使**目錄**的內容失效。  
  
 如果您嘗試變更開啟的**儲存格**物件的**ActiveConnection**屬性，就會發生錯誤。  
  
> [!NOTE]
>  在 Visual Basic 中，將**ActiveConnection**屬性設定為**連接**物件時，請記得使用**Set**關鍵字。 如果您省略 **Set** 關鍵字，您實際上會將 **ActiveConnection** 屬性設定為等於 **連接** 物件的 default 屬性 **ConnectionString**。 程式碼將可運作;不過，您將會建立其他與資料來源的連接，這可能會對效能造成負面影響。  
  
 使用 MSOLAP 資料提供者時，請將連接字串中的資料來源設定為伺服器名稱，並將初始目錄設定為數據源中的目錄名稱。 若要連接到與伺服器中斷連線的 cube 檔案，請將位置設定為的完整路徑。.CUB 檔。 在任一種情況下，請將提供者設定為提供者名稱。 例如，下列字串會使用 MSOLAP 提供者，連接到名為 **Servername**的伺服器上名為 Bobs-machine Video Store 的目錄：  
  
```  
"Data Source=Servername;Initial Catalog=Bobs Video Store;Provider=msolap"  
```  
  
 下列字串會連接到位置 C:\MSDASDK\samples\oledb\olap\data\bobsvid.cub 的本機 cube 檔案：  
  
```  
"Location=C:\MSDASDK\samples\oledb\olap\data\bobsvid.cub;Provider=msolap"  
```  
  
## <a name="applies-to"></a>套用至  

:::row:::
    :::column:::
        [Catalog 物件 (ADO MD)](./catalog-object-ado-md.md)  
    :::column-end:::
    :::column:::
        [Cellset 物件 (ADO MD)](./cellset-object-ado-md.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>另請參閱  
 [ (VB) 的集格範例 ](./cellset-example-vb.md)   
 [ (ADO) 的 Connection 物件 ](../ado-api/connection-object-ado.md)   
 [Open 方法 (ADO MD)](./open-method-ado-md.md)