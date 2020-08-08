---
title: " (OracleToSQL) 建立測試案例 |Microsoft Docs"
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Test Case Wizard
ms.assetid: 22f38901-ec35-4707-a911-784e6ad8dafb
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: 270d904c11df5ab28062cd83672071319ca6f17f
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2020
ms.locfileid: "87934951"
---
# <a name="creating-test-cases-oracletosql"></a>建立測試案例 (OracleToSQL)
使用 [測試案例] Wizard 建立測試。 此 wizard 可讓您藉由選擇已測試和已驗證的物件，並藉由指定測試參數來建立測試案例。  
  
## <a name="starting-the-test-case-wizard"></a>啟動測試案例嚮導  
若要啟動測試案例，請按一下 [測試**人員**] 功能表中的 [**新增測試案例 ...** ]。  
  
啟動時，嚮導會尋找來源 Oracle 伺服器上的架構 SSMATESTER_ORACLE。 這是用來儲存輔助物件的測試人員延伸模組架構。 如果 [測試案例嚮導] 找不到 SSMATESTER_ORACLE，就會顯示建議建立架構的交談視窗。  (這種情況通常會在第一次執行 SSMA 測試器時發生。 )   
  
如果您看到交談視窗，請按一下 [**是**]，在來源伺服器上建立 SSMATESTER_ORACLE 架構。 請注意，您必須具有 Oracle 許可權，才能建立新的使用者，並在此使用者的架構中建立物件。  
  
## <a name="overview-of-creating-test-cases-using-the-wizard"></a>使用 Wizard 建立測試案例的總覽  
建立測試案例的套裝程式含五個步驟：  
  
1.  [&#40;OracleToSQL&#41;初始化測試案例](../../ssma/oracle/initializing-test-cases-oracletosql.md)  
  
2.  [選取並設定要測試的物件 &#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-objects-to-test-oracletosql.md)  
  
3.  [選取並設定受影響的物件 &#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
  
4.  [自訂呼叫順序 &#40;OracleToSQL&#41;](../../ssma/oracle/customizing-calls-order-oracletosql.md)  
  
5.  [完成測試案例準備 &#40;OracleToSQL&#41;](../../ssma/oracle/finishing-test-case-preparation-oracletosql.md)  
  
## <a name="see-also"></a>另請參閱  
[&#40;OracleToSQL&#41;測試遷移的資料庫物件](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
