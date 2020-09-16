---
description: 在 SQL Server Management Studio (SSMS) 損毀之後取得診斷資料
title: 針對 SSMS 沒有回應的系統或損毀進行疑難排解
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c28ffa44-7b8b-4efa-b755-c7a3b1c11ce4
author: markingmyname
ms.author: maghan
ms.reviewer: dnethi
ms.custom: seo-lt-2019
ms.date: 09/18/2019
ms.openlocfilehash: 2a6f7d1ac44b40b1b58ebe0a2a595e9f69f1ab63
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88480060"
---
# <a name="get-diagnostic-data-after-a-sql-server-management-studio-ssms-crash"></a>在 SQL Server Management Studio (SSMS) 損毀之後取得診斷資料

[!INCLUDE[Applies to](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

## <a name="get-full-memory-dump-after-an-unresponsive-system-or-crash"></a>在系統沒有回應或損毀之後，取得完整的記憶體傾印

在 SQL Server Management Studio (SSMS) 停止回應或損毀時，取得完整記憶體傾印。

若要擷取診斷資訊以針對 SSMS 損毀或停止回應進行疑難排解，請遵循下列步驟。

1. 下載 [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx)。

2. 將下載項目解壓縮到資料夾。

3. 開啟命令提示字元，並執行下列命令。

    ```console
    <PathToProcDumpFolder>\procdump.exe -e -h -ma -w ssms.exe
    ```

    若它提示您接受授權合約，請選取 [同意]  。

4. 啟動 SSMS (如果尚未啟動)。

5. 重現問題。

6. 命令提示字元中應該會顯示與寫入傾印檔有關的文字，請等待它完成。

7. 建立新資料夾，並將寫出的 *.dmp 檔案複製到該資料夾。

8. 將下列檔案複製到相同的資料夾。

    "C:\Windows\Microsoft.NET\Framework\v4.0.30319\mscordacwks.dll"  "C:\Windows\Microsoft.NET\Framework\v4.0.30319\SOS.dll"  "C:\Windows\Microsoft.NET\Framework\v4.0.30319\clr.dll"

9. 壓縮資料夾

## <a name="get-full-memory-dump-for-an-outofmemoryexception"></a>取得 OutOfMemoryException 的完整記憶體傾印

在 SSMS 擲回 OutOfMemoryException 時，取得 SSMS 的完整記憶體傾印。

您可以使用任何受控例外狀況來取得完整的記憶體傾印。

若要擷取診斷資訊以針對 SSMS 的 OutOfMemoryException 進行疑難排解，請遵循下列步驟。

1. 下載 [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx)。

2. 將下載項目解壓縮到資料夾。

3. 開啟命令提示字元，並執行下列命令。

    ```console
    <PathToProcDumpFolder>\procdump.exe -e 1 -f System.OutOfMemoryException -ma -w ssms.exe
    ```

    若它提示您接受授權合約，請選取 [同意]  。

4. 啟動 SQL Server Management Studio (若尚未啟動的話)。

5. 重現問題。

6. 命令提示字元中應該會顯示與寫入傾印檔有關的文字，請等待它完成。

7. 建立新資料夾，並將寫出的 *.dmp 檔案複製到該資料夾。

8. 將下列檔案複製到相同的資料夾。

    "C:\Windows\Microsoft.NET\Framework\v4.0.30319\mscordacwks.dll"  "C:\Windows\Microsoft.NET\Framework\v4.0.30319\SOS.dll"  "C:\Windows\Microsoft.NET\Framework\v4.0.30319\clr.dll"

9. 壓縮資料夾。
