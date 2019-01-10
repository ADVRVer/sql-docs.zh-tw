---
title: 附錄-1 (OracleToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e01f8be5-ce68-4c9f-bd13-d65e73a16470
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: ad627f91cedf04c71d53bf14f8e0427aa531f3f1
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2018
ms.locfileid: "52534034"
---
# <a name="appendix---1-oracletosql"></a>附錄 - 1 (OracleToSQL)
SSMA 主控台命令列選項的快速檢視：  
  
|Sl。 資料分割|參數|必要項？|參數引數|允許的值|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s/script|是|scriptfile|有效的 XML 檔案名稱。<br /><br />主控台指令碼定義檔。|  
|2|-v/變數|否|variablevaluefile|有效的 XML 檔案名稱。<br /><br />如果指令碼檔案中使用變數，則必須指定這個檔案。|  
|3|-c/serverconnection|否|serverconnectionfile|有效的 XML 檔案名稱。<br /><br />此檔案包含伺服器連接資訊。|  
|4|-x/xmloutput|否|xmloutputfile|這個選項表示以 XML 格式的主控台輸出。 如果未指定此選項，預設的輸出是文字格式。<br /><br />如果未指定 xmloutputfile，XML 輸出會導向至`STDOUT`。<br /><br />Xmloutputfile 是以 XML 格式的主控台輸出會寫入至其中之檔案的名稱。|  
|5|-l/記錄檔|否|logfile|有效的檔案名稱。|  
|6|-e/projectenvironment|否|projectenvironmentfolder|有效的資料夾名稱包含 SSMA 專案環境檔案。|  
|7|-p/securepassword|否|-a/加入 {< server_id > [，...n]&#124;所有}-c&#124;serverconnection < 伺服器-連接-檔案 > [-v&#124;變數 < 變數-值-檔案 >] [-o/覆寫]<br /><br />中的多個<br /><br />-a/加入 {< server_id > [，...n]&#124;所有}-s&#124;指令碼 < 指令碼檔案 > [-v&#124;變數 < 變數-值-檔案 >] [-o/覆寫]<br /><br />-r/移除 {< server_id > [，...n]&#124;所有}<br /><br />-l/清單<br /><br />-e/匯出 {< 伺服器識別碼 > [，...n]&#124;所有} < 加密密碼-檔案 ><br /><br />-i / 匯入 {< 伺服器識別碼 > [，...n]&#124;所有} < 加密密碼-檔案 >|如果指定，此選項必須不與其他任何選項結合。<br /><br />伺服器識別碼：提供給 {string} 的伺服器唯一識別碼<br /><br />伺服器連線檔案： 伺服器定義檔案 （serverconnectionfile 或指令碼檔案）。<br /><br />變數值檔案：它是變數的定義檔案，並使用伺服器連線檔案中。<br /><br />加密密碼-檔案：這是使用使用者指定的複雜密碼來加密伺服器密碼檔案。|  
|8|-?|否|不適用|不適用|  
  
## <a name="see-also"></a>另請參閱  
[執行 SSMA 主控台 (Oracle)](https://msdn.microsoft.com/7228ccba-c69f-4b4c-8664-01a2750183c5)  
  
