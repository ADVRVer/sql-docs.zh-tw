---
title: TRANSLATE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/01/2019
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- TRANSLATE
- TRANSLATE_TSQL
helpviewer_keywords:
- TRANSLATE function
ms.assetid: 0426fa90-ef6d-4d19-8207-02ee59f74aec
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4f14e6d10f7793fff889dea43841556b9d43d09c
ms.sourcegitcommit: c4870cb5bebf9556cdb4d8b35ffcca265fb07862
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/02/2019
ms.locfileid: "55652557"
---
# <a name="translate-transact-sql"></a>TRANSLATE (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

將第二個引數中指定的部分字元轉譯為第三個變數中指定的一組目的地字元之後，傳回提供作為第一個引數的字串。

## <a name="syntax"></a>語法

```
TRANSLATE ( inputString, characters, translations) 
```

## <a name="arguments"></a>引數   

 *inputString*   
 這是要搜尋的字串[運算式](../../t-sql/language-elements/expressions-transact-sql.md)。 *inputString* 可以是任何字元資料類型 (nvarchar、varchar、nchar、char)。

 *characters*   
 包含應取代之字元的字串[運算式](../../t-sql/language-elements/expressions-transact-sql.md)。 *characters* 可以是任何字元資料類型。

*translations*   
 包含取代字元的字串[運算式](../../t-sql/language-elements/expressions-transact-sql.md)。 *translations* 必須與 *characters* 是一樣的資料類型和長度。

## <a name="return-types"></a>傳回類型

傳回資料類型與 `inputString` 相同的字元運算式，其中第二個引數中的字元會取代為第三個引數中相符的字元。

## <a name="remarks"></a>Remarks   

如果 *characters* 和 *translations* 運算式的長度不同，則 `TRANSLATE` 函數會傳回錯誤。 如果任何引數是 NULL，`TRANSLATE` 會傳回 NULL。  

`TRANSLATE` 函式的行為類似於使用多個 [REPLACE](../../t-sql/functions/replace-transact-sql.md) 函式。 不過，`TRANSLATE` 不會多次取代字元。 這與多個 `REPLACE` 函式不同，因為每次使用時都會取代相關的所有字元。 


`TRANSLATE` 永遠是 SC 定序感知。

## <a name="examples"></a>範例

### <a name="a-replace-square-and-curly-braces-with-regular-braces"></a>A. 將方括號和大括號取代為一般括號

下列查詢會將輸入字串中的方括號和大括號取代為括號：

```sql
SELECT TRANSLATE('2*[3+4]/{7-2}', '[]{}', '()()');
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

```plain_text
2*(3+4)/(7-2)
```

#### <a name="equivalent-calls-to-replace"></a>呼叫 REPLACE 的對等用法

下列的 SELECT 陳述式中，有四個巢狀呼叫 REPLACE 函數的群組。 此群組相當於對上一個 SELECT 中的 TRANSLATE 呼叫一次：

```sql
SELECT
REPLACE
(
      REPLACE
      (
            REPLACE
            (
                  REPLACE
                  (
                        '2*[3+4]/{7-2}',
                        '[',
                        '('
                  ),
                  ']',
                  ')'
            ),
            '{',
            '('
      ),
      '}',
      ')'
);
```

###  <a name="b-convert-geojson-points-into-wkt"></a>B. 將 GeoJSON 點轉換成 WKT

GeoJSON 是一種格式，可針對各種不同的地理資料結構編碼。 開發人員可以利用 `TRANSLATE` 函數，輕鬆地將 GeoJSON 點轉換為 WKT 格式，反之亦然。 下列查詢會將輸入中的方括號和大括號取代為一般括號：

```sql
SELECT TRANSLATE('[137.4, 72.3]' , '[,]', '( )') AS Point,
    TRANSLATE('(137.4 72.3)' , '( )', '[,]') AS Coordinates;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

|點  |座標 |  
|---------|--------- |
|(137.4  72.3) |[137.4,72.3] |

### <a name="c-use-the-translate-function"></a>C. 使用 TRANSLATE 函式

```sql
SELECT TRANSLATE('abcdef','abc','bcd') AS Translated,
       REPLACE(REPLACE(REPLACE('abcdef','a','b'),'b','c'),'c','d') AS Replaced;
```

結果如下：

| 已轉譯 | 已取代 |  
| ---------|--------- |
| bcddef | ddddef |


## <a name="see-also"></a>另請參閱

 [CONCAT &#40;Transact-SQL&#41;](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS &#40;Transact-SQL&#41;](../../t-sql/functions/concat-ws-transact-sql.md)  
 [FORMATMESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME &#40;Transact-SQL&#41;](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE &#40;Transact-SQL&#41;](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE &#40;Transact-SQL&#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE &#40;Transact-SQL&#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF &#40;Transact-SQL&#41;](../../t-sql/functions/stuff-transact-sql.md)  
 [字串函數 (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)