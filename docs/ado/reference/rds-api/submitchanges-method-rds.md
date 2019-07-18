---
title: SubmitChanges 方法 (RDS) |Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SubmitChanges method [ADO]
ms.assetid: 250062a4-13c4-4bed-807d-8b9ad81536d4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 783ad55a2355759f7625d536272f5243cd1c61c4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67963283"
---
# <a name="submitchanges-method-rds"></a>SubmitChanges 方法 (RDS)
提交暫止的變更以及與在本機快取可更新[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)中所指定的資料來源[Connect](../../../ado/reference/rds-api/connect-property-rds.md)屬性或有[URL](../../../ado/reference/rds-api/url-property-rds.md)屬性。  
  
> [!IMPORTANT]
>  從 Windows 8 和 Windows Server 2012 開始，RDS 伺服器元件不會再包含在 Windows 作業系統中 (請參閱 Windows 8 和[Windows Server 2012 相容性操作手冊](https://www.microsoft.com/download/details.aspx?id=27416)如需詳細資訊)。 RDS 用戶端元件將會在 Windows 的未來版本中移除。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 使用 RDS 的應用程式應該移轉至[WCF 資料服務](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
## <a name="syntax"></a>語法  
  
```  
  
DataControl.SubmitChanges DataFactory.SubmitChanges Connection, Recordset  
```  
  
#### <a name="parameters"></a>參數  
 *DataControl*  
 物件變數，表示[rds。DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)物件。  
  
 *DataFactory*  
 物件變數，表示[RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)物件。  
  
 *[連接]*  
 A**字串**值，表示與所建立的連接**rds。DataControl**物件的[Connect](../../../ado/reference/rds-api/connect-property-rds.md)屬性。  
  
 *Recordset*  
 物件變數，表示**資料錄集**物件。  
  
## <a name="remarks"></a>備註  
 [Connect](../../../ado/reference/rds-api/connect-property-rds.md)，[伺服器](../../../ado/reference/rds-api/server-property-rds.md)，並[SQL](../../../ado/reference/rds-api/sql-property.md)必須先設定屬性，您可以使用**SubmitChanges**方法**RDS。DataControl**物件。  
  
 如果您呼叫[CancelUpdate](../../../ado/reference/rds-api/cancelupdate-method-rds.md)方法之後呼叫了**SubmitChanges**的相同**資料錄集**物件**CancelUpdate**呼叫失敗，因為已認可變更。  
  
 只有已變更的記錄，修改和變更的所有傳送成功或所有的變更一起失敗。  
  
 您可以使用**SubmitChanges**只能搭配預設**RDSServer.DataFactory**物件。 自訂商務物件無法使用此方法。  
  
 如果**URL**設定的屬性， **SubmitChanges**會將變更提交至由 URL 指定的位置。  
  
## <a name="applies-to"></a>適用於  
  
|||  
|-|-|  
|[DataControl 物件 (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[DataFactory 物件 (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|  
  
## <a name="see-also"></a>另請參閱  
 [SubmitChanges 方法範例 (VBScript)](../../../ado/reference/rds-api/submitchanges-method-example-vbscript.md)   
 [通訊錄命令按鈕](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [CancelUpdate 方法 (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Refresh 方法 (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)



