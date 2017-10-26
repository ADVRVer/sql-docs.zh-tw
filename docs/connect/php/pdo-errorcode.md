---
title: "Pdo:: errorcode |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5864b1d8-6814-41cd-a88d-415124484c13
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a0104db7e46a377fa78b7f323de6ad237431a032
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="pdoerrorcode"></a>PDO::errorCode
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

PDO::errorCode 會擷取資料庫控制代碼上最新作業的 SQLSTATE。  
  
## <a name="syntax"></a>語法  
  
```  
  
mixed PDO::errorCode();  
```  
  
## <a name="return-value"></a>傳回值  
PDO::errorCode 會以字串形式傳回五字元的 SQLSTATE；如果沒有資料庫控制代碼的作業，則傳回 NULL。  
  
## <a name="remarks"></a>備註  
PDO_SQLSRV 驅動程式中的 PDO::errorCode 會針對某些成功的作業傳回警告。 例如，在成功連接之後，PDO::errorCode 會傳回 "01000"，指出 SQL_SUCCESS_WITH_INFO。  
  
PDO::errorCode 只會針對直接在資料庫連接上執行作業擷取錯誤碼。 如果您透過 PDO::prepare 或 PDO::query 建立 PDOStatement 執行個體，並產生陳述式物件的錯誤，PDO::errorCode 將不會擷取該錯誤。 您必須呼叫 PDOStatement::errorCode，才能傳回在特定陳述式物件上執行之作業的錯誤碼。  
  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]2.0 版已加入 PDO 支援。  
  
## <a name="example"></a>範例  
在此範例中，資料行名稱的拼字錯誤 (`Cityx`而不是`City`)，導致發生錯誤，而後會予以報告。  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks ", "", "");  
$query = "SELECT * FROM Person.Address where Cityx = 'Essen'";  
  
$conn->query($query);  
print $conn->errorCode();  
?>  
```  
  
## <a name="see-also"></a>另請參閱  
[PDO 類別](../../connect/php/pdo-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  

