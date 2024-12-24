---

著作権:
  年: 2015、2017
最終更新日: "2017-12-15"

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

# Watson Discovery Knowledge Graph

ナレッジ・グラフは、さまざまな文書にあるデータを関連付けて新しいナレッジを生成することにより、単なるデータや情報を上回る価値を生み出します。IBM は非構造化データからカスタム・ナレッジ・グラフを自動的に作成する AI テクノロジーを提供しています。これは、エンティティーと関係を抽出してあいまいさを除去し、アルゴリズム手法を使用して関係をエンリッチし、さらに関連性アルゴリズムを使用して結果をランク付けすることによって行われます。Knowledge Graph は企業の「ナレッジ・ハブ」として機能し、エンタープライズに対応した検索、要約、推奨の各エンジンや、その他の意思決定プロセス (例えば、不正、無駄、悪用の検出など) に使用できます。{{site.data.keyword.knowledgestudioshort}} で作成したカスタム・モデルを Knowledge Graph の作成プロセスで使用すると、金融、テクノロジー、セキュリティー、インテリジェンス、医療などの領域やその他多くの領域に適用可能な、領域固有のナレッジ・グラフの構築に役立ちます。

2 つの新しいエンドポイントが {{site.data.keyword.discoveryfull}} に追加され、非構造化文書のコレクションにある文書全体で、あいまいさを除去したエンティティーやエンリッチされた関係を検索する機能が提供されました。検索結果は、関連性または人気の順番にランク付けできます。API では、検索トークンを使用できるほか、自動的に作成された大規模なナレッジ・グラフ内で、より関連性の高いエンティティーや関係を検索するオプションのコンテキスト・ワードや文節を使用できます。

 次の図は、Knowledge Graph がどのように現在の {{site.data.keyword.discoveryfull}} パイプラインに適合するのかを示します。{{site.data.keyword.nlushort}} は、エンティティーを持つ文書をそれぞれの文書レベルでエンリッチします。Knowledge Graph の作成時には、暗黙の (自動的な) エンティティー分解とグラフ拡張の手法を使用して、さまざまな文書にあるエンティティーと関係の接続グラフを自動的に作成します。作成される Knowledge Graph に加え、Knowledge Graph 分析サービスによって、結果を返すための関連性をランク付ける手法が追加されます。

![Knowledge Graph のプロセス](images/knowledge-graph.png)

このナレッジの接続グラフとランク付け手法によって、次のものが得られます。

-  ファジー検索トークン、タイプ情報 (オプション)、およびコンテキスト (オプション) を使用してあいまいさを除去したエンティティー。例: `Apple` のコンテキストで `Steve` を検索すると `Steve Jobs` がトップで返されるのに対し、`Microsoft` のコンテキストで `Steve` を検索すると `Steve Ballmer` がトップで返されます。
-  ファジー検索トークンとコンテキスト (オプション) の入力によって関連性がランク付けされた関係。関連性のランク付けはグラフのグローバル・プロパティーを使用して、より具体的な情報を明示します。例: `health` のコンテキストで `Obama` の関係を検索すると、`Affordable Care Act` (医療保険制度改革法) とその関連エンティティーが返されます。
-  ナレッジの接続グラフでエンティティーと関係を照会することによる、文書間における推論と集約。このような照会の例として、X さんはどのように Y さんと関連付けられているのか、従業員 X のデータ・アクセス・パターンは標準とどの程度異なっているのか、X さんの影響が及ぶ範囲はどれぐらいか、などがあります。

## サービス要件

ベータ版では、Knowledge Graph 機能とそれに関連する方法は、**Advanced**プランでサブスクライブされるサービス・インスタンスでのみ使用できます。

## コレクションの要件

{{site.data.keyword.discoveryshort}} は、取り込んだ文書から抽出したエンティティーと関係を使用して Knowledge Graph を作成した上でエンティティーと関係を照会できるようにします。

**注:** Knowledge Graph はプライベート・データ・コレクションにのみ使用でき、{{site.data.keyword.discoverynewsshort}} で使用するようには設計されていません。

Knowledge Graph を使用するには、コレクションが、以下に示す特定の条件を満たすように構成されている必要があります。

-  Knowledge Graph を使用するフィールドで `entities` エンリッチメントと `relations` エンリッチメントの両方を指定する必要があり、各エンリッチメントは同じカスタム・モデルを使用しなければなりません。パブリック・モデルが必要な場合は、カスタム・モデル `model="en-news"` のフォームでそれを指定する必要があります。

-  `relations` エンリッチメントは、次のように指定してください。
   ```json
   "relations": {
     "model": "en-news"
   }
   ```
   {: codeblock}

-  `entities` エンリッチメントは次のように指定し、さらに `mentions`、`mentions_types`、および `sentence_locations` の各パラメーターを指定してください。
   ```json
   "entities": {
     "mentions": true,
     "mention_types": true,
     "sentence_locations": true,
     "model": "en-news"
    }
    ```
    {: codeblock}

   上記のほか、オプションの `enrichments` オプション (`"sentiment": true` など) は、必要に応じて指定できます。

これらのオプションは {{site.data.keyword.discoveryshort}} ツールを使用して追加できず、API を使用してカスタム構成をアップロードしなければなりません。パブリック・モデルのナレッジ・グラフでコレクションを使用するために `text` フィールドをエンリッチするよう変更したデフォルト構成のコピーは、[こちら](https://raw.githubusercontent.com/watson-developer-cloud/doc-tutorial-downloads/master/discovery/config-default-kg.json)にあります。

{{site.data.keyword.discoveryshort}} サービス・インスタンスを作成したあと、以下のようにカスタム構成を作成します。

1. 次のコマンドを発行して、`my-first-environment` という名前の環境を作成します。`{username}` と `{password}` は、ご使用のサービス資格情報に置き換えてください。

   ```bash
   curl -X POST -u "{username}":"{password}" -H "Content-Type: application/json" -d '{ "name":"my-first-environment", "description":"exploring environments"}' "api/v1/environments?version=2017-11-07"
   ```
   {: pre}

   API によって、環境 ID、環境状況、環境が使用しているストレージ量などの情報が返されます。

   返された `{environment_id}` が必要となります。

1. 次に、カスタム構成を作成します。この手順では、[こちら](https://raw.githubusercontent.com/watson-developer-cloud/doc-tutorial-downloads/master/discovery/config-default-kg.json) で見つかった構成をアップロードしていることを前提としています。独自のカスタム構成を作成する場合は、[構成リファレンス](/docs/services/discovery/custom-config.html) を参照してください。

   ```bash
   curl -X PUT -u "{username}":"{password}" -H "Content-Type: application/json" -d config-default-kg.json "https://gateway.watsonplatform.net/discovery/api/v1/environments/{environment_id}/configurations?version=2017-11-07"
   ```
   {: pre}

1. カスタム構成がアップロードされると、作成する任意のコレクションでそのカスタム構成を使用でき、そのカスタム構成が指定されている限り、文書をアップロードする任意のメソッドが使用できます。コレクションの作成と文書のアップロードに慣れていない場合は、[ツールの概要](/docs/services/discovery/getting-started-tool.html) を参照してください。[ステップ 3](/docs/services/discovery/getting-started-tool.html#create-custom-configuration) に進んだら、新規構成を作成せずに、「Knowledge Graph の構成 (Knowledge Graph Configuration)」を選択してください。
## エンティティー照会
{: #entities}

Knowledge Graph のベータ版では、エンティティーの照会は、コンテキスト・ベースのエンティティーのあいまいさ除去をサポートしてます。提供されたエンティティー・テキストおよびオプションのコンテキスト・テキストに基づいて、あいまいさ除去は固有のエンティティーを識別し、コンテキスト情報に基づいてランク付けしたエンティティーのリストを返します。Knowledge Graph のエンティティー照会は、`JSON` オブジェクトを `v1/environments/{environment_id}/collections/{collection_id}/query_entities` エンドポイントに `POST` することで実行されます。
エンティティーの照会は、API を使用するか、{{site.data.keyword.discoveryshort}} ツールによって行うことができます。ツールの情報については、[Discovery ツールを使用した Knowledge Graph の照会](/docs/services/discovery/building-kg.html#querying-kg) を参照してください。

Knowledge Graph エンティティー照会の JSON オブジェクトは、次のような形式です。

```json
{
  "feature": "disambiguate",
  "entity": {
    "text": "Steve",
    "type": "Person"
  },
  "context": {
    "text": "iphone"
  },
  "count": 10
}
```
{: codeblock}

-  `"feature": string` _required_ - 使用するエンティティー照会機能であり、`disambiguate` でなければなりません。
-  `"entity": {}` _required_ - あいまいさを除去するためのエンティティー情報を含むオブジェクト。
   -  `"text": string` _required_ - あいまいさが除去されるエンティティー・テキスト。
   -  `"type": string` _optional_ - あいまいさを除去するオプションのエンティティー・タイプ。指定しない場合は、すべてのタイプが対象となります。
-  `"context": {}` _optional_ - あいまいさ除去のためのコンテキスト要件を含むオプションのオブジェクト。
   -  `"text": string` _optional_ - 照会されたエンティティーのコンテキストを提供し、その関連性に基づいてランク付けするためのエンティティー・テキスト。例えば、England の都市 London を検索する場合、照会は `England` というコンテキストを使用して `London` を検索します。入力は、名前の一部でも、関連するエンティティー用語を含む大きな文節でもかまいません。複数の用語を一緒に渡すことができます。
-  `"count": INT` _optional_ - あいまいさを除去したエンティティーの返却数。デフォルトは `10` です。最大は `1000` です。

照会は結果を次の形式で返します。

```json
{
  "entities": [
    {
      "text": "Steve Jobs",
      "type": "PERSON"
    },
    {
      "text": "Steve Wozniak",
      "type": "PERSON"
    }
  ]
}
```
{: codeblock}

一致が見つからなかった場合は、次の JSON オブジェクトが返されます。

```json
{
  "entities": []
}
```
{: codeblock}

## 関係照会
{: #relations}

Knowledge Graph の関係照会は、最も関連性の高い関係の検索をサポートしています。これには、入力エンティティーに基づいて、エンティティーの暗黙のあいまいさ除去、コンテキスト・ベースの関係、関連性スコアと言及カウントによるソート、タイプと文書 id によるフィルタリングが使用されます。

関係の照会は、API を使用するか、{{site.data.keyword.discoveryshort}} ツールによって行うことができます。ツールの情報については、[Discovery ツールを使用した Knowledge Graph の照会](/docs/services/discovery/building-kg.html#querying-kg) を参照してください。

Knowledge Graph のエンティティー照会は、`JSON` オブジェクトを `v1/environments/{environment_id}/collections/{collection_id}/query_relations` エンドポイントに `POST` することで実行されます。
Knowledge Graph 関係照会の JSON オブジェクトは、次のような形式です。

```json
{
  "entities": [
    {
      "text": "Steve Jobs",
      "type": "PERSON",
      "exact": true
    }
  ],
  "context": {
    "text": "iphone"
  },
  "sort": "score",
  "filter": {
    "relation_types": {
      "exclude": ["colocation"],
      "include": ["locatedAt", "employedBy", "managerOf", "founderOf"]
    },
    "entity_types": {
      "exclude": ["EVENT"],
      "include": ["PERSON", "GPE", "ORGANIZATION"]
    },
    "document_ids": ["b95df4c1-d00f-4771-abb2-a52baea0444a", "ad340635-bf3e-47a5-bea5-5e778f600c32"]
  },
  "count": 10
}
```
{: codeblock}

-  `"entities": []` _required_ - 関係が照会されるエンティティーを含む配列。エンティティー・オブジェクトが 1 つしか定義されていない場合は、近隣の関係がすべて返されます。複数のエンティティー・オブジェクトが定義されている場合は、相互にペアワイズの関係が返されます。相互にペアワイズの関係は、近隣のすべてのエンティティーを含む関係の代わりに、入力エンティティー間の直接の関係を返します。各エンティティー・オブジェクトには以下が含まれます。
   -  `"text": string` _required_ - エンティティー・テキスト。
   -  `"type": string` _optional_ - オプションのエンティティー・タイプ。`"exact"` が `true` の場合、このフィールドは必須です。
   -  `"exact": boolean` _optional_ - `false` の場合、暗黙のあいまいさ除去が実行されます。暗黙のあいまいさ除去は、各入力エンティティー・オブジェクトに、あいまいさを除去した最上位のエンティティーを使用します。デフォルトは `false` です。
-  `"context": {}` _optional_ - コンテキスト要件を含むオプションのオブジェクト。
   -  `"text": string` _optional_ - 照会されたエンティティーのコンテキストを提供し、その関連性に基づいてランク付けするためのエンティティー・テキスト。例えば、England の都市 London を検索する場合、照会は `England` というコンテキストを使用して `London` を検索します。入力は、名前の一部でも、関連するエンティティー用語を含む大きな文節でもかまいません。複数の用語を一緒に渡すことができます。
-  `"sort": string` _optional_ - 関係のソート方法であり、`score` または `frequency` のいずれかです。デフォルトは `score` です。`score` は、入力エンティティーに対する関係と近隣の関連性、およびコンテキストに対する関連性 (コンテキストが提供されている場合) に基づいています。`frequency` は、各関係が識別された固有の回数です。
-  `"filter": {}` _optional_ - この照会のフィルター処理に使用する関係のタイプ、エンティティー・タイプ、特定の文書を含むオブジェクト。デフォルトでは、何も除外されません。
   -  `"relation_types": {}` _optional_ フィルター処理する関係タイプのリスト。
      -  `"exclude": []` _optional_ 照会から除外する関係タイプを含むコンマ区切りリスト。
      -  `"include": []` _optional_ 明示的に照会に含める関係タイプを含むコンマ区切りリスト。指定した場合、他のすべてのタイプは除外とみなされます。
   -  `"entity_types": {}` _optional_ 近隣をフィルター処理するためのエンティティー・タイプのリスト。新しい近隣は返されないので、複数エンティティー入力には適用されません。
      -  `"exclude": []` _optional_ 照会から除外するエンティティー・タイプを含むコンマ区切りリスト。
      -  `"include": []` _optional_ 明示的に照会に含めるエンティティー・タイプを含むコンマ区切りリスト。指定した場合、他のすべてのタイプは除外とみなされます。
   -  `"document_ids": []` _optional_ 関係照会を実行する文書を含むコンマ区切りリスト。
-  `"count": INT` _optional_ 返す関係の数。デフォルトは `10` です。最大は `1000` です。

照会は結果を次の形式で返します。

```json
{
  "relations": [
    {
      "type": "FOUNDEROF",
      "frequency": 7,
      "arguments": [
        {
          "entities": [
            {
              "type": "PERSON",
              "text": "Steve Jobs"
            }
          ]
        },
        {
          "entities": [
            {
              "type": "ORGANIZATION",
              "text": "Apple"
            }
          ]
        }
      ]
    }
  ]
}
```
{: codeblock}

関係配列内の各オブジェクトに、エンティティー配列のペア (最初がソースまたはサブジェクト、2 番目が関係のターゲットまたはオブジェクト) を含む引数配列が返されます。

一致が見つからない場合は、次の JSON オブジェクトが返されます。

```json
{
  "relations": []
}
```
{: codeblock}

## Discovery ツールを使用した Knowledge Graph の照会
{: #querying-kg}

[**Advanced**](/docs/services/discovery/building-kg.html#service-requirements) プランでサブスクライブされたサービス・インスタンスでは、
{{site.data.keyword.discoveryshort}} ツールを使用して Knowledge Graph でプライベート・コレクションを照会できます。

{{site.data.keyword.discoveryshort}} ツールで Knowledge Graph 照会にアクセスするには、次のようにします。

1.  ![照会アイコン](images/search_icon.svg)<!-- {width="20" height="20" style="padding-left:5px;padding-right:5px;"} --> をクリックして、照会ページを開きます。
1.  コレクションを選択して、**「開始 (Get started)」**をクリックします。
1.  **「照会の作成 (Build queries)** 画面で**「ナレッジ・グラフ (Knowledge graph)」**タブを選択し、**「エンティティー」**または**「関係」**を選択します。
