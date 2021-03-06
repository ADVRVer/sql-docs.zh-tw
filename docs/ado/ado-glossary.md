---
description: ADO 詞彙
title: ADO 詞彙 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, glossary
ms.assetid: b0478836-4123-4357-969a-c5784fc28be5
author: rothja
ms.author: jroth
ms.openlocfilehash: dd781612557faebd4b6eefb710ffad2379928aee
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2020
ms.locfileid: "88980849"
---
# <a name="ado-glossary-terms"></a>ADO 詞彙
本主題定義與 ADO 相關的詞彙。

## <a name="a"></a>A
 絕對 URL：指定位於網際網路或內部網路之資源位置的完整 URL。 另請參閱 *url* 和 *相對 url*。

 ActiveX 控制項自我註冊、同進程 COM 元件，在設計階段或執行時間，通常會有視覺元素。 ActiveX 控制項也能夠與使用中的檔容器（例如 Microsoft Internet Explorer）進行通訊。

 ADISAPI (Advanced Data Internet Server 應用程式開發介面) ISAPI DLL，以提供剖析、自動化控制、記錄集封送處理和 MIME 封裝。 ADISAPI 元件會透過 Internet Information Services (IIS) 所提供的 API 來運作。 另請參閱 *ISAPI*。

 查詢中的彙總函式、COUNT、AVG 或 STDEV 這類函數會使用資料表資料行中的所有資料列來計算值。 在撰寫運算式和程式設計中，您可以使用 SQL 彙總函式 (包括以上所列的三個) 和網域彙總函式來判斷各種統計資料。

 別名：您在 SQL SELECT 語句中提供給資料行或運算式的替代名稱，通常較短或更有意義。 例如，BobSales 是下列 SELECT 語句中的別名： "Select wr-Sales as BobSales from SalesDB"。 別名可以用來以動態方式指派資料行，以控制 DataControl 物件的系結。

 單元執行緒化 COM 執行緒模型，其中物件的所有呼叫都會在一個執行緒上發生。 在單元執行緒中，COM 會同步處理並封送處理呼叫。 另請參閱 *COMmddefcom*。

 非同步作業會將控制權傳回呼叫的程式，而不會等待作業完成。 作業完成之前，會繼續執行程式碼。 另請參閱 *同步操作*。

## <a name="b"></a>B
 系結專案：資料表中的欄位與變數之間的對應。 在 ADO Visual C++ 擴充功能中， **記錄集** 欄位會對應至 c/c + + 變數。

 位元遮罩是一個數值，用於比對其他數值的比對值，通常是用來旗標參數或傳回值中的選項。 這項比較通常是使用位邏輯運算子來完成，例如 **和** 和 **或** 在 Visual Basic 中， **&** 以及在 c + + 中 **&#124;** 。

 例如，ADO **FieldAttributeEnum** 值可以用來做為位元遮罩，以決定欄位的屬性。 假設您想要判斷欄位是否可更新。 您可以使用下列運算式在 Visual Basic 中進行測試：`Field.Attributes AND adFldUpdatable`

 如果結果為 TRUE，則欄位是可更新的。

 將標記設定為書簽，以在一組資料列中唯一識別資料列，讓使用者可以快速流覽至該標記。

 商務物件：執行一組已定義的作業，例如資料驗證或商務規則邏輯的物件。 商務物件通常位於仲介層。

 商務規則：驗證編輯、登入驗證、資料庫查閱、原則和演算法轉換的組合，這些都是構成企業商務運作方式的組合。 也稱為 *商務邏輯*。

## <a name="c"></a>C
 計算運算式：不是常數的運算式，但其值相依于其他值。 計算運算式必須從其他來源（通常是在其他欄位或資料列）取得和計算值，才能進行評估。

 章節的參考資料源中的資料列範圍。 在 ADO 中，章節通常是另一個 **記錄集**的參考。

 章節資料行可讓您定義 *父子式* 關聯性，其中 *父系* 是包含章節資料行的 **記錄集** ，而 *子* 系是該章節所代表的 **記錄集** 。

 章節-別名，此別名會參考附加至父系的資料行。

 字元集：將一組字元對應至其數值。 例如，Unicode 是16位的字元集，可將所有已知字元編碼，並作為全球字元編碼標準。

 子系：階層式關聯性的相依端。 子系是階層結構中的節點，其上方有另一個節點， (更接近根) 。 另請參閱 *子別名*、 *父子式關聯*性、 *父系*。

 子別名指的是指向子系的別名。 另請參閱 *別名*、 *子*系。

 CLSID (類別識別碼) 識別 COM 元件 (UUID) 的通用唯一識別碼。 每個 COM 元件在 Windows 登錄中都有其 CLSID，讓其他應用程式可以載入它。 另請參閱 *ProgID*、 *COM*。

 用戶端層是分散式系統的邏輯層，通常會向使用者呈現資料並處理輸入，有時也稱為 *前端*。 通常，用戶端層會根據輸入要求來自伺服器的資料，然後格式化並顯示結果。 另請參閱 *中介層*、 *資料來源層*、 *分散式應用程式*。

 COM (元件物件模型) 二進位標準，可讓物件在網路環境中相交互操作，而不論其開發的語言或其所在的電腦。 以 COM 為基礎的技術包括 ActiveX 控制項、自動化，以及物件連結與內嵌 (OLE) 。 COM 可讓物件向其他元件公開其功能，以及裝載應用程式。 它會定義物件本身的公開方式，以及此風險在跨進程和跨網路之間的運作方式。 COM 也會定義物件的生命週期。

 COM 元件二進位檔案（例如 .dll、.ocx 和一些 .exe 檔案）支援提供物件的 COM 標準。 這類檔案包含一或多個 class factory、COM 類別、登錄輸入機制、載入程式碼等的程式碼。

 比較運算子：比較兩個運算式並傳回布林值的運算子。

 可表示為 ">" 的準則參數 (大於) 、" \<" (less than), "=" (equal), "> =" (大於或等於) 、"<=" (小於或等於) 、"<>" (不等於) 或 "like" (模式比對) 。

 元件封裝資料和程式碼的物件，並提供一組指定的公開可用服務。

 複合檔案是檔案的 COM 結構化儲存區的實作為。 複合檔案會將不同的物件儲存在由兩個主要元素組成的單一結構化檔案中：儲存物件和資料流程物件。 它們會一起運作，如同檔案內的檔案系統。

 在一個實體檔案中系結在一起的多個個別檔案。 複合檔案中的每個個別檔案都可以像單一實體檔案一樣存取。

 常數：不會變更的數值或字串值。 命名的 ADO 列舉 (列舉常數) 可以在您的程式碼中使用，而不是實際值，例如， **adUseClient** 是其值為3的常數。  (Const adUseClient = 3) 。 另請參閱 *列舉*。

 資料指標是控制記錄導覽、資料可更新性的資料庫專案，以及其他使用者對資料庫所做之變更的可見度。

## <a name="d"></a>D
 資料系結將應用程式的物件或控制項與資料來源建立關聯的進程。 與資料來源建立關聯的控制項稱為 *資料繫結控制項*。

 資料繫結控制項的內容會與資料庫中的值相關聯。 例如，當**記錄集**內的資料列更新時，系結至**記錄集**物件的方格控制項可以更新。 當 **記錄集**抓取新值時，新值會顯示在方格中。

 直接或透過服務提供者公開資料給 ADO 應用程式的資料提供者軟體。 另請參閱服務提供者。

 資料成形的技術會利用正規化的語法 (稱為**圖形語言**) 來定義特製化的**記錄**集物件 (稱為圖形*記錄集*) ，其中不只包含資料，還會根據**其他記錄集物件參考**其他**記錄**集物件和/或計算值。

 資料來源層是分散式系統的邏輯層，代表執行 DBMS 的電腦，例如 SQL Server 資料庫。 另請參閱 *用戶端層*、仲介 *層*、 *分散式應用程式*。

 DCOM A 線路通訊協定，可讓 COM 元件在網路上直接彼此通訊。 另請參閱 *COM*、 *元件*。

 DDL (資料定義語言) SQL 中定義，而不是運算元據的語句。 使用 DDL 建立或修改資料庫的架構。 例如， **CREATE TABLE**、 **CREATE INDEX**、 **GRANT**和 **REVOKE** 都是 SQL DDL 語句。

 預設資料流程：當使用特定 OLE DB 提供者（例如 Microsoft OLE DB Provider for Internet 發行）時，與**記錄**或**記錄集**物件相關聯的**資料流程**物件)  (表示的文字或二進位資料流程。 預設資料流程通常會包含檔案的內容，例如，網站根目錄的 HTML 程式碼。

 分散式應用程式是一種撰寫的程式，可透過網路將處理分割成多部電腦。 通常，分散式應用程式會分成展示、商務邏輯和資料存放區層，或是 *分層*。 另請參閱用戶端層、仲介層、資料來源層。

 已中斷連接的記錄集：用戶端快取中的 **記錄集** 物件不再具有伺服器的即時連線。 如果因為某些原因而需要重新存取原始資料來源（例如更新資料），則必須重新建立連接。 不過，仍然可以存取已中斷連線 **記錄集** 的集合、屬性和方法。

 DML (資料操作語言) SQL 中操作的語句，而不是定義資料。 系統會選取資料庫中的值，並使用 DML 來修改這些值。 例如， **INSERT**、 **UPDATE**、 **DELETE**和 **SELECT** 都是 SQL DML 語句。

 檔來源提供者是一種特殊的提供者類別，可管理資料夾和檔。 當檔以 **Record** 物件表示，或檔的資料夾由 **記錄集** 物件表示時，檔來源提供者會使用一組唯一的欄位來填入這些物件，以描述檔的特性，而不是實際檔本身。 另請參閱資源記錄。

 DSN (資料來源名稱) 用來將應用程式連接到特定 ODBC 資料庫的資訊集合。 ODBC 驅動程式管理員會使用此資訊來建立與資料庫的連接。 DSN 可以儲存在檔案中 (檔案 DSN) 或在 Windows 登錄中， (機器 DSN) 。

 動態屬性：資料提供者或資料指標服務特有的屬性。 物件的 **Properties** 集合會自動以「動態」 ( 「動態」 ) 來填入。 物件在透過特定的資料提供者連接到資料來源之前，沒有動態屬性。 另請參閱資料提供者、資料指標。

## <a name="e"></a>E
 列舉已命名常數的清單。 列舉值不需要是唯一的。 不過，每個值的名稱在定義列舉的範圍內都必須是唯一的。 在 ADO 中，列舉可用於數值參數和傳回值，以將意義新增至 ADO 程式碼，並讓開發人員不受數值的 (，這些值可能會從版本變更為版本) 。 例如，若要開啟靜態 **記錄集**，請使用 **adOpenStatic** 列舉值： `Recordset.Open ,,adOpenStatic`

 也稱為 *列舉常數*。 另請參閱 *常數*。

 事件：物件可辨識的動作，您可以為其撰寫程式碼以回應。 事件可以由命令執行、交易完成、記錄集流覽和資料更新產生，還有其他動作。 另請參閱 *事件處理常式*。

 事件處理常式：事件處理常式是事件發生時所執行的程式碼。 另請參閱事件。

## <a name="h"></a>H
 處理常式，此常式會管理常見且相當簡單的條件或作業，例如錯誤復原或資料管理。

 階層式記錄集：包含另一個**記錄集**的**記錄**集。 另請參閱資料成形（章節）。

 如需詳細資訊，請參閱 [存取階層式記錄集中](./guide/data/accessing-rows-in-a-hierarchical-recordset.md)的資料列。

 階層一般而言，階層是具有最上層層級和從屬層級的排名結構。 在 ADO 中，階層式 **記錄集** 是用來代表記錄與章節之間的父子式關聯性。 此外，在 ADO 中， **記錄** 和 **資料流程** 物件也可以用來存取階層式樹狀結構，例如資料夾和檔。 ADO MD **也包含階層** 物件，以表示 OLAP cube 中維度層級之間的關聯性。 另請參閱階層式記錄集、父子式關聯性、章節、樹狀結構。

## <a name="i-l"></a>I-L
 ISAPI (網際網路伺服器應用程式開發介面) 一組適用于網際網路伺服器的函式，例如執行 &reg; Microsoft &reg; INTERNET INFORMATION SERVICES (IIS) 的 Windows NT Server/Windows 2000 伺服器。

 索引鍵資料行或資料表中唯一識別資料列的資料行;通常用來編制資料表的索引。

## <a name="m"></a>M
 封送處理跨執行緒或進程界限的封裝、傳送和解除封裝介面方法參數的程式。

 在分散式系統中，使用者介面或 Web 用戶端與資料庫之間的邏輯層的中介層。 這通常是商務物件具現化的位置。 仲介層是商務規則和函式的集合，可在接收資訊時產生和操作。 他們透過商務規則達成此目的，而這些規則可能會經常變更，因此封裝至與應用程式邏輯本身實體分開的元件中。 也稱為 *應用程式伺服器層*。 另請參閱分散式應用程式、用戶端層、資料來源層。

 MIME (多用途網際網路郵件延伸模組) 原本開發的網際網路通訊協定，可讓您在不同的網路、電腦和電子郵件環境之間，以豐富的內容交換電子郵件訊息。 在實務上，MIME 也是由非郵件應用程式採用和延伸。

 MIME 是一種標準，可讓您在網際網路上發佈和讀取二進位資料。 具有二進位資料之檔案的標頭包含資料的 MIME 類型。這會通知用戶端程式 (的網頁瀏覽器和郵件封裝，例如) 它們需要以與處理直接文字不同的方式來處理資料。 例如，包含 JPEG 圖形之 Web 檔的標頭包含 JPEG 檔案格式的特定 MIME 類型。 這可讓瀏覽器以其 JPEG 檢視器顯示檔案（如果有的話）。

## <a name="n-o"></a>N-O
 節點：階層式樹狀結構中的元素。 節點可以是根或另一個節點的子系。 節點也可以是多個子系的父系。 另請參閱階層、樹狀結構、根、子系、父系。

 物件變數：包含物件參考的變數。 例如， `objCustomObject` 是指向 CustomObject 型別物件的變數：`Set objCustomObject = CreateObject(adodb.Recordset)`

 ODBC (開放式資料庫連接) 標準的程式設計語言介面，用來連接到各種資料來源。 這通常是透過主控台來存取，也就是可以指派資料來源名稱 (Dsn) ，以使用特定的 ODBC 驅動程式。

 OLE DB 一組介面，這些介面會使用 COM 公開各種來源的資料。 OLE DB 介面會提供應用程式，以統一存取儲存在多樣化資訊來源中的資料。 這些介面支援適用于資料來源的 DBMS 功能數量，可讓它共用其資料。 另請參閱 COM。

 開放式鎖定一種鎖定類型，其中包含一或多筆記錄的資料頁（包括正在編輯的記錄）只有在 **更新** 方法更新記錄時才可供其他使用者使用，但在呼叫 **更新**之前和之後皆可使用。

 當使用**LockType**參數或屬性設定為**adLockOptimistic**或**adLockBatchOptimistic**來開啟**記錄集**物件時，會使用開放式鎖定。 另請參閱封閉式鎖定。

 順序值：專案在訂單內的數位位置。 在 ADO 集合中，第一個專案的序數值為零 (0) 。 下一個專案是 (1) 等等。

## <a name="p"></a>P
 參數化命令：可讓您在執行命令之前設定參數值的查詢或命令。 例如，您可以在 SQL 字串中內嵌參數標記（ (由 '？ ' 字元) 指定）來將 SQL 字串參數化。 然後，應用程式會指定每個參數的值，然後執行命令。

 父項：階層式關聯性的控制端。 在階層式結構中，父系在階層中的下有一個或多個子節點。 另請參閱父-別名、父子式關聯性、子系。

 父別名：參考父系的別名。 另請參閱別名、父系。

 父子式關聯性：階層式結構中的關聯性，其中父系層級是較高的層級，而且直接與一個或多個子系相關聯。 子系較低層級，而且必須有一個父系。 另請參閱父系、子系。

 封閉式鎖定鎖定類型，其中包含一或多筆記錄的頁面（包括正在編輯的記錄）無法供其他使用者使用，以確保會進行更新。 封閉式鎖定行為是由 OLE DB 提供者所定義。 一般來說，在 **更新** 方法完成之前，記錄會在編輯時鎖定，並保持無法使用。

 當 **記錄集** 物件開啟時， **LockType** 參數或屬性設定為 **adLockPessimistic**時，即會啟用封閉式鎖定。 另請參閱開放式鎖定。

 根據使用預先配置的資源集合（例如物件或資料庫連接）來共用效能優化。 從集區中繪製現有資源比建立新的資源更有效率。

 ProgID (程式設計識別碼) COM 應用程式對應至 Windows 登錄的唯一名稱。 ADO 連接的 ProgID 是「ADODB。連接」。 另請參閱 CLSID、COM。

 proxy 特定介面的物件，提供用戶端呼叫在不同執行環境中執行的應用程式物件所需的參數封送處理和通訊，例如在不同的執行緒或另一個進程中執行的應用程式物件。 Proxy 位於用戶端，而且會與相對應的存根進行通訊，該存根與所呼叫的應用程式物件位於同一個位置。 另請參閱存根。

## <a name="r"></a>R
 相對 URL：在網際網路或內部網路上指定資源的部分限定 URL，其位置是相對於絕對 URL 或對等 ADO 連線物件所指定的起點。 實際上，串連的絕對和相對 Url 會 consitute 完整的 URL。 另請參閱 URL 和絕對 URL。

 遠端資料源：存在於另一部電腦上的資料來源，而不是在執行用戶端應用程式) 的本機系統 (。

 資源記錄來自檔來源提供者的記錄，其中包含資料夾或檔的定義和描述欄位。 檔本身不包含在資源記錄中，但通常可以透過預設資料流程或包含 URL 的資源記錄中的欄位來存取。 另請參閱檔來源提供者、預設資料流程、URL。

 從資料來源資料列集的資料列集，全都具有相同的欄位架構。 資料列集可以代表資料表中的所有欄位或部分欄位。 資料列集也可以代表由查詢建立的虛擬資料表或兩個或多個資料表的聯結。 在 ADO 中，資料列集是以 **記錄集** 物件來表示。

## <a name="s"></a>S
 針對某個物件或變數的參考範圍，或在視圖或資料表中的一系列記錄範圍。 例如，只能在定義區域變數的程式內參考本機變數。 公用變數可從應用程式中的任何位置存取。 如果物件位於定義的搜尋路徑中，則物件（例如目前的資料庫）會在範圍內。 您可以使用多個命令中的 Scope 子句來指定記錄範圍。

 藉由產生和取用資料、增強 ADO 應用程式中的功能，來封裝服務的服務提供者軟體。 這是不會直接公開資料的提供者，而是提供服務，例如查詢處理。 服務提供者可能會處理資料提供者所提供的資料。 另請參閱資料提供者。

 已塑造的記錄集：其資料行已明確定義為不只包含資料的 **記錄** 集，但也 (稱為章節的參考，) **至其他記錄集物件** 和/或根據其他 **記錄集** 物件的計算值。

 在階層中相同層級的階層式結構中，有兩個或多個節點的同級。 階層中的根節點沒有任何同級。

 預存程式：預編譯的程式碼集合，例如 SQL 語句和選擇性的流程式控制制語句，儲存在名稱下並處理為一個單位。 預存程式會儲存在資料庫中;您可以使用應用程式的一個呼叫來執行，並允許使用者宣告的變數、條件式執行和其他強大的程式設計功能。

 stub 介面特定物件，此物件會提供應用程式物件接收來自用戶端的呼叫（在不同的執行環境中執行，例如在不同的執行緒或另一個進程中），以提供所需的參數封送處理和通訊。 存根是以應用程式物件來尋找，並與呼叫它的用戶端所在的對應 proxy 進行通訊。 另請參閱 proxy。

 子節點請參閱子節點。

 同步作業是由程式碼所起始的作業，這個作業會在下一項作業開始之前完成。 另請參閱非同步作業。

## <a name="t-z"></a>T-Z
 樹狀結構，代表) 專案 (節點之間的階層式關聯性。 樹狀結構的最上層有一個節點 (根) 。 在根底下，可以有多個子系。 每個子系可能會變成其他子系的父系，因此會像樹狀結構一樣。 包含檔和其他資料夾的資料夾是樹狀結構的一般範例。 另請參閱階層、節點、根、子系、父系。

 Web 服務器：提供 Web 服務和頁面給內部網路和網際網路使用者的電腦。