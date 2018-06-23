---
title: bcp_setbulkmode |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bcp_setbulkmode function
ms.assetid: de56f206-1f7e-4c03-bf22-da9c7f9f4433
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9d4fd20ddc1820c02c24ed79a8d38d416e284908
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36132410"
---
# <a name="bcpsetbulkmode"></a>bcp_setbulkmode
  bcp_setbulkmode 可讓您在大量複製作業，在單一函數呼叫中設定的所有資料行屬性中指定的資料行格式。  
  
## <a name="syntax"></a>語法  
  
```  
  
RETCODE bcp_setbulkmode (  
   HDBC   
hdbc  
,  
   INT   
property  
,  
   void *   
pField  
,  
   INT   
cbField  
,  
   void *   
pRow  
,  
   INT   
cbRow  
);  
  
```  
  
## <a name="arguments"></a>引數  
 *hdbc*  
 已啟用大量複製的 ODBC 連接控制代碼。  
  
 *property*  
 類型為 BYTE 的常數。 如需常數的清單，請參閱＜備註＞一節中的表格。  
  
 *pField*  
 欄位結束字元值的指標。  
  
 *cbField*  
 欄位結束字元值的長度 (以位元組為單位)。  
  
 *pRow*  
 資料列結束字元值的指標。  
  
 *cbRow*  
 資料列結束字元值的長度 (以位元組為單位)。  
  
## <a name="returns"></a>傳回值  
 SUCCEED 或 FAIL  
  
## <a name="remarks"></a>備註  
 bcp_setbulkmode 可用來大量複製查詢或資料表。 Bcp_setbulkmode 大量複製查詢陳述式使用時，它必須之前呼叫 bcp_control 再使用 bcp_hint 來呼叫。  
  
 bcp_setbulkmode 是替代[bcp_setcolfmt](bcp-setcolfmt.md)和[bcp_columns](bcp-columns.md)，它只能讓您指定的每個函式呼叫的一個資料行格式。  
  
 下表列出的常數*屬性*參數。  
  
|屬性|描述|  
|--------------|-----------------|  
|BCP_OUT_CHARACTER_MODE|指定字元輸出模式。<br /><br /> 對應到 BCP 中的 – c 選項。EXE，並與 bcp_setcolfmt`BCP_FMT_TYPE`屬性設定為`SQLCHARACTER`。|  
|BCP_OUT_WIDE_CHARACTER_MODE|指定 Unicode 輸出模式。<br /><br /> 對應到 BCP 中的 – w 選項。EXE 和與 bcp_setcolfmt`BCP_FMT_TYPE`屬性設定為`SQLNCHAR`。|  
|BCP_OUT_NATIVE_TEXT_MODE|指定非字元類型的原生類型和字元類型的 Unicode。<br /><br /> 對應到 BCP 中的 – N 選項。EXE 和與 bcp_setcolfmt`BCP_FMT_TYPE`屬性設定為`SQLNCHAR`如果資料行類型是字串 （預設值如果不是字串）。|  
|BCP_OUT_NATIVE_MODE|指定原生資料庫類型。<br /><br /> 對應到 BCP 中的 – n 選項。EXE 和與 bcp_setcolfmt`BCP_FMT_TYPE`屬性設定為預設值。|  
  
 您不應該使用函式呼叫的序列，包括 bcp_setcolfmt、 bcp_control 和 bcp_readfmt bcp_setbulkmode。 例如，您不應該呼叫 bcp_control(BCPTEXTFILE) 和 bcp_setbulkmode。  
  
 您可以呼叫 bcp_control 和 bcp_setbulkmode bcp_control bcp_setbulkmode 不衝突的選項。 例如，您可以呼叫 bcp_control(BCPFIRST) 和 bcp_setbulkmode。  
  
 如果您想要呼叫的函式呼叫的序列，包括 bcp_setcolfmt、 bcp_control 和 bcp_readfmt bcp_setbulkmode，其中一個函式呼叫會傳回順序錯誤失敗。 如果您選擇要更正失敗，請呼叫 bcp_init 來重設所有設定並重新開始。  
  
 下表將呈現產生函數順序錯誤之函數呼叫的部分範例。  
  
 呼叫順序  
  
```  
bcp_init(“table”, DB_IN);  
bcp_setbulkmode();  
```  
  
```  
bcp_init(“table”, DB_OUT);  
bcp_setbulkmode();  
bcp_readfmt();  
```  
  
```  
bcp_init(NULL, DB_OUT);  
bcp_control(BCPHINTS, “select …”);  
bcp_setbulkmode();  
```  
  
```  
bcp_init(“table”, DB_OUT);  
bcp_setbulkmode();  
bcp_setcolfmt();  
```  
  
```  
bcp_init(“table”, DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_readfmt();  
bcp_setcolfmt();  
```  
  
```  
bcp_init(NULL, DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_setbulkmode();  
bcp_control(BCPHINTS, “select …”);  
bcp_readfmt();  
```  
  
```  
bcp_init(“table”, DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_columns();  
```  
  
```  
bcp_init(“table”, DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_setcolfmt();  
```  
  
## <a name="example"></a>範例  
 下列範例會使用不同的 bcp_setbulkmode 設定來建立四個檔案。  
  
```  
// compile with: sqlncli11.lib odbc32.lib  
  
#include <windows.h>  
#include <stdio.h>  
#include <tchar.h>  
#include <sqlext.h>  
#include "sqlncli.h"  
  
// Global variables  
SQLHENV g_hEnv = NULL;  
SQLHDBC g_hDbc = NULL;  
  
void ODBCCleanUp() {  
   if (g_hDbc) {  
      SQLDisconnect(g_hDbc);  
      SQLFreeHandle(SQL_HANDLE_DBC, g_hDbc);  
      g_hDbc = NULL;  
   }  
   if (g_hEnv) {  
      SQLFreeHandle(SQL_HANDLE_ENV, g_hEnv);  
      g_hEnv = NULL;  
   }  
}  
  
BOOL MakeODBCConnection(TCHAR * pszServer) {  
   TCHAR szConnectionString[500];  
   TCHAR szOutConnectionString[500];  
   SQLSMALLINT iLen;  
   SQLRETURN rc;  
  
   _sntprintf_s(szConnectionString, 500, TEXT("DRIVER={SQL Server Native Client 11.0};Server=%s;Trusted_connection=yes;"), pszServer);  
   rc = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE,&g_hEnv);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLAllocHandle(SQL_HANDLE_ENV...) failed\n");  
      return false;  
   }  
   rc = SQLSetEnvAttr(g_hEnv,SQL_ATTR_ODBC_VERSION, (SQLPOINTER)SQL_OV_ODBC3, SQL_IS_UINTEGER);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLSetEnvAttr failed\n");  
      SQLFreeHandle(SQL_HANDLE_ENV, g_hEnv);  
      return false;  
   }  
   rc = SQLAllocHandle( SQL_HANDLE_DBC, g_hEnv , &g_hDbc);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLAllocHandle(SQL_HANDLE_DBC...) failed\n");  
      SQLFreeHandle(SQL_HANDLE_ENV, g_hEnv);  
      return false;  
   }  
   // Enable BCP  
   rc = SQLSetConnectAttr(g_hDbc, SQL_COPT_SS_BCP, (SQLPOINTER)SQL_BCP_ON, SQL_IS_INTEGER);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLSetConnectAttr(.. SQL_COPT_SS_BCP, (SQLPOINTER)SQL_BCP_ON ...) failed\n");  
      ODBCCleanUp();  
      return false;  
   }  
   // connecting ...  
   rc = SQLDriverConnect(g_hDbc,NULL, (SQLTCHAR*)szConnectionString, SQL_NTS, (SQLTCHAR*)szOutConnectionString, 500, &iLen, SQL_DRIVER_NOPROMPT);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLDriverConnect(SQL_HANDLE_DBC...) failed\n");  
      ODBCCleanUp();  
      return false;  
   }  
   return true;  
}  
  
BOOL BCPSetBulkMode(TCHAR * pszServer, TCHAR * pszQureryOut, char BCPType, TCHAR * pszDataFile) {  
   SQLRETURN rc;  
  
   if (!MakeODBCConnection(pszServer))  
      return false;  
   rc = bcp_init(g_hDbc, NULL, pszDataFile, NULL, DB_OUT);   // bcp init for queryout  
   if (SUCCEED != rc) {  
      printf("bcp_init failed\n");  
      ODBCCleanUp();  
      return false;  
   }  
   // setbulkmode  
   char ColTerm[] = "\t";  
   char RowTerm[] = "\r\n";  
   wchar_t wColTerm[] = L"\t";  
   wchar_t wRowTerm[] = L"\r\n";  
   BYTE * pColTerm = NULL;  
   int cbColTerm = NULL;  
   BYTE * pRowTerm = 0;  
   int cbRowTerm = 0;  
   int bulkmode = -1;  
  
   if (BCPType == 'c') {   // bcp -c  
      pColTerm = (BYTE*)ColTerm;  
      pRowTerm = (BYTE*)RowTerm;  
      cbColTerm = 1;  
      cbRowTerm = 2;  
      bulkmode = BCP_OUT_CHARACTER_MODE;  
   }  
   else  
      if (BCPType == 'w') {   // bcp -w   
         pColTerm = (BYTE*)wColTerm;  
         pRowTerm = (BYTE*)wRowTerm;  
         cbColTerm = 2;  
         cbRowTerm = 4;  
         bulkmode = BCP_OUT_WIDE_CHARACTER_MODE;  
      }  
      else  
         if (BCPType == 'n')   // bcp -n  
            bulkmode = BCP_OUT_NATIVE_MODE;  
         else  
            if (BCPType == 'N')   // bcp -n  
               bulkmode = BCP_OUT_NATIVE_TEXT_MODE;  
            else {  
               printf("unknown bcp mode\n");  
               ODBCCleanUp();  
               return false;  
            }  
            rc = bcp_setbulkmode(g_hDbc, bulkmode, pColTerm, cbColTerm, pRowTerm, cbRowTerm);  
            if (SUCCEED != rc) {  
               printf("bcp_setbulkmode failed\n");  
               ODBCCleanUp();  
               return false;  
            }  
            // set queryout TSQL statement  
            rc = bcp_control(g_hDbc, BCPHINTS , pszQureryOut);  
            if (SUCCEED != rc) {  
               printf("bcp_control(..BCP_OPTION_HINTS..) failed\n");  
               ODBCCleanUp();  
               return false;  
            }  
            // bcp copy  
            DBINT nRowsInserted = 0;  
            rc = bcp_exec(g_hDbc, &nRowsInserted);  
            if (SUCCEED != rc) {  
               printf("bcp_exec failed\n");  
               ODBCCleanUp();  
               return false;  
            }  
            printf("bcp done\n");  
            ODBCCleanUp();  
            return true;  
}  
  
int main() {  
   BCPSetBulkMode(TEXT("localhost"), TEXT("SELECT 'this is a bcp -c test', 1,2") , 'c', TEXT("bcpc.dat"));  
   BCPSetBulkMode(TEXT("localhost"), TEXT("SELECT 'this is a bcp -w test', 1,2") , 'w', TEXT("bcpw.dat"));  
   BCPSetBulkMode(TEXT("localhost"), TEXT("SELECT 'this is a bcp -c test', 1,2") , 'n', TEXT("bcpn.dat"));  
   BCPSetBulkMode(TEXT("localhost"), TEXT("SELECT 'this is a bcp -w test', 1,2") , 'N', TEXT("bcp_N.dat"));  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [大量複製函數](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  