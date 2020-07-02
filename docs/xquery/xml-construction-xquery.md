---
title: XML 結構（XQuery） |Microsoft Docs
description: 瞭解如何使用直接和計算的函數，在 XQuery 中建立 XML 結構。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- white space [XQuery]
- computed constructor
- construct XML structures [XQuery]
- constructors [XQuery]
- prolog
- direct constructor [SQL Server]
- XML [SQL Server], construction
- XQuery, XML construction
ms.assetid: a6330b74-4e52-42a4-91ca-3f440b3223cf
author: rothja
ms.author: jroth
ms.openlocfilehash: 16bffa4040e1a5068f83e9f68da981ed4aa0d7f1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730730"
---
# <a name="xml-construction-xquery"></a>XML 建構 (XQuery)
[!INCLUDE [SQL Server Azure SQL Database ](../includes/applies-to-version/sqlserver.md)]

  在 XQuery 中，您可以使用**直接**和**計算**的函數，在查詢中建立 XML 結構。  
  
> [!NOTE]  
>  **直接**和**計算**的函數之間沒有任何差異。  
  
## <a name="using-direct-constructors"></a>使用直接建構函式  
 當您使用直接建構函式時，可以在建構 XML 時指定與 XML 相似的語法。 下列範例說明以直接建構函式建構 XML 。  
  
### <a name="constructing-elements"></a>建構元素  
 在使用 XML 註解時，您可以建構元素。 下列範例會使用直接元素的「函式」運算式，並建立 \<ProductModel> 元素。 此建構元素具有三個子元素  
  
-   文字節點。  
  
-   兩個元素節點： \<Summary> 和 \<Features> 。  
  
    -   \<Summary>元素具有一個文位元組點子系，其值為「部分描述」。  
  
    -   \<Features>元素具有三個元素節點子系：、 \<Color> \<Weight> 和 \<Warranty> 。 這些節點的每一個都有一個文字子節點，而且分別有 Red、25、2 years parts and labor 的值。  
  
```sql
declare @x xml;  
set @x='';  
select @x.query('<ProductModel ProductModelID="111">;  
This is product model catalog description.  
<Summary>Some description</Summary>  
<Features>  
  <Color>Red</Color>  
  <Weight>25</Weight>  
  <Warranty>2 years parts and labor</Warranty>  
</Features></ProductModel>')  
  
```  
  
 以下是產生的 XML：  
  
```xml
<ProductModel ProductModelID="111">  
  This is product model catalog description.  
  <Summary>Some description</Summary>  
  <Features>  
    <Color>Red</Color>  
    <Weight>25</Weight>  
    <Warranty>2 years parts and labor</Warranty>  
  </Features>  
</ProductModel>  
```  
  
 雖然從常數運算式建構元素 (如本範例所示) 非常有用，不過此 XQuery 語言真正強大的功能在於能夠從資料庫動態擷取資料來建構 XML。 您可以使用大括號指定查詢運算式。 在產生的 XML 中，其值將會取代運算式。 例如，下列查詢會 `NewRoot` 以一個子項目（<>）來建立 <> 專案 `e` 。 元素 <> 的值 `e` 是藉由在大括弧（"{...}"）內指定路徑運算式來計算。  
  
```sql
DECLARE @x xml;  
SET @x='<root>5</root>';  
SELECT @x.query('<NewRoot><e> { /root } </e></NewRoot>');  
```  
  
 括號是做為內容切換 Token 並將查詢從 XML 建構切換到查詢評估。 在此例中，已評估在括號中的 XQuery 路徑運算式 `/root`，且其結果將會取代它。  
  
 以下是結果：  
  
```xml
<NewRoot>  
  <e>  
    <root>5</root>  
  </e>  
</NewRoot>  
```  
  
 下列查詢與上一個查詢相似。 不過，大括弧中的運算式會指定**data （）** 函式來抓取 <> 元素的不可部分完成值， `root` 並將它指派給已 <> 的結構化專案 `e` 。  
  
```sql
DECLARE @x xml;  
SET @x='<root>5</root>';  
DECLARE @y xml;  
SET @y = (SELECT @x.query('  
                           <NewRoot>  
                             <e> { data(/root) } </e>  
                           </NewRoot>' ));  
SELECT @y;  
```  
  
 以下是結果：  
  
```xml
<NewRoot>  
  <e>5</e>  
</NewRoot>  
```  
  
 如果您想要使用大括號做為文字而不是內容切換 Token 的一部份，只要使用 "}}" 或 "{{" 就可以跳過它們，如本範例所示：  
  
```sql
DECLARE @x xml;  
SET @x='<root>5</root>';  
DECLARE @y xml;  
SET @y = (SELECT @x.query('  
<NewRoot> Hello, I can use {{ and  }} as part of my text</NewRoot>'));  
SELECT @y;  
```  
  
 以下是結果：  
  
```xml
<NewRoot> Hello, I can use { and  } as part of my text</NewRoot>  
```  
  
 下列查詢是使用直接元素建構函式來建構元素的另一個範例。 此外，也 `FirstLocation` 會藉由在大括弧中執行運算式來取得 <> 元素的值。 查詢運算式會在第一個工作中心位置從 Production.ProductModel 資料表的 Instructions 資料行傳回製造步驟。  
  
```sql
SELECT Instructions.query('  
    declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
        <FirstLocation>  
           { /AWMI:root/AWMI:Location[1]/AWMI:step }  
        </FirstLocation>   
') as Result   
FROM Production.ProductModel  
WHERE ProductModelID=7;  
```  
  
 以下是結果：  
  
```xml
<FirstLocation>  
  <AWMI:step xmlns:AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions">  
      Insert <AWMI:material>aluminum sheet MS-2341</AWMI:material> into the <AWMI:tool>T-85A framing tool</AWMI:tool>.   
  </AWMI:step>  
  <AWMI:step xmlns:AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions">  
      Attach <AWMI:tool>Trim Jig TJ-26</AWMI:tool> to the upper and lower right corners of the aluminum sheet.   
  </AWMI:step>  
   ...  
</FirstLocation>  
```  
  
#### <a name="element-content-in-xml-construction"></a>在 XML 建構中的元素內容  
 下列範例使用直接元素建構函式，說明運算式建構元素內容的行為。 在下列範例中，直接元素建構函式指定了一個運算式。 為了此運算式，在產生的 XML 中建立了一個文字節點。  
  
```sql
declare @x xml;  
set @x='  
<root>  
  <step>This is step 1</step>  
  <step>This is step 2</step>  
  <step>This is step 3</step>  
</root>';  
select @x.query('  
<result>  
 { for $i in /root[1]/step  
    return string($i)  
 }  
</result>');  
  
```  
  
 從運算式評估所產生的不可部份完成值順序將會加入文字節點，並在相鄰的不可部份完成值之間加入空格，如下列結果所示。 建構元素具有一個子元素。 這是包含值的文字節點，如下列結果所示。  
  
```xml
<result>This is step 1 This is step 2 This is step 3</result>  
```  
  
 如果您不指定一個運算式而是指定三個獨立的運算式以產生三個文字節點，相鄰的節點會在產生的 XML 中依串連合併成單一文字節點。  
  
```sql
declare @x xml;  
set @x='  
<root>  
  <step>This is step 1</step>  
  <step>This is step 2</step>  
  <step>This is step 3</step>  
</root>';  
select @x.query('  
<result>  
 { string(/root[1]/step[1]) }  
 { string(/root[1]/step[2]) }  
 { string(/root[1]/step[3]) }  
</result>');  
```  
  
 建構元素節點具有一個子元素。 這是包含值的文字節點，如下列結果所示。  
  
```xml
<result>This is step 1This is step 2This is step 3</result>  
```  
  
### <a name="constructing-attributes"></a>建構屬性  
 當您使用直接元素建構函式建構元素時，您也可以使用與 XML 相似的語法來指定元素的屬性，如下列範例所示：  
  
```sql
declare @x xml;  
set @x='';  
select @x.query('<ProductModel ProductModelID="111">;  
This is product model catalog description.  
<Summary>Some description</Summary>  
</ProductModel>')  
```  
  
 以下是產生的 XML：  
  
```xml
<ProductModel ProductModelID="111">  
  This is product model catalog description.  
  <Summary>Some description</Summary>  
</ProductModel>  
```  
  
 <> 的結構化元素 `ProductModel` 具有 ProductModelID 屬性和下列子節點：  
  
-   文字節點 `This is product model catalog description.`  
  
-   元素節點，<`Summary`>。 此節點擁有一個文字子節點 `Some description`。  
  
 當您建構屬性時，您可以在大括號中指定值與運算式。 在此情況下，將以屬性值傳回運算式的結果。  
  
 在下列範例中，不會嚴格要求**data （）** 函數。 因為您要將運算式值指派給屬性，所以會隱含地套用**data （）** ，以取得所指定運算式的具類型值。  
  
```sql
DECLARE @x xml;  
SET @x='<root>5</root>';  
DECLARE @y xml;  
SET @y = (SELECT @x.query('<NewRoot attr="{ data(/root) }" ></NewRoot>'));  
SELECT @y;  
```  
  
 以下是結果：  
  
```xml
<NewRoot attr="5" />  
```  
  
 以下是另一個範例，它為 LocationID 與 SetupHrs 屬性建構指定運算式。 這些運算式會針對 Instruction 資料行中的 XML 來評估運算式。 運算式中具類型的值會指派給屬性。  
  
```sql
SELECT Instructions.query('  
    declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
        <FirstLocation   
         LocationID="{ (/AWMI:root/AWMI:Location[1]/@LocationID)[1] }"  
         SetupHrs = "{ (/AWMI:root/AWMI:Location[1]/@SetupHours)[1] }" >  
           { /AWMI:root/AWMI:Location[1]/AWMI:step }  
        </FirstLocation>   
') as Result   
FROM  Production.ProductModel  
where ProductModelID=7;  
```  
  
 以下是部份結果：  
  
```xml
<FirstLocation LocationID="10" SetupHours="0.5" >  
  <AWMI:step ...   
  </AWMI:step>  
  ...  
</FirstLocation>  
```  
  
#### <a name="implementation-limitations"></a>實作限制  
 以下為其限制：  
  
-   不支援多個或混合的 (字串與 XQuery 運算式) 屬性運算式。 例如，如下列查詢所示，您可以建構 XML，其中 `Item` 是常數，而值 `5` 是由評估查詢運算式所取得：  
  
    ```xml
    <a attr="Item 5" />  
    ```  
  
     下列查詢會傳回錯誤，因為您將常數字串與運算式 ({/x}) 混用，這是不支援的：  
  
    ```sql
    DECLARE @x xml  
    SET @x ='<x>5</x>'  
    SELECT @x.query( '<a attr="Item {/x}"/>' )   
    ```  
  
     在這種情形下，您有下列選擇：  
  
    -   依兩個不可部份完成值的串連組成屬性值。 這些不可部份完成值將序列化成屬性值，並在兩個不可部份完成值之間加上空格：  
  
        ```sql
        SELECT @x.query( '<a attr="{''Item'', data(/x)}"/>' )   
        ```  
  
         以下是結果：  
  
        ```xml
        <a attr="Item 5" />  
        ```  
  
    -   使用[concat](../xquery/functions-on-string-values-concat.md)函式，將兩個字串引數串連成產生的屬性值：  
  
        ```sql
        SELECT @x.query( '<a attr="{concat(''Item'', /x[1])}"/>' )   
        ```  
  
         在此情況下，不會在兩個字串值之間加入空格。 如果您希望兩個值之間有空格，您必須明確地提供它。  
  
         以下是結果：  
  
        ```xml
        <a attr="Item5" />  
        ```  
  
-   不支援做為屬性值的多個運算式。 例如，下列查詢會傳回錯誤：  
  
    ```sql
    DECLARE @x xml  
    SET @x ='<x>5</x>'  
    SELECT @x.query( '<a attr="{/x}{/x}"/>' )  
    ```  
  
-   不支援異質性時序。 嘗試指派異質性時序做為屬性值將會傳回錯誤，如下列範例所示。 在此範例中，會將異類序列、字串 "Item" 和元素 <`x`> 指定為屬性值：  
  
    ```sql
    DECLARE @x xml  
    SET @x ='<x>5</x>'  
    select @x.query( '<a attr="{''Item'', /x }" />')  
    ```  
  
     如果您套用**data （）** 函數，則查詢會運作，因為它會抓取運算式的不可部分完成值，而該運算式 `/x` 會與字串串連。 下列是不可部份完成值的時序：  
  
    ```sql
    SELECT @x.query( '<a attr="{''Item'', data(/x)}"/>' )   
    ```  
  
     以下是結果：  
  
    ```xml
    <a attr="Item 5" />  
    ```  
  
-   屬性節點順序會在序列化期間強制執行，而非靜態類型檢查期間。 例如，由於下列查詢嘗試將節點加入非屬性節點後面，因此查詢將會失敗。  
  
    ```sql
    select convert(xml, '').query('  
    element x { attribute att { "pass" }, element y { "Element text" }, attribute att2 { "fail" } }  
    ')  
    go  
    ```  
  
     上述查詢傳回的錯誤如下：  
  
    ```  
    XML well-formedness check: Attribute cannot appear outside of element declaration. Rewrite your XQuery so it returns well-formed XML.  
    ```  
  
### <a name="adding-namespaces"></a>加入命名空間  
 使用直接建構函式來建構 XML 時，可以使用命名空間前置詞來限定建構元素與屬性名稱。 您可以利用下列方式來繫結命名空間的前置詞：  
  
-   使用命名空間宣告屬性。  
  
-   使用 WITH XMLNAMESPACES 子句。  
  
-   在 XQuery 初構中。  
  
#### <a name="using-a-namespace-declaration-attribute-to-add-namespaces"></a>使用命名空間宣告屬性加入命名空間  
 下列範例會在元素 <> 中使用命名空間宣告屬性 `a` ，以宣告預設命名空間。 <的子項目結構> 會 `b` 復原在父元素中宣告之預設命名空間的宣告。  
  
```sql
declare @x xml  
set @x ='<x>5</x>'  
select @x.query( '  
  <a xmlns="a">  
    <b xmlns=""/>  
  </a>' )   
```  
  
 以下是結果：  
  
```xml
<a xmlns="a">  
  <b xmlns="" />  
</a>  
```  
  
 您可以指派前置詞給命名空間。 前置詞是在 <> 元素的結構中指定 `a` 。  
  
```sql
declare @x xml  
set @x ='<x>5</x>'  
select @x.query( '  
  <x:a xmlns:x="a">  
    <b/>  
  </x:a>' )  
```  
  
 以下是結果：  
  
```xml
<x:a xmlns:x="a">  
  <b />  
</x:a>  
```  
  
 您可以取消宣告 XML 建構中的預設命名空間，但是您無法取消宣告命名空間的前置詞。 下列查詢會傳回錯誤，因為您無法取消宣告元素 <> 中所指定的前置詞 `b` 。  
  
```sql
declare @x xml  
set @x ='<x>5</x>'  
select @x.query( '  
  <x:a xmlns:x="a">  
    <b xmlns:x=""/>  
  </x:a>' )  
```  
  
 新建構的命名空間可在查詢中使用。 例如，下列查詢會在建立專案時宣告命名空間，<`FirstLocation`>，並在 LocationID 和 SetupHrs 屬性值的運算式中指定前置詞。  
  
```sql
SELECT Instructions.query('  
        <FirstLocation xmlns:AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
         LocationID="{ (/AWMI:root/AWMI:Location[1]/@LocationID)[1] }"  
         SetupHrs = "{ (/AWMI:root/AWMI:Location[1]/@SetupHours)[1] }" >  
           { /AWMI:root/AWMI:Location[1]/AWMI:step }  
        </FirstLocation>   
') as Result   
FROM  Production.ProductModel  
where ProductModelID=7  
```  
  
 請注意以此方式建立的新命名空間前置詞，將會覆寫此前置詞的任何已存在的命名空間宣告。 例如，在查詢初構中的命名空間宣告， `AWMI="https://someURI"` 會由 <> 專案中的命名空間宣告所覆寫 `FirstLocation` 。  
  
```sql
SELECT Instructions.query('  
declare namespace AWMI="https://someURI";  
        <FirstLocation xmlns:AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
         LocationID="{ (/AWMI:root/AWMI:Location[1]/@LocationID)[1] }"  
         SetupHrs = "{ (/AWMI:root/AWMI:Location[1]/@SetupHours)[1] }" >  
           { /AWMI:root/AWMI:Location[1]/AWMI:step }  
        </FirstLocation>   
') as Result   
FROM  Production.ProductModel  
where ProductModelID=7  
```  
  
#### <a name="using-a-prolog-to-add-namespaces"></a>使用初構加入命名空間  
 此範例說明命名空間如何加入已建構的 XML。 在查詢初構中會宣告預設的命名空間。  
  
```sql
declare @x xml  
set @x ='<x>5</x>'  
select @x.query( '  
           declare default element namespace "a";  
            <a><b xmlns=""/></a>' )  
```  
  
 請注意，在專案 <> 的結構中 `b` ，命名空間宣告屬性是以空字串做為其值所指定。 這將會取消宣告在父元素中所宣告的預設命名空間。  
  

以下是結果：  

```xml
<a xmlns="a">  
  <b xmlns="" />  
</a>  
```  
  
### <a name="xml-construction-and-white-space-handling"></a>XML 建構與空白處理  
 在 XML 建構中的元素內容可以包含空白字元。 這些字元是以下列方式處理：  
  
-   命名空間 Uri 中的空白字元會被視為 XSD 型別**anyURI**。 具體而言，以下是處理它們的方式：  
  
    -   任何在開頭和結尾的空白字元都會被刪減。  
  
    -   內部空白字元值會摺疊成單一空格。  
  
-   在屬性內容中的換行字元將以空格取代。 所有其他的空白字元仍然會維持不變。  
  
-   元素內的空白將予以保留。  
  
 下列範例說明在 XML 建構中空白的處理：  
  
```sql
-- line feed is repaced by space.  
declare @x xml  
set @x=''  
select @x.query('  
  
declare namespace myNS="   https://       
 abc/  
xyz  
  
";  
<test attr="    my   
test   attr   
value    " >  
  
<a>  
  
This     is  a  
  
test  
  
</a>  
</test>  
') as XML_Result  
  
```  
  
 以下是結果：  
  
```xml
-- result  
<test attr="<test attr="    my test   attr  value    "><a>  
  
This     is  a  
  
test  
  
</a></test>  
"><a>  
  
This     is  a  
  
test  
  
</a></test>  
```  
  
### <a name="other-direct-xml-constructors"></a>其他直接 XML 建構函式  
 處理指示和 XML 註解的建構函式使用與對應 XML 建構語法相同的語法。 也支援文字節點的計算建構函式，但主要用於 XML DML 以建構文字節點。  
  
 **注意**如需使用明確文位元組點的範例，請參閱[insert &#40;XML DML&#41;](../t-sql/xml/insert-xml-dml.md)中的特定範例。  
  
 在下列查詢中，已建構的 XML 包含一個元素、兩個屬性、註解以及處理指示。 請注意，<> 之前會使用逗號 `FirstLocation` ，因為正在建立序列。  
  
```sql
SELECT Instructions.query('  
  declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
   <?myProcessingInstr abc="value" ?>,   
   <FirstLocation   
        WorkCtrID = "{ (/AWMI:root/AWMI:Location[1]/@LocationID)[1] }"  
        SetupHrs = "{ (/AWMI:root/AWMI:Location[1]/@SetupHours)[1] }" >  
       <!-- some comment -->  
       <?myPI some processing instructions ?>  
       { (/AWMI:root/AWMI:Location[1]/AWMI:step) }  
    </FirstLocation>   
') as Result   
FROM Production.ProductModel  
where ProductModelID=7;  
  
```  
  
 以下是部份結果：  
  
```xml
<?myProcessingInstr abc="value" ?>  
<FirstLocation WorkCtrID="10" SetupHrs="0.5">  
  <!-- some comment -->  
  <?myPI some processing instructions ?>  
  <AWMI:step xmlns:AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions">I  
  nsert <AWMI:material>aluminum sheet MS-2341</AWMI:material> into the <AWMI:tool>T-85A framing tool</AWMI:tool>.   
  </AWMI:step>  
    ...  
</FirstLocation>  
  
```  
  
## <a name="using-computed-constructors"></a>使用計算建構函式  
 . 在此情況下，您可以指定關鍵字，以識別您要建構的節點類型。 只支援下列關鍵字：  
  
-   element  
  
-   屬性  
  
-   text  
  
 對於元素和屬性節點而言，這些關鍵字後面接著括在括號中的節點名稱及運算式，它們將會產生該節點的內容。 在以下範例中，您正在建構此 XML：  
  
```xml
<root>  
  <ProductModel PID="5">Some text <summary>Some Summary</summary></ProductModel>  
</root>  
```  
  
 以下查詢是使用計算建構函式產生 XML：  
  
```sql
declare @x xml  
set @x=''  
select @x.query('element root   
               {   
                  element ProductModel  
     {  
attribute PID { 5 },  
text{"Some text "},  
    element summary { "Some Summary" }  
 }  
               } ')  
  
```  
  
 產生節點內容的運算式可以指定查詢運算式。  
  
```sql
declare @x xml  
set @x='<a attr="5"><b>some summary</b></a>'  
select @x.query('element root   
               {   
                  element ProductModel  
     {  
attribute PID { /a/@attr },  
text{"Some text "},  
    element summary { /a/b }  
 }  
               } ')  
```  
  
 請注意計算元素與屬性建構函式 (如 XQuery 規格所定義) 允許您計算節點名稱。 當您使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中的直接建構函式時，節點名稱 (例如元素與屬性) 必須以常值指定。 因此，元素和屬性的直接建構函式與計算建構函式之間並沒有差異。  
  
 在下列範例中，會從 ProductModel 資料表中**xml**資料類型的指示資料行中所儲存的 xml 製造指示，取得所結構化節點的內容。  
  
```sql
SELECT Instructions.query('  
  declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
   element FirstLocation   
     {  
        attribute LocationID { (/AWMI:root/AWMI:Location[1]/@LocationID)[1] },  
        element   AllTheSteps { /AWMI:root/AWMI:Location[1]/AWMI:step }  
     }  
') as Result   
FROM  Production.ProductModel  
where ProductModelID=7  
```  
  
 以下是部份結果：  
  
```xml
<FirstLocation LocationID="10">  
  <AllTheSteps>  
    <AWMI:step> ... </AWMI:step>  
    <AWMI:step> ... </AWMI:step>  
    ...  
  </AllTheSteps>  
</FirstLocation>    
```  
  
## <a name="additional-implementation-limitations"></a>其他的實作限制  
 計算屬性建構函式無法用以宣告新命名空間。 另外，下列計算建構函式不支援 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]：  
  
-   計算文件節點建構函式  
  
-   計算處理指示建構函式  
  
-   計算註解建構函式  
  
## <a name="see-also"></a>另請參閱  
 [XQuery 運算式](../xquery/xquery-expressions.md)  
  
  
