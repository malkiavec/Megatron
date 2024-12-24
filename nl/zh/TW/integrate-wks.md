---

copyright:
  years: 2015, 2018, 2019
lastupdated: "2019-01-08"

subcollection: discovery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:note: .note}
{:pre: .pre}
{:important: .important}
{:deprecated: .deprecated}
{:codeblock: .codeblock}
{:screen: .screen}
{:download: .download}
{:hide-dashboard: .hide-dashboard}
{:apikey: data-credential-placeholder='apikey'} 
{:url: data-credential-placeholder='url'}
{:curl: #curl .ph data-hd-programlang='curl'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:ruby: .ph data-hd-programlang='ruby'}
{:swift: .ph data-hd-programlang='swift'}
{:go: .ph data-hd-programlang='go'}

# 與 Watson Knowledge Studio 整合
{: #integrating-with-wks}

您可以將 {{site.data.keyword.knowledgestudiofull}} 的一或多個自訂模型與 {{site.data.keyword.discoveryshort}} 服務整合，以提供自訂實體和關係強化。
{: shortdesc}

這可讓您使用特定焦點區域的特有資訊來彈性地套用 {{site.data.keyword.discoveryshort}} 服務的文件強化功能，例如產業或科學紀律。您可以在強化模型中同時使用公用資料和您自己專屬的資料。

您可以使用服務 API 或 {{site.data.keyword.discoveryshort}} 工具來整合 {{site.data.keyword.knowledgestudioshort}} 模型與 {{site.data.keyword.discoveryshort}} 服務。

## 開始之前
{: #wks-beforeintegration}

在透過 {{site.data.keyword.knowledgestudioshort}} 來整合自訂模型與 {{site.data.keyword.discoveryshort}} 服務之前，您必須先使用 {{site.data.keyword.knowledgestudioshort}} 建立及部署該模型。如需建立及部署模型的相關資訊，請參閱 [{{site.data.keyword.knowledgestudioshort}} 文件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.ibm.com/docs/services/knowledge-studio/tutorials-create-project.html#wks_tutintro){: new_window}。您需要所部署模型的唯一 ID，才能將它與 {{site.data.keyword.discoveryshort}} 服務整合。

## 整合自訂模型與 API
{: #integrate-customAPI}

1.  取得 {{site.data.keyword.discoveryshort}} 環境的 ID，如[列出環境 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/discovery#list_environments){: new_window} 所述。記下環境 ID。
1.  列出現行 {{site.data.keyword.discoveryshort}} 配置的 ID，如[列出配置 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/discovery#list_configurations){: new_window} 所述。記下您要與 {{site.data.keyword.knowledgestudiofull}} 自訂模型整合的配置 ID。
1.  在 Bash Shell 或同等環境（例如 Cygwin for Windows）中執行下列指令，以下載現行 {{site.data.keyword.discoveryshort}} 配置的副本。將 `{environment_id}` 和 `{configuration_id}` 替換為您在前兩個步驟中記下的 ID。

    ```bash
    curl -u "apikey":"{apikey_value}" "https://gateway.watsonplatform.net/discovery/api/v1/environments/{environment_id}/configurations/{configuration_id}?version=2017-11-07" > my_config.json
    ```
    {: pre}

    此指令列出集合檔案的內容，並將它們放置在名稱為 `my_config.json` 的 JSON 檔案中。
1.  在文字編輯器中開啟 `my_config.json` 檔案，並進行下列變更：
    1.  變更 `"name"` 欄位的值，以指出新配置的用途。您也可以選擇性地變更 `"description"` 欄位的值。

        ```json
        ...
        "name": "wks-config",
        "description": "This is a configuration to use with a WKS model",
        ...
        ```
        {: codeblock}

    1.  使用 {{site.data.keyword.knowledgestudioshort}} 模型的資訊來更新強化欄位。假設強化欄位最初如下所示：

        ```json
        "enrichments": [
        {
            "source_field": "text",
            "destination_field": "enriched_text",
            "enrichment": "natural_language_understanding",
            "options": {
                "features": {
                    "entities": {
                        "sentiment": true,
                        "emotion": false,
                        "limit": 50
                    },
                    "sentiment": {
                        "document": true
                    },
                    "categories": {},
                    "concepts": {
                        "limit": 8
                    },
                    "relations": {}
                }
            }
        }]
        ```
        {: codeblock}

    1.  如下所示更新檔案，以「開始之前」所描述的 {{site.data.keyword.knowledgestudioshort}} 模型的唯一 ID 來替換 `{watson_knowledge_studio_model_ID}`。

        使用 API 能夠將多個自訂模型套用於相同的欄位。請參閱[整合多個自訂模型](/docs/services/discovery?topic=discovery-integrating-with-wks#integrate-multiplecustom)中的範例。如果您也要納入 [Watson {{site.data.keyword.discoveryshort}} Knowledge Graph](/docs/services/discovery?topic=discovery-kg#kg)，則必須使用相同的模型，以將單一強化物件中的實體和關係同時強化。
        {: note}

        ```json
        "enrichments": [
        {
            "source_field": "text",
            "destination_field": "enriched_text",
            "enrichment": "natural_language_understanding",
            "options": {
                "features": {
                    "entities": {
                        "sentiment": true,
                        "emotion": false,
                        "limit": 50,
                        "model": "{watson_knowledge_studio_model_ID}"
                    },
                    "sentiment": {
                        "document": true
                    },
                    "categories": {},
                    "concepts": {
                        "limit": 8
                    },
                    "relations": {
                      "model": "{watson_knowledge_studio_model_ID}"
                    }
                }
            }
        }]
        ```
        {: codeblock}

1.  儲存 `my_config.json` 檔案。
1.  使用 JSON 驗證器（例如 [JSLint ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://jslint.com){: new_window}）來驗證，必要的話，請先更正您所編輯的 JSON，然後再執行下一步。
1.  如下所示更新配置。同樣地，您需要在此程序開始時所收集的 `{environment_id}` 和 `{configuration_id}` ID。

    ```bash
    curl -X PUT -u "apikey":"{apikey_value}" -H "Content-Type: application/json" -d @my_config.json "https://gateway.watsonplatform.net/discovery/api/v1/environments/{environment_id}/configurations/{configuration_id}?version=2017-11-07"
    ```
    {: pre}

    **附註：**如果您要建立新配置或修改預設配置，則需要建立新的自訂配置，而不是更新現有的配置。在建立新配置之前，請確定 `"configuration_id":` 欄位已從您的 `my_config.json` 檔案中移除，然後執行下列指令：

    ```bash
    curl -X POST -u "apikey":"{apikey_value}" -H "Content-Type: application/json" -d @my_config.json "https://gateway.watsonplatform.net/discovery/api/v1/environments/{environment_id}/configurations?version=2017-11-07"
    ```
    {: pre}

    這兩個指令都會傳回已更新配置檔的內容。

### 整合多個自訂模型 
{: #integrate-multiplecustom}

您可以使用 API 將多個自訂模型套用於相同的欄位。請遵循[整合自訂模型與 API](/docs/services/discovery?topic=discovery-integrating-with-wks#integrate-customAPI) 中的步驟操作，並使用這裡的範例做為指南。如果您也要納入 [Watson {{site.data.keyword.discoveryshort}} Knowledge Graph](/docs/services/discovery?topic=discovery-kg#kg)，則必須使用相同的模型，以將單一強化物件中的實體和關係同時強化。請參閱 `"destination_field": "enriched_text"` 的範例做為指南。

您無法使用 {{site.data.keyword.discoveryshort}} 工具來套用多個自訂模型。只有實體和關係強化可供自訂。

您必須為每個相同的 `source_field` 指定不同的 `destination_field`。此外，每個 `source_field` 都必須由唯一的模型強化。例如，如果您想要將多個自訂模型套用於 `text` 的 `source_field`，而且您將 `model` `{watson_knowledge_studio_model_ID}` 套用於 `entities` 強化，則不應再為 `entities` 強化使用該模型。
{: tip}


```json
        "enrichments": [
        {
            "source_field": "text",
            "destination_field": "enriched_text",
            "enrichment": "natural_language_understanding",
            "options": {
                "features": {
                    "entities": {
                        "model": "{watson_knowledge_studio_model_ID}"
                },
                    "relations": {
                      "model": "{watson_knowledge_studio_model_ID}"
                    }
                }
    }
},
   {
        "source_field": "text",
        "destination_field": "enriched_text_2",
        "enrichment": "natural_language_understanding",
        "options": {
            "features": {
                    "entities": {
                        "model": "{watson_knowledge_studio_model_ID_b}"
            },
                    "relations": {
                      "model": "{watson_knowledge_studio_model_ID_c}"
            }
        }
    }
}]
```
{: codeblock}    

## 整合自訂模型與 Discovery 工具
{: #integrate-customtooling}

您可以透過 {{site.data.keyword.discoveryshort}} 工具將 {{site.data.keyword.knowledgestudioshort}} 自訂模型整合到[實體擷取](/docs/services/discovery?topic=discovery-configservice#entity-extraction)或[關係擷取](/docs/services/discovery?topic=discovery-configservice#relation-extraction)強化中。

您無法使用 {{site.data.keyword.discoveryshort}} 工具將多個自訂模型套用於相同的欄位。使用 API 能夠將多個自訂模型套用於相同的欄位。請參閱[整合自訂模型與 API](/docs/services/discovery?topic=discovery-integrating-with-wks#integrate-customAPI)。

1. 取得 {{site.data.keyword.knowledgestudioshort}} 模型的 `Model ID`。
1. 在 {{site.data.keyword.discoveryshort}} 工具中，按一下左上方的**管理資料**圖示，以開啟**管理資料**畫面，然後建立或開啟集合。**附註：**如果您選擇現有的集合，它應該是空的。否則，在建立新的配置檔之後，您應該重新汲取那些文件。
1. 在您集合之**管理資料**畫面的**配置**區段中，按一下**切換**，然後按一下**建立新的配置**。為此配置命名。 
1. 按一下**新增強化**，然後選取**實體擷取**或**關係擷取**強化。
1. 在所選取強化的 `Custom Model ID` 方框中，輸入 `Model ID`。自訂 {{site.data.keyword.knowledgestudiofull}} 模型將置換該強化的預設值。 
1. 按一下**套用**，然後按一下**完成**。

文件上傳至資料集合後，會使用針對該集合所選擇的配置檔來轉換及強化文件。如果您在上傳文件之後將現有的集合切換為新的配置檔，則那些已上傳的文件仍然由原始配置檔進行轉換。在切換配置檔之後所上傳的任何文件都會使用新的配置檔。如果您想要**整個**集合使用新的配置，則需要建立新的集合、選擇新的配置檔，然後重新上傳所有文件。

## 後續步驟
{: #wks-nextsteps}

請使用 {{site.data.keyword.discoveryshort}} 服務搭配新的配置來汲取專用資料。您以更新的配置所汲取的文件會使用自訂模型的資料自動強化。
