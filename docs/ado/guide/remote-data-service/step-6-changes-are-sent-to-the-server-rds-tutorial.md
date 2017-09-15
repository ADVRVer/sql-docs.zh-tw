---
title: "步驟 6： 變更傳送到伺服器 （RDS 教學課程） |Microsoft 文件"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDS tutorial [ADO], changes sent to server
ms.assetid: b1e927d6-7d50-4978-9eef-045043cdce7a
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b811d4b5fb1809c0e528f644f28d81559d5df6b6
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="step-6-changes-are-sent-to-the-server-rds-tutorial"></a>步驟 6： 變更傳送到伺服器 （RDS 教學課程）
如果**資料錄集**物件編輯，可以傳送至伺服器 （也就是資料列會加入、 變更或刪除） 的任何變更。  
  
> [!NOTE]
>  RDS 的預設行為可以叫用隱含 ADO 物件和 Microsoft OLE DB 遠端服務提供者。 查詢可以傳回**資料錄集**s，並編輯**資料錄集**s 可以更新資料來源。 本教學課程不會呼叫 RDS 使用 ADO 物件，但這是如何起來會像這樣如果：  
  
```  
Dim rs as New ADODB.Recordset  
rs. "SELECT * FROM Authors","=MS Remote;=Pubs;" & _  
=http://yourServer;=SQLOLEDB;"  
...              ' Edit the Recordset.  
rs.   ' The equivalent of   
...  
```  
  
 **組件 A**您只能使用此案例假設[.RDSDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)而且**資料錄集**物件現在與相關聯**.RDSDataControl**。 [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md)方法的任何變更，以更新資料來源**資料錄集**物件，如果[伺服器](../../../ado/reference/rds-api/server-property-rds.md)和[連接](../../../ado/reference/rds-api/connect-property-rds.md)仍會設定屬性。  
  
```  
Sub RDSTutorial6A()  
Dim DC as New RDS.DataControl  
Dim RS as ADODB.Recordset  
DC. = "http://yourServer"  
DC. = "DSN=Pubs"  
DC. = "SELECT * FROM Authors"  
DC.  
...  
Set RS = DC.  
   ' Edit the Recordset.  
...  
DC.  
...  
```  
  
 **組件 B**或者，您無法更新伺服器[RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)物件，指定連接和**資料錄集**物件。  
  
```  
Sub RDSTutorial6B()  
Dim DS As New RDS.DataSpace  
Dim RS As ADODB.Recordset  
Dim DC As New RDS.DataControl  
Dim DF As Object  
Dim blnStatus As Boolean  
Set DF = DS.("RDSServer.DataFactory", "http://yourServer")  
Set RS = DF. ("DSN=Pubs", "SELECT * FROM Authors")  
DC. = RS    ' Visual controls can now bind to DC.  
    ' Edit the Recordset.  
blnStatus = DF."DSN=Pubs", RS  
End Sub  
```  
  
 **這是教學課程結束時。**  
  
> [!IMPORTANT]
>  從 Windows 8 和 Windows Server 2012 開始，RDS 伺服器元件已不再包含在 Windows 作業系統中 (請參閱 < Windows 8 和[Windows Server 2012 相容性手冊](https://www.microsoft.com/en-us/download/details.aspx?id=27416)如需詳細資訊)。 Windows 的未來版本將移除 RDS 用戶端元件。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 使用 RDS 的應用程式應該移轉到[WCF 資料服務](http://go.microsoft.com/fwlink/?LinkId=199565)。  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft OLE DB 的遠端服務提供者 （ADO 服務提供者）](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md)   
 [RDS 教學課程](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [RDS 教學課程 (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   

