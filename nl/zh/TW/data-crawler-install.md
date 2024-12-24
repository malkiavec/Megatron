---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-18"

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

# 下載並安裝資料搜索器

「資料搜索器」會收集最後用來形成 {{site.data.keyword.discoveryshort}} 服務的搜尋結果的原始資料。搜索資料儲存庫時，搜索器會從使用者指定的種子 URL 開始下載文件及 meta 資料。搜索器會探索階層中的文件，或者從種子 URL 鏈結，並將這些文件放入佇列以進行擷取。
{: shortdesc}

## 必備項目

-   Java Runtime Environment 第 8 版或更新版本

    `JAVA_HOME` 環境變數必須正確設定，或完全不設定，才能執行「搜索器」。
    {: tip}
-   Red Hat Enterprise Linux 6 或 7，或 Ubuntu Linux 15 或 16。為了達到最佳效能，「資料搜索器」應該在自己的 Linux 實例上執行，不論它是虛擬機器、容器或硬體。

-   Linux 系統上最少有 2 GB RAM

## 下載並安裝資料搜索器

1.  開啟瀏覽器，並登入 [{{site.data.keyword.Bluemix}} 帳戶 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.ng.bluemix.net){: new_window}。

1.  從 {{site.data.keyword.Bluemix_notm}} 儀表板中，選取您先前建立的 {{site.data.keyword.discoveryshort}} 服務。

1.  按「下載資料搜索器」鏈結以下載「資料搜索器」。

1.  驗證您執行的是 Java Runtime Environment 第 8 版或更新版本。執行 `java -version` 指令，並尋找 **1.8**。如果您執行 **1.8** 之前的版本，則需要從套件管理系統安裝 Java Developer Kit (JDK) 8 來升級 Java，您可以從 [IBM JDK ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/developerworks/java/jdk/){: new_window}網站或從 [java.com ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.java.com){: new_window} 來進行。

    `JAVA_HOME` 環境變數必須正確設定，或完全不設定，才能執行「搜索器」。
    {: tip}

1.  以管理者身分，使用適當的指令來安裝您下載的保存檔：

    -   在使用 rpm 套件的 Red Hat 及 CentOS 之類的系統上，請使用如下的指令：`rpm -i /full/path/to/rpm/package/rpm-file-name`
    -   在使用 deb 套件的 Ubuntu 及 Debian 之類的系統上，請使用如下的指令：`dpkg -i /full/path/to/deb/package/deb-file-name`
    -   「搜索器 Script」會安裝至 `{installation_directory}/bin`；例如，`/opt/ibm/crawler/bin`。請確定 `{installation_directory}/bin` 位於 `PATH` 環境變數中，「搜索器」指令才能正確運作。

    「搜索器 Script」也會安裝至 `/usr/local/bin`，因此這也可以新增至 `PATH` 環境變數。
    {: tip}
1.  建立工作目錄，方法是將 `{installation_directory}/share/examples/config` 目錄的內容複製到系統上的工作目錄，例如 `/home/config`。

    **警告：**請勿直接修改提供的配置範例檔。請複製後再進行編輯。如果您直接編輯範例檔，則在升級「資料搜索器」時可能會改寫您的配置，或在解除安裝時可能會將其移除。

    **附註：**本手冊其餘部分如參照 `config` 目錄中的檔案（例如 `config/crawler.conf`），是參照您工作目錄中的該檔案，而「非」已安裝的 `{installation_directory}/share/examples/config` 目錄中的檔案。

1.  現在您可以[配置資料搜索器以連接至儲存庫](/docs/services/discovery/data-crawler-seeds.html)

## 資料搜索器結構

「資料搜索器」下載會將下列資料夾放置在您的系統上：

-   `doc` - 包含具有著作權和授權資訊的檔案。
-   `bin` - 用來執行搜索器的 Script 檔。
-   `connectorFramework` - 此目錄中的檔案可讓您與資料交談，不論是企業中的內部資料或 Web 或雲端中的外部資料。
-   `lib` - 搜索器使用的程式庫檔案。
-   `share`
    -   `doc` - 同時提供 HTML 和 Markdown 格式的文件檔。
    -   `examples/config` - 這些檔案可讓您告知搜索器要用於其搜索的資料、在搜索完成之後要將所搜索資料的集合傳送至何處，以及其他搜索管理選項。
    -   `man` - 產品說明頁搜索器文件。

## 此版本的已知限制

-   使用無效或遺漏的 URL 執行「檔案系統」連接器時，「資料搜索器」可能會當掉。
-   在 `crawler.conf` 檔案中配置 `urls_to_filter` 值，使所有白名單 URL 或 RegEx 都包含在單一 RegEx 表示式中。如需相關資訊，請參閱[配置搜索選項](/docs/services/discovery/data-crawler-discovery.html#configuring-crawl-options)。
-   `--config -c` 選項中所傳入的配置檔路徑必須是完整路徑。也就是說，它必須採用相對格式 `config/crawler.conf` 或 `./crawler.conf`，或絕對路徑 `/path/to/config/crawler.conf`。只有當 `orchestration_service.conf` 檔案是以行內方式存在，而非在 `crawler.conf` 檔案中使用 `include` 來參照時，才能單獨指定 `crawler.conf`。
