---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-30"

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

# Watson Discovery News

{{site.data.keyword.discoverynewsfull}} 隨附於 {{site.data.keyword.discoveryshort}}。{{site.data.keyword.watson}} {{site.data.keyword.discoverynewsshort}} 是已使用下列認知見解進行預先強化的已檢索資料集：**關鍵字擷取**、**實體擷取**、**語意角色擷取**、**觀感分析**、**關係擷取**及**種類分類**。（若要進一步瞭解強化，請參閱[新增強化](building.html#adding-enrichments)。）也新增了下列其他 meta 資料：搜索日期和發佈日期。過去 60 天的新聞資料可供歷程搜尋。請參閱[這裡 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://discovery-news-demo.mybluemix.net/){: new_window}，它示範使用 {{site.data.keyword.discoverynewsfull}} 可建置的內容。

會隨著新文章持續更新 {{site.data.keyword.watson}} {{site.data.keyword.discoverynewsshort}}。{{site.data.keyword.discoverynewsshort}} 英文版每天大約會更新 300,000 篇新文章。{{site.data.keyword.discoverynewsshort}} 西班牙文版每天大約會更新 60,000 篇新文章；{{site.data.keyword.discoverynewsshort}} 韓文版每天會更新 10,000 篇新文章。

{{site.data.keyword.watson}} {{site.data.keyword.discoverynewsshort}} 的使用案例：

- 新聞警示 - 透過利用實體、關鍵字、種類及觀感分析的支援來監看新聞及對它的理解，以建立新聞警示。

- 事件偵測 - 主旨/動作/物件語意角色擷取會檢查詞彙/動作，例如 "acquisition"、"election results" 或 "IPO"。

- 新聞中的熱門話題 - 可識別熱門主題及監視提及它們（或相關主題）的頻率的增加及減少。

如需撰寫 {{site.data.keyword.discoverynewsfull}} 查詢的相關資訊，請參閱[查詢概念](/docs/services/discovery/using.html)及[查詢參照](/docs/services/discovery/query-reference.html)。

您無法調整 {{site.data.keyword.discoverynewsfull}} 配置、訓練，或將文件新增至 {{site.data.keyword.discoverynewsfull}} 集合中。

**附註：**對 Watson Discovery News 查詢傳回的結果數上限為 `50`。使用其他查詢及 `offset` 參數，可傳回超過 `50` 個結果。

**附註：**{{site.data.keyword.discoverynewsfull}} 的這個版本在 **2017 年 7 月 31 日**初次亮相。原始版本已重新命名為 {{site.data.keyword.discoverynewsfull}} Original，並已絕版，從 **2018 年 1 月 15 日**起不再提供服務。如需移轉的相關資訊，請參閱[從 Watson Discovery News Original 移轉](/docs/services/discovery/migrate-bwdn.html)。
