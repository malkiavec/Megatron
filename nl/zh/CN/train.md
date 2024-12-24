---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-08"

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

# 使用 API 改进结果相关性

可以培训 {{site.data.keyword.discoveryshort}} 服务以改进特定组织或主题区域的查询结果相关性。向 {{site.data.keyword.discoveryshort}} 实例提供*培训数据*时，服务会使用机器学习 Watson 方法在您的内容和问题中查找信号。然后，服务会对查询结果进行重新排序，使最相关的结果显示在最前。添加更多培训数据后，服务实例对所返回的结果排序将变得更准确、更复杂。
{: shortdesc}

相关性培训是可选的；如果查询结果满足您的需求，那么没必要进一步培训。有关构建用例进行培训的概述，请参阅博客帖子 [How to get the bost out of Relevance Training ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/dwblog/2017/get-relevancy-training/){: new_window}。

有关培训 API 的综合信息，请参阅 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/watson/developercloud/discovery/api/v1/){: new_window}。

如果您希望使用 {{site.data.keyword.discoveryshort}} 工具来培训 {{site.data.keyword.discoveryshort}}，请参阅[使用工具改进结果相关性](/docs/services/discovery/train-tooling.html)。

**注：**相关性培训需要满足特定培训数据需求才能生效。服务会定期检查培训数据以确定是否满足这些需求，并自动根据任何更改来更新自身。

**注：**目前，相关性培训仅适用于专用集合中的自然语言查询。它不适用于结构化的 {{site.data.keyword.discoveryshort}} Query Language 查询。有关 {{site.data.keyword.discoveryshort}} Query Language 的更多信息，请参阅[查询概念](/docs/services/discovery/using.html)。

已培训的集合将在自然语言查询的结果中返回 `confidence` 分数。请参阅[置信度分数](/docs/services/discovery/train-tooling.html#confidence)以获取详细信息。

**注：**每个环境最多可有 4 个经过培训的集合。

<!-- A trained Discovery service instance is intended primarily for use with natural language queries, but it works equally well with queries that use structured syntax. -->  <!-- See [Query Concepts](/docs/services/discovery/using.html) and the [Query reference](/docs/services/discovery/query-reference.html) for information about structured queries and natural language queries. -->

培训 Discovery 实例所需的组件包括：

 - **培训数据**。这是服务用于优化查询结果的*查询*和*示例*集。
 - **查询**。这是应用于培训数据集的自然语言查询。每个查询都有一个或多个关联的*示例*，如以下各项目符号点中所述。每个查询在培训数据集内必须唯一。
 - **示例**。这是在 Discovery 集合中建立了索引的文档，充当关联查询的样例（**好或差**）。向培训数据查询添加示例后，在将其应用于指定查询时，可包含相关性标签，用于指示文档的相关性（即“好”与“差”）。

   示例由已建立索引的文档标识进行标识。如上所述，每个示例必须包含一个标签，用于指示文档与查询的相关性是“好”还是“差”。

   示例可以选择指定交叉引用查询。交叉引用查询需要仅返回示例文档，并且必须独立于唯一的 Watson Discovery 文档标识。目前，不会自动使用交叉引用查询，但在摄入事件期间将新标识分配给文档的情况下，可以将其用于修复培训数据。

## 培训数据需求

培训数据必须满足以下**最低**质量条件，才可有效改进 Discovery 服务返回的答案的相关性。请注意，**最低**并不意味着**最佳**。

- 集合的培训数据集必须包含至少 49 个唯一培训查询（即，查询和示例集）。根据集合的大小和复杂性，集合中的培训查询数可能需要多于 49 个，Watson 才能将相关性培训应用于该集合。
- 每个培训查询的相关性分数必须为非负整数，例如 `0` 表示 *不相关*，`1` 表示 *有些相关*，`2` 表示 *高度相关*。但是，为了实现最大的灵活性，服务接受 `0` 到 `100` 之间的非负整数，以供高级用户试用不同的评分方案。无论您使用哪个范围，培训查询集内的最大整数都表示最大相关性。{{site.data.keyword.discoveryshort}} 工具使用相关性分数 `0` 表示 *不相关*，使用 `10` 表示*相关*。如果您计划使用 {{site.data.keyword.discoveryshort}} 工具和 API 对文档进行评分，或者计划从 API 开始，然后移至工具，请使用 `0` 到 `10` 的相关性分数。
- 培训查询必须在查询与期望答案之间包含一些项重叠，以便可以由 Discovery 服务的范围广泛的初始搜索检索到。

**注：**Watson 使用培训数据是为了学习模式和执行一般化，而不是为了记住各个培训查询。因此，对于任何给定的培训查询，服务可能不一定会重现完全相同的相关性结果。

## 向培训数据集添加查询

使用 `POST /v1/environments/{environment_id}/collections/{collection_id}/training_data` 方法可将查询添加到集合的培训数据集。查询会指定为以下格式的 JSON 对象：

```json
{
  "query_id": "string",
  "natural_language_query": "string",
  "filter": "string",
  "examples": [
    {
      "document_id": "string",
      "cross_reference": "string",
      "relevance": 0
    }
  ]
}
```
{: codeblock}

此对象中的值如下所示：

- `query_id`：查询的唯一标识。如果未指定此字段，那么服务会自动生成标识。
- `natural_language_query`：应用于培训集的 Discovery 自然语言查询。<!-- The `natural_language_query` parameter is preferred. -->
- `filter`：查询的可选过滤器，如[查询参考](/docs/services/discovery/query-reference.html#parameter-descriptions)中所述。

    **注：**如果在培训数据查询中包含过滤器，请确保在已培训集合中使用自然语言查询时使用相同的过滤器。如果使用已过滤的数据来培训集合，但在查询该集合时未使用相同类型的过滤器，那么结果可能不可预测。

- `examples`：包含以下值的数组：

   - `document_id`：应用于培训集的文档的唯一标识。这是先前描述的*示例*。
   - `cross_reference`：可选标签，通常由所引用文档中的某个字段组成，用于在文档标识更改时（例如，对新摄入的文档指定了相同标识时），“锁定”文档和字段的信息。为 `cross-reference` 指定值**不会**将一个文档链接到另一个文档；而是会确保在重命名或覆盖文档时，服务将保留文档的相关信息。
   - `relevance`：从 `0` 到 `100`（含 0 和 100）的整数，用于指示查询与培训数据的相对相关性。值越高，相关性也越高。值 `0` 指示与查询完全不相关，而值 `100` 指示与查询绝对相关。

   **注：**尽管为了实现最大的灵活性，`relevance` 参数的范围为 `0` 到 `100`，但您可以使用较小的范围来简化评分示例。标准范围可能为 `0` 到 `4`，您也可以使用整个范围，但只能以 20 为增量（`0`、`20`、`40`、`60`、`80` 和 `100`）。{{site.data.keyword.discoveryshort}} 工具使用相关性分数 `0` 表示 *不相关*，使用 `10` 表示*相关*。如果您计划使用 {{site.data.keyword.discoveryshort}} 工具和 API 对文档进行评分，或者计划从 API 开始，然后移至工具，请使用 `0` 到 `10` 的相关性分数。

以下对象显示了填充的培训数据查询。

```json
{
  "natural_language_query": "why is the sky blue",
  "filter": "text:meteorology",
  "examples": [
    {
      "document_id": "9afcf06e-2ef7-438e-b2a5-e4d9432dc877",
      "relevance": 0
    },
    {
      "document_id": "54f95ac0-3e4f-4756-bea6-7a67b2713c81",
      "relevance": 1
    },
    {
      "document_id": "01bcca32-7300-4c9f-8d32-33ed7ea643da",
      "cross_reference": "my_id_field:1463",
      "relevance": 4
    }
  ]
}
```
{: codeblock}

以下命令示例将先前的培训数据查询添加到名为 `a56dd9b4-040b-4ea3-a736-c1e7a467e191` 的环境中名为 `99040100-fe6a-4782-a4f5-28f9eee30850` 的集合：

```bash
curl -X POST -u "4ba1624f-48b6-484a-8e32-18d1c205c1fa":"qUy3B0CbGf9G" -H "Content-Type: application/json" -d
'{
  "natural_language_query": "why is the sky blue",
  "filter": "text:meteorology",
  "examples": [
    {
    "document_id": "9afcf06e-2ef7-438e-b2a5-e4d9432dc877",
    "relevance": 0
    },
    {
      "document_id": "54f95ac0-3e4f-4756-bea6-7a67b2713c81",
      "relevance": 1
    },
    {
      "document_id": "01bcca32-7300-4c9f-8d32-33ed7ea643da",
      "cross_reference": "my_id_field:1463",
      "relevance": 4
    }
  ]
}'
"https://gateway.watsonplatform.net/discovery/api/v1/environments/a56dd9b4-040b-4ea3-a736-c1e7a467e191/collections/99040100-fe6a-4782-a4f5-28f9eee30850/training_data?version=2016-12-01"
```
{: pre}

## 向培训数据查询添加示例

创建培训数据查询后，可以继续向其添加示例以提高培训的准确性。使用 `POST /v1/environments/{environment_id}/collections/{collection_id}/training_data/{query_id}` 向现有培训数据查询添加示例。

执行以下步骤以向培训数据查询添加示例。

1. 通过[列出集合的培训数据查询 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/watson/developercloud/discovery/api/v1/#get-training-data){: new_window}，获取要向其添加新示例的培训数据查询的查询标识：

   ```bash
    curl -u "4ba1624f-48b6-484a-8e32-18d1c205c1fa":"qUy3B0CbGf9G" "https://gateway.watsonplatform.net/discovery/api/v1/environments/a56dd9b4-040b-4ea3-a736-c1e7a467e191/collections/99040100-fe6a-4782-a4f5-28f9eee30850/training_data?version=2016-12-01"
   ```
   {: pre}

   返回的 JSON 格式如下：

   ```json
    {
      "query_id": "484baad4-d440-44b7-a0dd-70bb2ac77baa",
      "natural_language_query": "why is the sky blue",
      "filter": "text:meteorology",
      "examples": [
        {
          "document_id": "9afcf06e-2ef7-438e-b2a5-e4d9432dc877",
          "relevance": 0
        },
        {
          "document_id": "54f95ac0-3e4f-4756-bea6-7a67b2713c81",
          "relevance": 1
        },
        {
          "document_id": "01bcca32-7300-4c9f-8d32-33ed7ea643da",
          "cross_reference": "my_id_field:1463",
          "relevance": 4
        }
      ]
    }
   ```
   {: codeblock}

1. 使用在创建新的培训数据查询时用于定义示例的相同语法来添加新示例。以下命令示例不包含交叉引用。

   ```bash
    curl -u -X POST -u "4ba1624f-48b6-484a-8e32-18d1c205c1fa":"qUy3B0CbGf9G" -H "Content-Type: application/json" -d
    '{
      "document_id": "46b52fdc-3a72-4700-9849-ac217532b373",
      "relevance": 3
    }' "https://gateway.watsonplatform.net/discovery/api/v1/environments//a56dd9b4-040b-4ea3-a736-c1e7a467e191/collections/99040100-fe6a-4782-a4f5-28f9eee30850/training_data/484baad4-d440-44b7-a0dd-70bb2ac77baa?version=2016-12-01"
   ```
   {: pre}

1. 通过再次[列出集合的培训数据查询 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/watson/developercloud/discovery/api/v1/#get-training-data){: new_window}，验证新示例是否已添加到培训数据查询中：

   ```bash
    curl -u "4ba1624f-48b6-484a-8e32-18d1c205c1fa":"qUy3B0CbGf9G" "https://gateway.watsonplatform.net/discovery/api/v1/environments/a56dd9b4-040b-4ea3-a736-c1e7a467e191/collections/99040100-fe6a-4782-a4f5-28f9eee30850/training_data?version=2016-12-01"
   ```
   {: pre}

   返回的 JSON 格式如下：

   ```json
    {
      "query_id": "484baad4-d440-44b7-a0dd-70bb2ac77baa",
      "natural_language_query": "why is the sky blue",
      "filter": "text:meteorology",
      "examples": [
        {
          "document_id": "9afcf06e-2ef7-438e-b2a5-e4d9432dc877",
          "relevance": 0
        },
        {
          "document_id": "54f95ac0-3e4f-4756-bea6-7a67b2713c81",
          "relevance": 1
        },
        {
          "document_id": "01bcca32-7300-4c9f-8d32-33ed7ea643da",
          "cross_reference": "my_id_field:1463",
          "relevance": 4
        },
        {
          "document_id": "46b52fdc-3a72-4700-9849-ac217532b373",
          "relevance": 3
        }
      ]
    }
   ```
   {: codeblock}

1. 使用[列出集合详细信息 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/watson/developercloud/discovery/api/v1/#list-collection-details){: new_window} 方法并查看 `"training"`/`"available"` 字段的值来检查培训的状态。根据培训需求添加了足够的查询和示例后，该字段的值会返回为 `true`，并且服务会自动开始使用培训数据。

   ```bash
    curl -u "4ba1624f-48b6-484a-8e32-18d1c205c1fa":"qUy3B0CbGf9G" "https://gateway.watsonplatform.net/discovery/api/v1/environments/a56dd9b4-040b-4ea3-a736-c1e7a467e191/collections/99040100-fe6a-4782-a4f5-28f9eee30850?version=2016-12-01"
   ```
   {: pre}

   返回的 JSON 格式如下：

   ```json
    {
      "collection_id": "99040100-fe6a-4782-a4f5-28f9eee30850",
      "name": "democollection",
      "description": "this is a demo collection",
      "created": "2015-08-24T18:42:25.324Z",
      "updated": "2015-08-24T18:42:25.324Z",
      "status": "available",
      "configuration_id": "def9bd08-8472-470f-ab5a-e377f77e9300",
      "language": "en_us",
      "document_counts": {
        "available": 1000,
        "processing": 20,
        "failed": 180
      },
      "training": {
        "total_examples": 54,
        "available": true,
        "processing": false,
        "minimum_queries_added": true,
        "minimum_examples_added": true,
        "sufficient_label_diversity": false,
        "notices": 13,
        "successfully_trained": "2017-02-08T14:18:22.786Z",
        "data_updated": "2017-02-10T14:18:22.786Z"
      }
    }
   ```
   {: codeblock}

1. 上一步中的以下字段全部返回 `true` 时，发出一些样本查询来查看服务是否返回更相关的结果：

   - `minimum_queries_added`
   - `minimum_examples_added`
   - `sufficient_label_diversity`

   如果结果的相关性未得到改进，请添加更多培训查询，直到结果满足您的需求。

有关其他培训指导信息，请参阅[相关性培训技巧](/docs/services/discovery/train-tips.html#relevancy-tips)。   

## 执行其他培训数据查询操作
{: #training-data-operations}

可以使用其他 API 方法来管理和维护培训数据查询，如 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/watson/developercloud/discovery/api/v1/){: new_window} 中所述：

 - [列出集合的培训数据 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/watson/developercloud/discovery/api/v1/#get-training-data){: new_window}
 - [删除集合的所有培训数据 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/watson/developercloud/discovery/api/v1/#delete-all-training-data){: new_window}
 - [显示指定培训数据查询的内容 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/watson/developercloud/discovery/api/v1/#show-td-query){: new_window}
 - [从集合中删除培训数据查询 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/watson/developercloud/discovery/api/v1#delete-td-query-example){: new_window}
 - [更改培训数据查询示例的相关性标签或交叉引用 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/watson/developercloud/discovery/api/v1/#update-example){: new_window}
 - [从培训数据查询中删除示例文档 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/watson/developercloud/discovery/api/v1/#delete-example){: new_window}

 **错误监视：**培训数据错误会以通知方式显示，您可以使用[查询通知 API ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/watson/developercloud/discovery/api/v1/#query-notices){: new_window} (`GET /v1/environments/{environment_id}/collections/{collection_id}/notices`) 来监视通知。
