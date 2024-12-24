---

copyright:
  years: 2015, 2017
lastupdated: "2017-12-15"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# 版本注意事項

版本注意事項提供自舊版以來 {{site.data.keyword.discoveryfull}} 服務變更的相關資訊。
{: shortdesc}

## 服務 API 版本化
{: shortdesc}

API 要求需要以 `version=YYYY-MM-DD` 格式採用日期的版本參數。每當我們變更 API 的方式與舊版不相容時，我們就會發行該 API 新的次要版本。

請隨每一個 API 要求傳送版本參數。服務會使用您指定日期的 API 版本，或該日期之前的最新版本。不要預設為現行日期。請改為指定符合您應用程式相容版本的日期，而且在您的應用程式備妥可用於較新版本之前，請勿變更此日期。

現行版本為 `2017-11-07`。

## 測試版特性
{: #beta-features}

IBM 將提供分類為測試版或實驗性的服務、特性及語言支援。這些功能可能不穩定，可能會經常變更，因此可能一經通知就停止使用。它們是為了讓您評估其功能而提供。測試版或實驗性功能可能未提供一般發行功能所提供的相同效能或相容性層次。這些功能並非設計用於正式作業環境，如有這類使用需由您自行承擔風險。


## 變更
{: #change-log}

該服務有下列新增特性和變更。

## 2017 年 12 月 15 日

- 發行了**元素分類**強化，其可剖析控管文件中的元素（句子、清單、表格），以對重要種類和類型進行分類。如需相關資訊，請參閱[元素分類](/docs/services/discovery/element-classification.html)。「元素分類」無法用於已訂閱**超值**方案的服務實例。
- 新增了簡體中文和荷蘭文的基本語言支援。如需相關資訊，請參閱[語言支援](/docs/services/discovery/language-support.html)。目前，必須使用 API 來建立簡體中文和荷蘭文集合。
- 新增了「資料搜索器」的兩個新參數：`proxy_host_port` 和 `read-timeout`。如需詳細資料，請參閱[配置資料搜索器](/docs/services/discovery/data-crawler-discovery.html)。
- 汲取 PDF 文件時，可能會看到下列問題：
  - 當查詢汲取通知時，會以 `html` 傳回 PDF 文件的 `file_type` 欄位。
  - 針對 PDF 文件，結果的 `extracted_metadata` 物件中的 `file_type` 欄位是設為 `html`。
  - 文件詳細資料 API 也會將 PDF 文件的 `file_type` 欄位傳回為 `html`。

{{site.data.keyword.discoveryshort}} 工具：

- 針對 {{site.data.keyword.discoveryfull}} Knowledge Graph 測試版新增了視覺化查詢建置器。請參閱[使用 {{site.data.keyword.discoveryshort}} 工具查詢知識圖](/docs/services/discovery/building-kg.html#querying-kg)

## 2017 年 11 月 30 日

- 發行了 {{site.data.keyword.discoveryfull}} Visual Insights 的實驗性版本。您可以使用 Visual Insights，以視覺化方式探索 {{site.data.keyword.discoveryshort}} 基於對語意元素、關係、概念等等的瞭解所識別的連接。如需相關資訊，請參閱 [Visual Insights](/docs/services/discovery/visual-insights.html)。可以在[這裡](/docs/services/discovery/release-notes.html#beta-features)找到說明實驗性/測試版特性的陳述。
- 發行了 {{site.data.keyword.discoveryfull}} Knowledge Graph 的測試版，其可提供新的端點來查詢文件之間的實體及關係。這包括基於環境定義的搜尋和相關性分級。這項測試版特性只提供給**進階**方案使用者。它無法使用於**專用**環境。如需相關資訊，請參閱 [{{site.data.keyword.discoveryfull}} Knowledge Graph](/docs/services/discovery/building-kg.html)。可以在[這裡](/docs/services/discovery/release-notes.html#beta-features)找到說明測試版特性的陳述。
  - {{site.data.keyword.discoveryfull}} Knowledge Graph 中的已知問題：在汲取期間，所有實體類型名稱及關係類型名稱都會轉換為大寫。例如，實體 "GeoPoliticalEntity" 轉換為 "GEOPOLITICALENTITY"，而關係 "partOf”轉換為 "PARTOF"。
- 發行了其他兩種語言的 [{{site.data.keyword.discoverynewsfull}}](/docs/services/discovery/watson-discovery-news.html)：韓文 (`collection_id`: `news-ko`) 和西班牙文 (`collection_id`: `news-es`)。{{site.data.keyword.discoverynewsfull}} 韓文版和西班牙文版只能透過 API 來使用；如需透過 API 查詢集合的相關資訊，請參閱 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/discovery/api/v1/#query-collection){: new_window}。{{site.data.keyword.discoverynewsfull}} 英文版現在的 `collection_id` 為 `news-en`。早期，`collection_id` 是 `news` - 如果您是使用先前的 `collection_id`，它會繼續運作，不過，您可能會想要針對新專案切換至新的 `collection_id`。
- 查詢結果傳回 `score` 值，其指出查詢結果之間的相對相關性。從 2017 年 11 月 30 日開始，計算 `score` 的方式已變更。`score` 值只能用於在單一搜尋中對文件進行分級，而不能跨搜尋或階段作業。如果您已訓練集合，則會在自然語言查詢的結果中傳回 `score` 值。由於 `score` 指出查詢結果之間的相對相關性，因此不應使用它作為臨界值。請改用 `confidence` 來設定臨界值，它可指出與訓練模型相較之下的結果相關性。如需設定臨界值的相關資訊，請參閱[信賴度評分](/docs/services/discovery/train-tooling.html#confidence)。
- 從這個版本開始，段落擷取會偵測句子界限 - 它會嘗試傳回在句子開頭開始並在尾端結束的段落。以前，許多段落會在句子中間開始或結束。如需「段落擷取」的相關資訊，請參閱[段落](/docs/services/discovery/query-parameters.html#passages)。

## 2017 年 11 月 15 日

{{site.data.keyword.discoveryshort}} 工具：

- 新增了[關係擷取](/docs/services/discovery/building.html#relation-extraction)強化，其中包含可納入使用 {{site.data.keyword.knowledgestudiofull}} 所建立之自訂關係模型的選項。
- [實體擷取](/docs/services/discovery/building.html#entity-extraction)強化 {{site.data.keyword.discoveryshort}} 工具，現在包括可納入使用 {{site.data.keyword.knowledgestudiofull}} 所建立之自訂實體模型的選項。
- 從 {{site.data.keyword.discoveryshort}} 工具中移除了建立日文集合的選項，但是，使用 {{site.data.keyword.discoveryshort}} API 建立日文集合的選項仍保留。
- {{site.data.keyword.discoveryshort}} 工具現在支援聯合環境。

## 2017 年 11 月 10 日

{{site.data.keyword.discoveryshort}} 工具：

- 新增了其他選項來進行 {{site.data.keyword.discoveryshort}} 工具的「段落擷取」。現在當您查詢時，可以指定要從其中傳回段落的欄位、要傳回的段落數，以及每一個段落的字元數上限。如需限制、最小值和最大值，請參閱[段落](/docs/services/discovery/query-parameters.html#passages)。

## 2017 年 11 月 8 日

所有 API 呼叫的版本字串已從 `2017-10-16` 變更為 `2017-11-07`。此版本：
- 已將每一個查詢結果中的 `score` 移至名稱為 `results_metadata` 的新物件。
- 如果所查詢的集合已訓練，且查詢是自然語言查詢，則 `results_metadata` 會包含 `confidence` 欄位，其顯示該結果的信賴度評分。如需詳細資料，請參閱[信賴度評分](/docs/services/discovery/train-tooling.html#confidence)。
- 在汲取期間將過濾掉包含空格的欄位（例如：`body.additional reading`）。`notices` 說明會變成 `The field 'additional reading' is invalid: whitespace, '.', '#' and ',' are invalid in a field name`。
- 在汲取期間將過濾掉 `result_metadata` 欄位。

## 2017 年 10 月 16 日

- 所有 API 呼叫的版本字串已從 `2017-09-01` 變更為 `2017-10-16`。此版本不再支援將新文件上傳至使用 {{site.data.keyword.alchemylanguageshort}} 強化來強化的現有集合，也不再支援建立新集合及使用 {{site.data.keyword.alchemylanguageshort}} 強化來強化它們。以 {{site.data.keyword.alchemylanguageshort}} 強化的現有集合應儘快移轉到 {{site.data.keyword.nlushort}} 強化。如需詳細資料，請參閱[將強化移轉至 {{site.data.keyword.nlushort}}](/docs/services/discovery/migrate-nlu.html#migrating-enrichments-to-natural-language-understanding)。{{site.data.keyword.discoveryshort}} 工具也使用 `2017-10-16` 版本，如需相關資訊，請參閱下面。

{{site.data.keyword.discoveryshort}} 工具：

- {{site.data.keyword.discoveryshort}} 工具使用 `2017-10-16` API 版本字串，因此，如果您是使用該工具，則無法再將文件上傳至現有的 {{site.data.keyword.alchemylanguageshort}} 集合，或建立利用 `2017-10-16` 之後的 {{site.data.keyword.alchemylanguageshort}} 強化來強化的新集合。如果您要繼續使用 {{site.data.keyword.discoveryshort}} 工具來強化集合，請先將集合移轉到 {{site.data.keyword.nlushort}}。如需詳細資料，請參閱[將強化移轉至 {{site.data.keyword.nlushort}}](/docs/services/discovery/migrate-nlu.html#migrating-enrichments-to-natural-language-understanding)。
- **資料綱目瀏覽器**顯示對 {{site.data.keyword.discoverynewsfull}} 集合中的數個強化的範例查詢。它現在也有一個「顯示其他值」鏈結，此鏈結將在 {{site.data.keyword.discoverynewsfull}} 中顯示該強化的其他範例值。
- 多個生產力加強功能，包括結合集合統計資料、錯誤和警告，以及**管理資料**畫面的資料見解。
- 新增了一則訊息，可在文件完成處理時顯示警示。

## 2017 年 10 月 9 日

- 此 API 提供了新的聚集度量值 `unique_count`。它將傳回集合中所指定欄位的唯一實例計數。如需相關資訊，請參閱 [unique_count](/docs/services/discovery/query-aggregations.html#unique_count)。

{{site.data.keyword.discoveryshort}} 工具：

- 現在，**視覺化查詢建置器**中支援「直方圖」及「時間片段」聚集。您也可以選擇開啟「時間片段」查詢的異常偵測。
- **資料綱目瀏覽器**顯示所選擇強化的範例查詢。它現在也有一個「顯示其他值」鏈結，此鏈結將顯示該強化的其他範例值。
- 新增了 hamburger 功能表，使導覽**管理資料**、**檢視資料綱目**及**建置查詢**畫面更快速。

### 2017 年 10 月 3 日

- 現在可以使用文件分段。請參閱[使用文件分段來分割文件](/docs/services/discovery/building.html#doc-segmentation)。

### 2017 年 9 月 29 日

- {{site.data.keyword.discoveryshort}} 已在 2017 年 9 月 29 日於 `Germany` 地區推出。為了遵守 EU 資料法規，此地區不支援 AlchemyLanguage 強化。
- 已知問題：查詢欄位不能包含空格。在 {{site.data.keyword.discoveryshort}} 中撰寫查詢時，如果有任何查詢欄位包含空格（例如，`body.additional reading`），您會收到 `400: Invalid query syntax error`。

### 2017 年 9 月 25 日

- 現在提供「超值」定價方案。如需相關資訊，請參閱 [{{site.data.keyword.discoveryshort}} 定價方案](/docs/services/discovery/pricing-details.html)。
- 新增了在相同環境內的集合之間查詢、列出欄位及查詢通知的能力。如需詳細資料，請參閱[查詢多個集合](/docs/services/discovery/using.html#multiple-collections)。
- [語言支援](/docs/services/discovery/language-support.html)提供了 {{site.data.keyword.discoveryshort}} 的語言支援資訊

{{site.data.keyword.discoveryshort}} 工具：
- 「視覺化查詢建置器」已從測試版狀態移至 GA 狀態。「視覺化查詢建置器」目前不支援「過濾器」、「時間片段」及「直方圖」聚集。可按一下**包含結果的分析**，然後按一下**建置查詢**畫面上的**以查詢語言編輯**，來撰寫那些聚集。
- 新增了測試版功能，以刪除 {{site.data.keyword.discoverynewsfull}} 查詢的重複項目。
- 除了英文、德文及西班牙文語言集合之外，您現在還可以建立阿拉伯文、法文、義大利文、韓文及巴西葡萄牙文集合。
- 已知問題：{{site.data.keyword.discoveryshort}} 工具不支援聯合環境。

### 2017 年 9 月 14 日

{{site.data.keyword.discoveryshort}} 工具：

- 新增了「資料綱目瀏覽器」，它會顯示轉換後文件中的欄位和值。利用本資訊，您可以在使用「Discovery 查詢語言」建置查詢之前，先瞭解集合的資料結構。有兩種方式可檢視資料綱目：依文件（文件視圖）或依欄位（集合視圖）。若要存取「資料綱目瀏覽器」：在**我的資料見解**畫面上，按一下**檢視資料綱目**按鈕，或按一下左邊的**檢視資料綱目**圖示。

### 2017 年 9 月 6 日

- 新增了對您的查詢傳回的文件進行刪除重複文件的能力。此測試版特性同時適用於專用集合與 Watson Discovery News 集合。如需詳細資料，請參閱[從查詢結果中排除重複文件](/docs/services/discovery/query-parameters.html#deduplication)。

刪除重複文件目前僅支援作為測試版功能。如需相關資訊，請參閱本文件頂端有關測試版的陳述。

### 2017 年 8 月 31 日

- 所有 API 呼叫的版本字串已從 `2017-08-01` 變更為 `2017-09-01`。這個版本包含的更新項目將在預覽和汲取期間將過濾掉下列無效 JSON 欄位，因此只汲取有效的 JSON 欄位。將您的版本字串更新為 `2017-09-01`，以避免衝突和可能的錯誤。

   - 最上層的 `id`、`score` 及 `highlight`（您可以繼續透過 `add a document` 功能，使用文件 ID 將文件新增至集合中）。如需詳細資料，請參閱 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.ibm.com/watson/developercloud/discovery/api/v1/#add-doc){: new_window}。
   - 最上層以 `_` 作為字首的欄位名稱（因此，在依 ID 查詢文件時，您可以查詢 `id` 而非 `_id`）。
   - 欄位名稱中的 `#` 和 `,`
   - 以 `+` 和 `-` 作為字首的欄位名稱
   - 欄位名稱的 `"` `"` 空白值

**附註：**如果 JSON 文件在欄位名稱中包含這些字元，或最上層是 `id`、`score` 及 `highlight`，您必須先移除它們，然後才能將文件新增至集合，否則這些欄位會是空的。您可以先建立自訂配置並將 JSON 正規化，然後再將文件新增至集合以避免此問題。請參閱[自訂配置](/docs/services/discovery/building.html#custom-configuration)。此外，檔名中包含標點符號字元 `?`、`:` 或 `#` 的文件將導致汲取時發生錯誤。請先將任何包含這些字元的文件重新命名，然後再汲取它們。

- 更新了 `natural_language_query` 的擷取方法，透過比對單字與相關語意來改善結果的相關性。這個更新項目只會影響沒有相關性訓練的集合。如果您使用 `natural_language_query` 且未進行相關性訓練，則可能會看到所傳回結果的順序有所改善。

{{site.data.keyword.discoveryshort}} 工具：

- 對查詢建置器的一些變更，讓您在「Discovery 查詢語言」與「自然語言」查詢選項之間，以及在查詢、過濾器和聚集之間更容易進行切換。


### 2017 年 8 月 25 日

- `passages` 陣列現在包含 `field`、`start_offset` 及 `end _offset`。`field` 是從其中擷取段落的欄位名稱。`start_offset` 是欄位內的段落文字起始字元。`end_offset` 是欄位內的段落文字結束字元。

{{site.data.keyword.discoveryshort}} 工具：
這個查詢建置加強功能可以在**建置查詢**畫面上找到。

-  新增了透過視覺化建置器，以「{{site.data.keyword.discoveryshort}} 查詢語言」撰寫查詢的測試版能力。按一下**搜尋文件**及**限制查詢的文件**區段中的**在視覺化模式中建置**，即可試用它的功能。當您以視覺化方式建置查詢時，它會顯示在其下方的 **{{site.data.keyword.discoveryshort}} 查詢語言**中。

   視覺化查詢建置器目前僅支援作為測試版功能。如需相關資訊，請參閱本文件頂端有關測試版的陳述。

### 2017 年 8 月 18 日

{{site.data.keyword.discoveryshort}} 工具：

- 在 [2017 年 8 月 11 日](/docs/services/discovery/release-notes.html#11aug)引進的測試版視覺化聚集建置器中，新增了對巢狀聚集和條件的支援。每個聚集列有 3 個條件的限制。

   視覺化聚集建置器目前僅支援作為測試版功能。如需相關資訊，請參閱本文件頂端有關測試版的陳述。

### 2017 年 8 月 11 日
{: #11aug}

{{site.data.keyword.discoveryshort}} 工具：

這兩個特性都是查詢建置加強功能，可以在**建置查詢**畫面上找到。

- 新增了從一組預先建置的範例查詢和聚集中選取查詢的選項。按一下右上方的**使用範例查詢**以存取清單。如果您要查詢專用資料集合，則範例會使用在您集合中找到的 `top entities`、`categories` 等等。這些查詢可作為撰寫您自己的查詢的起點。{{site.data.keyword.discoverynewsfull}} 集合和專用集合都有可用的範例查詢。

-  新增了透過視覺化建置器來撰寫聚集的測試版能力。按一下**使用 {{site.data.keyword.discoveryshort}} 查詢語言撰寫聚集查詢**欄位上方的**在視覺化模式中建置**，以試用它的功能。當您以視覺化方式建置聚集時，該查詢將顯示在其下方的 **{{site.data.keyword.discoveryshort}} 查詢語言**中。  

   視覺化聚集建置器目前僅支援作為測試版功能。如需相關資訊，請參閱本文件頂端有關測試版的陳述。

### 2017 年 7 月 31 日

- 發行了 {{site.data.keyword.discoverynewsfull}} 的新版本。原始版本已重新命名為 {{site.data.keyword.discoverynewsfull}} Original，並已絕版，從 **2018 年 1 月 15 日**起不再提供服務。如需移轉指示，請參閱[從 Watson Discovery News Original 移轉](/docs/services/discovery/migrate-bwdn.html)。
  **附註：**如果您已建立 {{site.data.keyword.discoveryshort}} 的新實例，您只能存取 {{site.data.keyword.discoverynewsfull}} 的新版本。

- 發行了 {{site.data.keyword.discoveryfull}} 的新定價方案。如需詳細資料，請參閱 [{{site.data.keyword.discoveryshort}} 定價方案](/docs/services/discovery/pricing-details.html)。

- 所有 API 呼叫的版本字串已從 `2017-07-19` 變更為 `2017-08-01`。此版本包含新定價方案的更新項目，以及 Watson Discovery News 的新版本。請更新版本字串，以避免衝突和可能的錯誤。

### 2017 年 7 月 19 日

 - 在 2017 年 8 月 1 日發表的定價變更中，目前使用已淘汰之 **30 天免費試用**方案的使用者將自動移轉至**精簡**方案。由於這項轉移，現有的使用者可能已達到或已超出精簡方案限制，亦即文件數 _(2000)_、儲存空間 _(200Mb)_ 或集合數 _(2)_。如果您已超出**精簡**方案的限制，則無法將任何其他內容新增至該服務，但仍然可以查詢集合。您可以使用 {{site.data.keyword.discoveryshort}} 工具或 API 來檢視所有這些限制的現行狀態。若要能夠繼續將內容新增至 {{site.data.keyword.discoveryshort}} 實例，您必須執行下列其中一項：
   - 移除集合及（或）文件，使其不超出**精簡**方案的限制。
    可以透過 API 使用 [delete-doc](https://www.ibm.com/watson/developercloud/discovery/api/v1/#delete-doc) 方法個別地刪除文件，或利用工具或 API，使用 [delete-collection](https://www.ibm.com/watson/developercloud/discovery/api/v1/#delete-collection) 方法來刪除整個集合。
   - 將方案升級至符合儲存空間需求的層次。
 - 大小為 **`1`**、**`2`** 或 **`3`** 環境的客戶將自動移轉至**進階**方案。

### 2017 年 7 月 17 日

 - 下列功能已從測試版狀態移至 GA 狀態：

   - 相關性訓練
   - 自然語言查詢
   - 強調顯示

 - 從這個版本開始，{{site.data.keyword.discoveryfull}} 會將其強化機制從 {{site.data.keyword.alchemylanguageshort}} 變更為 {{site.data.keyword.nlushort}}。{{site.data.keyword.alchemylanguageshort}} 正在進行淘汰，您應該儘快開始使用 {{site.data.keyword.nlushort}}。如需詳細資料，請參閱[從 {{site.data.keyword.alchemylanguageshort}} 強化移轉至 {{site.data.keyword.nlushort}} 強化](/docs/services/discovery/migrate-nlu.html)。
   **附註：**當與 Watson Knowledge Studio 整合時，仍必須使用 {{site.data.keyword.alchemylanguageshort}} 強化配置。如需詳細資料，請參閱[與 {{site.data.keyword.knowledgestudiofull}} 整合](/docs/services/discovery/integrate-wks.html)。

 - 所有 API 呼叫的版本字串已從 `2017-06-25` 變更為 `2017-07-19`。此版本在建立集合時啟用 NLU 預設配置。在舊版中，您仍然能夠以 {{site.data.keyword.alchemylanguageshort}} 進行強化。

    預設配置已更新為使用 {{site.data.keyword.nlushort}}。您應該儘快更新版本字串，以避免衝突和可能的錯誤。

 - Discovery 工具：

    對於使用 {{site.data.keyword.alchemylanguageshort}} 強化進行強化的集合，Insight Cards 將不再自動更新。您必須將集合移轉至 {{site.data.keyword.nlushort}} 強化，Insight Cards 才會更新。

    如果您在 **2017 年 7 月 18 日**之前已建立集合，且已套用**預設配置**，則該集合已使用 {{site.data.keyword.alchemylanguageshort}} 強化來強化。如果您在此日期之後將**預設配置**套用至集合，將會使用 {{site.data.keyword.nlushort}} 強化（配置名稱會變成工具中的 **Default Configuration with NLU**）。由於 {{site.data.keyword.alchemylanguageshort}} 強化會被淘汰，所以不應用於新集合。

### 2017 年 6 月 30 日

 -  在 2017 年 5 月 5 日引進作為測試版特性的實體正規化功能，已移至 GA 狀態。如需詳細資料，請參閱[建立自訂配置以將實體正規化](/docs/services/discovery/normalize-entities.html)。

### 2017 年 6 月 23 日

 - 所有 API 呼叫的版本字串已從 `2016-12-01` 變更為 `2017-06-25`。如果集合的語言是設為其中一種語言，新的版本字串會以德文 (`de`) 或西班牙文 (`es`) 啟用強化。之前，無論集合的語言設定為何，都以英文執行所有強化。

    如果您未使用非英文語言的強化，則可以繼續使用 `2016-12-01` 版本字串。不過，您應該儘快更新版本字串，以避免潛在的未來衝突。

 - 現在，在 `timeslice` 聚集中，提供了異常偵測作為 GA 功能。如需詳細資料，請參閱[時間片段異常偵測](/docs/services/discovery/query-aggregations.html#anomaly-detection)。

 - Discovery 工具：

   - 新增了使用 Discovery 工具（相關性工具）來改善查詢結果相關性的測試版能力。請參閱[透過 Discovery 工具來改善查詢結果的相關性](/docs/services/discovery/train-tooling.html)。

### 2017 年 6 月 19 日

  - Discovery 工具：

    - 新增了可將新集合中的文件語言指定為英文、西班牙文或德文的選項。若要使用它，請在**命名您的新集合**對話框上，選擇**選取文件的語言**。

    - 在**建置查詢**畫面中新增了**摘要**標籤。**摘要**標籤顯示現有 **JSON** 標籤中所提供的完整查詢結果的概觀。**摘要**顯示畫面會根據您的查詢和強化而有所不同。可能顯示的資訊包括：文件名稱或 ID、聚集統計資料、依相關性順序列出的文件段落，以及依強化列出的結果。

    - 在**建置查詢**畫面中新增了「自然語言查詢」選項。若要使用它，請按一下**搜尋文件**區段中的**以簡單語言提出問題**，即會出現一個可讓您輸入問題的欄位。現在，以按一下**使用 Discovery 查詢語言**按鈕，即可存取原始查詢欄位（之前稱為**輸入查詢或關鍵字**）。

    - 已重新設計**建置查詢**畫面，但仍保留所有欄位和選項。以下是欄位的新舊名稱。

| **舊欄位名稱**                                           | **新欄位或區段名稱**                                                                                             |
|----------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| 撰寫並執行查詢                                           | 搜尋文件                                                                                                                         |
| 縮小查詢結果（過濾器）                                   | 限制您查詢的文件                                                                                                                         |
| 將查詢結果分組（聚集）                                   | 包含結果的分析                                                                                                                          |
| 要顯示的欄位                                             | 名稱不變，但已移至新的**自訂顯示選項**區段。                                                                        |
| 要傳回的文件數（計數）                                   | 要傳回的文件數 [此欄位已移至**自訂顯示選項**區段。]                                                                            |
| 包括相符的段落                                           | 包含相關段落 [此欄位已移至**自訂顯示選項**區段。]                                                                    |
| 要在開始時跳過的查詢欄位數（偏移）                       | 要在開始時跳過的查詢結果數 [此欄位已移至**自訂顯示選項**區段。]                                                                             |

### 2017 年 6 月 5 日

 - 現在，Watson Discovery News 查詢只會顯示 `text` 和 `alchemyapi_text` JSON 欄位中每一篇文章的前 150 個字。`blekko.snippet` 欄位只會顯示 Snippet 陣列的第一個句子。

### 2017 年 5 月 30 日

 - 查詢 API 上的 `passages` 參數已從測試版移至 GA 狀態。

### 2017 年 5 月 25 日

 - Discovery 工具：這一版新增了查詢欄位強調顯示。此特性會在「結果」窗格的 JSON 中加上黃色來強調顯示欄位名稱。每一個結果的所有已查詢或已過濾的欄位都會強調顯示，即使該欄位的內容不符合查詢也一樣。在聚集中使用的任何欄位也會在查詢結果中強調顯示，但只會強調顯示第一個聚集作業。

### 2017 年 5 月 10 日

 - `query` 和 `notices` 方法現在支援 `highlight` 參數。參數是布林。當您執行查詢且 `highlight` 是指定為 `true` 時，該服務傳回的輸出將包含一個新的 `highlight` 欄位，其中符合查詢的單字會包裝在 HTML `*`（強調）標籤中。如需詳細資料，請參閱[查詢參數](/docs/services/discovery/query-parameters.html#highlight)。

 - 可以只局部完成環境的刪除，但會導致無法建立新環境的狀況，因為只允許每個服務實例有一個環境。如果您試圖在刪除環境後再建立環境，但發現其中一項作業停留在 `pending` 狀態，則可能會發生這個問題。解決之道是重新執行刪除作業以完成它，然後建立新環境。

### 2017 年 5 月 8 日

 - 更新了情緒語氣評分模型，以改善情緒分析（`docEmotion`）強化的精準度。擴充了訓練資料集，且改變了特性工程設計，因此模型在基準性能測試資料集上具有更高的精準度。

### 2017 年 5 月 5 日

 - 實體正規化現在可以與使用 Watson Knowledge Studio 所產生之自訂模型的 Discovery 服務搭配使用。實體正規化會將不同參照的正規化（標準）名稱插入至來源文件中的相同人員或物件。如需詳細資料，請參閱[建立自訂配置以將實體正規化](/docs/services/discovery/normalize-entities.html)。

     **附註：**實體正規化目前僅支援作為測試版功能。如需相關資訊，請參閱本文件頂端有關測試版的陳述。

 - 工具錯誤日誌不再限制為最多八 (8) 頁的結果。如果沒有文件名稱，則錯誤日誌仍會顯示文件 ID。

 - 配置名稱限制為 50 個字元，而且必須由 `[a-zA-Z0-9-_]` 字元組成。

 - 先前只能透過 API 使用的 `passages` 參數，現在透過「工具」及 API 都可以使用。

### 2017 年 4 月 25 日

  - 該服務現在可讓您提供*訓練資料* 來改善查詢結果的正確性。當您提供具有訓練資料的 Discovery 實例時，該服務會使用進階 Watson 演算法來判定最相關的結果。當您新增更多訓練資料時，該服務實例在它傳回的結果中會變得更準確。如需相關資訊，請參閱[改善查詢結果的相關性](/docs/services/discovery/train.html)及 [API 參考資料](http://www.ibm.com/watson/developercloud/discovery/api/v1/#training-data)。

  - 現在，API 支援 `natural_language_query` 參數作為測試版。此參數可讓您以自然語言（而非 Discovery 服務的查詢語言）指定查詢。如需相關資訊，請參閱 API 參考資料中的[查詢集合](http://www.ibm.com/watson/developercloud/discovery/api/v1/#query-collection)方法。

  - 文件更新及勘誤更正。

### 2017 年 4 月 14 日

已將加強功能新增至查詢 API (`GET /v1/environments/{environment_id}/collections/{collection_id}/query`)。如需相關資訊，請參閱 API 參考資料中的[查詢集合](http://www.ibm.com/watson/developercloud/discovery/api/v1/#query-collection)方法。

  - 現在，查詢 API 支援 `passages` 參數。如果此參數設為 `true`，則查詢會從集合的文件中傳回一組最相關的段落。段落是由更準確的 Watson 演算法所產生，用來決定該查詢所傳回之所有文件中的最佳文字段落。這可讓您更精確地尋找資訊及環境定義。如需相關資訊，請參閱 API 參考資料中的[查詢集合](http://www.ibm.com/watson/developercloud/discovery/api/v1/#query-collection)方法。

    - 在查詢中指定 `passages=true` 可能會降低效能，這是因為增加了處理來擷取段落。在較大型的環境下，效能影響會減輕。

    - 只有在專用集合上才支援 `passages` 參數。在 Watson Discovery News 集合中不支援它。

    - `passages` 參數目前最多傳回 10 個結果。無法變更傳回的結果數。

    - `passages` 參數從集合的任何給定文件中最多傳回三 (3) 個段落。如果文件包含超過三個其他相關段落，該參數不會傳回它們。

### 2017 年 4 月 7 日

- 現在，查詢 API (`GET /v1/environments/{environment_id}/collections/{collection_id}/query`) 支援 `sort` 參數，它可讓您指定文件中要排序的欄位清單（以逗點區隔）。如需相關資訊，請參閱 API 參考資料中的[查詢集合](http://www.ibm.com/watson/developercloud/discovery/api/v1/#query-collection)方法。
- 現在，查詢聚集的 `timeslice` 參數可正確處理 UNIX epoch 格式的日期。如需聚集和 `timeslice` 參數的相關資訊，請參閱[查詢參照](/docs/services/discovery/query-reference.html#aggregations)。
- 改善錯誤訊息。
- 更新服務的 Java SDK。如需詳細資料，請參閱 [API 參考資料](http://www.ibm.com/watson/developercloud/discovery/api/v1/?java)。
- 在查詢中使用萬用字元的下列限制，現在已修正並可正確運作：

  - 在任何給定的查詢中，只能使用一個萬用字元。例如，`query-month:*ctober` 有效，但 `query-month:*ctobe*` 則產生剖析錯誤。
  - 萬用字元對於包含大寫字母的查詢無效。例如，假設指定索引鍵/欄位配對 `{"borrower": "GOVERNMENT OF INDIA"}`，`query-borrower:*ndia` 會傳回結果，但 `query-borrower:*NDIA` 則不會。

**附註：**在查詢的詞組中，不需要萬用字元。例如，假設指定索引鍵/欄位配對 `{"borrower": "GOVERNMENT OF TIMOR"}`，`query-borrower:"GOVERNMENT OF TIMOR"` 會傳回結果，但 `query-borrower:"GOVERNMENT OF TI*OR"` 則不會。在詞組內使用萬用字元並不適合，因為詞組的引號 (`"`) 內的所有字元都會跳出。

### 2017 年 3 月 24 日

- 在 Discovery 工具的「我的資料見解」畫面中新增了過濾

### 2017 年 3 月 15 日

探索到下列已知問題。

-  從 HTML、PDF 和 Word 文件汲取的所有欄位都是輸入為**字串**。JSON 欄位和計算欄位（例如觀感評分）會依定義的方式輸入。
- `preview` 作業目前不檢查已提交的 JSON 文件內的巢狀 JSON 陣列。該服務目前不支援巢狀 JSON 陣列，因此具有巢狀陣列的文件可以順利通過 `preview` 作業，但在嘗試汲取時會失敗。
- 如果發生汲取錯誤，並看到 `unsupported text language` 訊息，請以 `"language": "english"` 強化選項更新您的配置，以強制所有文字以英文解譯，如下列範例所示。

```json
"enrichments": [
   {
     "enrichment": "alchemy_language",
     "source_field": "author.label",
     "options": {
       "extract": "taxonomy,entity,relation,doc-emotion,doc-sentiment,concept,keyword",
       "sentiment": true,
       "quotations": true,
       "language": "english"
     }
   }
 ]
```
{: codeblock}

下列錯誤已修正。

- 已改善服務的效能和穩定性。

### 2017 年 3 月 8 日

 - 後端已最佳化，包括增加了新的逾時值，以改善整體效能。
 - 導致免費（大小為 `0`）環境的環境狀態不論實際狀態如何都報告為 `pending` 狀態，此錯誤已修正。
 - {{site.data.keyword.discoveryshort}} 目前唯一支援的國家語言是美國英文 (`en_US`)。

### 2017 年 3 月 3 日

- 在 Discovery 工具中新增了「我的資料見解」畫面。

### 2017 年 2 月 26 日

-     改善了 {{site.data.keyword.discoverynewsshort}} 環境的效能。
-  {{site.data.keyword.discoverynewsshort}} 服務一次只傳回 50 個結果。暫行解決方法是在查詢中使用 `offset` 參數來翻看結果。
-  您可以使用下列指令，對個別文件提交新的配置：

```bash
curl -X POST -u {username}:{password} -F "file=@wikipedia-sample.html" -F "configuration=$(cat config.json)" "https://gateway.watsonplatform.net/v1/environments/{environment_id}/collections/{collection_id}/documents?version=2016-12-01"
```
{: pre}
-  該服務的 PDF 和 Word 轉換器會建立 HTML 作為中間步驟。在最終轉換成正規化 JSON 之前，該服務可以在中間 HTML 上套用其他轉換和正規化。

下列錯誤已修正。

-  改進了錯誤碼。
-  更正了數個文件勘誤。

### 2017 年 2 月 16 日

-  現在，您可以使用 CSS 選取器來選取 JSON 欄位，然後對其套用強化。如需相關資訊，請參閱[使用 CSS 選取器來擷取欄位](/docs/services/discovery/building.html#using-css)。
-  現在，您可以將新的 `size: X` 參數傳遞給 [update-environment 方法](http://www.ibm.com/watson/developercloud/discovery/api/v1/#update_environment)來增加環境的大小，其中 `X` 是 0 與 3 之間的整數。如需環境大小和屬性的相關資訊，請參閱 [create-environment 方法](http://www.ibm.com/watson/developercloud/discovery/api/v1/#create_environment)。

    **附註：**您無法減少現有環境的大小。如果您想要減少環境的大小，請聯絡 {{site.data.keyword.IBM}} 支援人員以尋求協助。

-  有新的查詢運算子可用。`::!` 運算子已新增為 not-equals 一元運算子。例如，您現在可以執行 `query=field::!value`（不等於）。先前唯一的排他運算子是 `:!`，代表 not-contains 運算子（例如，`query=field:!value`）。

下列錯誤已修正。

-  已套用安全更新項目。
-  已改善搜尋警示的狀態訊息。

### 2017 年 2 月 1 日

下列附註特別適用於「資料搜索器」1.3.0 版。

-   「資料搜索器」會記錄用來上傳文件的 `document_id` 值，以及上傳的狀態。轉換通知在日誌外不會持續保存。目前沒有工具可與該資料互動，但若時間允許，預期將會開發這類工具。可透過 H2 資料庫來存取資料，該資料庫可配置為使用遠端 DBMS。

### 2017 年 1 月 16 日

下列附註特別適用於「資料搜索器」1.2.5 版。

-  「資料搜索器」可以選擇性地在上傳檔案之後立即輪詢文件狀態。這項檢查是搜索器「上傳文件」概念的一部分，因此當啟用這項檢查時，「搜索器」要同時上傳的文件數目，幾乎不太可能超過 {{site.data.keyword.discoveryshort}} 服務可以為該使用者同時處理的文件。

    `check_for_completion` 特性的負面影響是「搜索器」也可以向使用者公開文件失敗的原因和時間。附加至已順利上傳但無法處理的文件的任何通知，都會顯示在「搜索器」日誌中。通知不會匯出為可處理的檔案，但 IBM 歡迎對此提出特性建議。

### 2017 年 1 月 5 日

下列附註說明在 2016 年 12 月 15 日 GA 發行之後所識別的問題。

-   如果您使用 `POST /v1/environments/{environment_id}/collections/{collection_id}/documents` 或 `POST /v1/environments/{environment_id}/collections/{collection_id}/documents/[:{id}]` 呼叫來新增文件，則該呼叫會傳回文件 ID 及**處理中**狀態。如果您隨後使用 `GET /v1/environments/{environment_id}/collections/{collection_id}/documents/[:{id}]` 呼叫來查詢該文件，則狀態會保持在**處理中**直到汲取完成，屆時狀態會變更為**可用**。

    如果您使用 `POST /v1/environments/{environment_id}/collections/{collection_id}/documents/[:{id}]` 呼叫來**更新**現有文件，則即使該服務尚未完全處理已更新的文件，對應的 **GET** 呼叫仍會傳回 `available` 狀態。`available` 狀態係指原始文件或已更新的文件。除非更新作業傳回錯誤，否則目前無從判定已更新文件的狀態。

    暫行解決之道是在提交文件更新之後，先等待最多 10 分鐘，再嘗試查詢更新的內容。
-   您無法上傳 JSON 陣列。若要上傳 JSON 陣列，您必須個別上傳每一個區段。例如，下列 JSON 無法上傳至該服務：

    ```json
    [{
      "accepted": 1,
      "answer": "You shouldn't have any issues keeping it on all the time however some thing to consider is any counters you may have like the use of millis code . From the Arduino docs on millis a This number will overflow go back to zero after approximately 50 days. blockquote So for projects that are on for long periods of time you may not see an issue immediately but something like this could pop up and cause errors down the road. ",
      "answerScore": "49",
      "authorUserId": "3",
      "authorUsername": "Butzke",
      "downModVotes": 0,
      "id": 2,
      "subtitle": "I'm making a simple Arduino web server and I want to keep it turned on all the time. So it must endure to stay working continuously. I'm using an Arduino Uno with a Ethernet Shield. It's powered with a simple outlet power supply 5V 1A. My Questions Will I have any problems leaving the Arduino turned on all the time? li Is there some other Arduino board better recommended for this? li Are there any precautions that I need to heed regarding this? li ul ",
      "tags": "<arduino-uno><web-server><ethernet>",
      "title": "Is an Arduino capable of running 24 7?",
      "upModVotes": 49,
      "userId": "11",
      "userReputation": 4535,
      "username": "sachleen",
      "views": 3234
    }, {
      "accepted": 0,
      "answer": "A couple of things to keep in mind outside of Sachleen's mention of Milli's Like any electronics heat can be disruptive. The micro controller itself isn't likely going to be a huge issue from the perspective of heat but other components like the power supply might cause issues. li If your code uses EEPROMWrite a be aware that the EEPROM is only rated for something in the neighbourhood of 100 000 writes. li ul ",
      "answerScore": "24",
      "authorUserId": "3",
      "authorUsername": "Butzke",
      "downModVotes": 0,
      "id": 3,
      "subtitle": "I'm making a simple Arduino web server and I want to keep it turned on all the time. So it must endure to stay working continuously. I'm using an Arduino Uno with a Ethernet Shield. It's powered with a simple outlet power supply 5V 1A. My Questions Will I have any problems leaving the Arduino turned on all the time? li Is there some other Arduino board better recommended for this? li Are there any precautions that I need to heed regarding this? li ul ",
      "tags": "<arduino-uno><web-server><ethernet>",
      "title": "Is an Arduino capable of running 24 7?",
      "upModVotes": 24,
      "userId": "13",
      "userReputation": 489,
      "username": "Matthew G.",
      "views": 3234
    }]
    ```
    {: codeblock}

    若要將此資訊上傳至服務，請分解陣列並上傳每一個區段，如下所示：

    區段 1：

    ```json
    {
      "accepted": 1,
      "answer": "You shouldn't have any issues keeping it on all the time however some thing to consider is any counters you may have like the use of millis code . From the Arduino docs on millis a This number will overflow go back to zero after approximately 50 days. blockquote So for projects that are on for long periods of time you may not see an issue immediately but something like this could pop up and cause errors down the road. ",
      "answerScore": "49",
      "authorUserId": "3",
      "authorUsername": "Butzke",
      "downModVotes": 0,
      "id": 2,
      "subtitle": "I'm making a simple Arduino web server and I want to keep it turned on all the time. So it must endure to stay working continuously. I'm using an Arduino Uno with a Ethernet Shield. It's powered with a simple outlet power supply 5V 1A. My Questions Will I have any problems leaving the Arduino turned on all the time? li Is there some other Arduino board better recommended for this? li Are there any precautions that I need to heed regarding this? li ul ",
      "tags": "<arduino-uno><web-server><ethernet>",
      "title": "Is an Arduino capable of running 24 7?",
      "upModVotes": 49,
      "userId": "11",
      "userReputation": 4535,
      "username": "sachleen",
      "views": 3234
    }
    ```
    {: codeblock}

    區段 2：

    ```json
    {
      "accepted": 0,
      "answer": "A couple of things to keep in mind outside of Sachleen's mention of Milli's Like any electronics heat can be disruptive. The micro controller itself isn't likely going to be a huge issue from the perspective of heat but other components like the power supply might cause issues. li If your code uses EEPROMWrite a be aware that the EEPROM is only rated for something in the neighbourhood of 100 000 writes. li ul ",
      "answerScore": "24",
      "authorUserId": "3",
      "authorUsername": "Butzke",
      "downModVotes": 0,
      "id": 3,
      "subtitle": "I'm making a simple Arduino web server and I want to keep it turned on all the time. So it must endure to stay working continuously. I'm using an Arduino Uno with a Ethernet Shield. It's powered with a simple outlet power supply 5V 1A. My Questions Will I have any problems leaving the Arduino turned on all the time? li Is there some other Arduino board better recommended for this? li Are there any precautions that I need to heed regarding this? li ul ",
      "tags": "<arduino-uno><web-server><ethernet>",
      "title": "Is an Arduino capable of running 24 7?",
      "upModVotes": 24,
      "userId": "13",
      "userReputation": 489,
      "username": "Matthew G.",
      "views": 3234
    }
    ```
    {: codeblock}

### 2016 年 12 月 15 日，通用版

下列附註適用於 {{site.data.keyword.discoveryfull}} 服務的「通用版 (GA)」。

#### 一般注意事項

-   您目前無法指定欄位的資料類型。所有欄位都是以文字進行檢索（資料類型**字串**）。
-   如果您使用 API 來使用該服務，則必須在每一個呼叫中指定 API 版本。現行 API 版本為 **2016-12-01**。

    **附註：**GA 版本不強制使用特定版本，但仍必須列出它，才能啟用與未來版本的相容性。

-   您可以利用一個以 {{site.data.keyword.knowledgestudiofull}} 建立的自訂模型來使用該服務。自訂模型可用來強化所汲取的文件。您必須使用 API 來整合自訂模型與 {{site.data.keyword.discoveryshort}} 服務；您無法使用該工具來執行整合。如需詳細資料，請參閱[與 {{site.data.keyword.knowledgestudiofull}} 整合](/docs/services/discovery/integrate-wks.html "您可以整合來自 {{site.data.keyword.knowledgestudiofull}} 的自訂模型與 {{site.data.keyword.discoveryshort}} 服務，以提供自訂強化。")。

#### 資料管理

-   搜尋索引未加密。
-   備份及還原功能不是使用者可控制的。

#### 環境

-   您只能為每個服務實例建立一個環境來上傳您自己的資料。
-   {{site.data.keyword.discoveryshort}} 服務位於單一可用性區域（美國南部）。
-   目前無法使用專用及超值方案。

#### 環境大小調整

-   只有在建立新環境時，您才能選擇環境大小。使用者目前無法調整環境的大小。
-   選擇具有更多 RAM 的環境大小可增加效能。
-   目前沒有規定的調整大小建議可用於特定使用案例。
-   {{site.data.keyword.knowledgestudiofull}} 模型的自訂大小調整不是自助式。如需相關資訊，請聯絡您的 {{site.data.keyword.IBM}} 代表。

#### 汲取限制

-   汲取率目前限制為 100 個並行文件汲取作業。將文件提交至該服務進行汲取的應用程式需要重視 HTTP 429 錯誤，並據此對汲取要求進行節流控制。
-   {{site.data.keyword.alchemylanguageshort}} 強化限制為每個欄位前 50 KB。
-   來自 {{site.data.keyword.knowledgestudiofull}} 自訂模型的強化不受限制，但會將文件分割成 10-KB 區塊。不會在區塊界限之間標註任何關係。

#### 查詢限制

-   過多的查詢負載可能導致搜尋索引處理程序自動重新啟動。
-   發出查詢的應用程式必須對並行查詢數目施行合理的限制。

### 已知問題

-   您無法使用該工具來刪除文件。如果您需要刪除文件，必須如 API 參考資料所述使用 API 的[刪除文件](http://www.ibm.com/watson/developercloud/discovery/api/v1/#delete-doc)方法。

-   API 目前不支援取得在文件汲取期間產生的通知（警告和錯誤）清單。因此，該工具無法顯示汲取通知清單，所以不容易判斷「資料搜索器」所搜索到的哪些文件（如果有的話）無法進行汲取。
-   文件狀態資訊不一定精確。
    -   如果汲取作業所花費的時間超過所配置的 10 分鐘逾時，則該服務會報告其無法辨識出此文件，直到汲取作業完成為止。作業完成之後，文件狀態就會變成可用且精確。
    -   已順利檢索但產生錯誤的文件，可能短時間內的狀態為**失敗**，直到文件完全確定至索引為止。在文件確定至索引之後，列出的狀態才精確。
-   您無法使用該工具來取代特定文件。如果您嘗試這麼做，第二份文件會以個別文件的形式上傳。如果您要使用 API，且知道您要取代的文件 ID，您可以這麼做；請參閱 API 參考資料中的[更新文件](http://www.ibm.com/watson/developercloud/discovery/api/v1/#update-doc)。如果您要使用「資料搜索器」，則從與前一個文件相同的 URL 上傳已更新的文件，會取代原始文件。
-   如果您要使用該工具來編輯配置中的強化，則只能編輯用於擷取的強化。如果您想要新增或編輯其他強化（例如，來自 {{site.data.keyword.knowledgestudiofull}} 模型的自訂強化），則必須使用 API。如需相關資訊，請參閱 API 參考資料中的[更新配置](http://www.ibm.com/watson/developercloud/discovery/api/v1/#replace_configuration)方法。
-   下列附註特別適用於「資料搜索器」。
    -   如果發生上傳失敗，「資料搜索器」會重試上傳。
    -   「資料搜索器」無法重試已順利上傳但無法轉換或檢索的文件。
    -   「資料搜索器」沒有功能可檢查下游狀態，以及嘗試重新上傳下游失敗的 URL。
    -   不容易判斷「資料搜索器」汲取了哪些文件。比方說，如果您針對一組 500 份的文件執行「資料搜索器」，則「資料搜索器」在提交 65 份文件（總計 212 份文件的集合）時可能報告失敗。剩餘 223 份文件的狀態為「不確定」。

        有暫行解決方法可用，但它很複雜，且涉及直接呼叫 API。請聯絡 {{site.data.keyword.IBM}} 支援人員以尋求協助。
-   {{site.data.keyword.discoveryshort}} 的 Java、Python 及 Node.js SDK 沒有提供預設 REST (cURL) API 所提供的所有功能。並非所有 cURL 方法在非 cURL SDK 中都有對等的方法，而且並非所有非 cURL 方法都提供其 cURL 對等項目具有的所有相同特性。換言之，Java、Python 及 Node.js SDK 目前只會提供 cURL API 功能的子集。
-   如果您使用 Word 轉換器，則使用 `style` 索引鍵比對標題，比使用 `level` 索引鍵更精確且更有效率。
