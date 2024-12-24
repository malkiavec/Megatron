---
copyright:
  years: 2015, 2018
lastupdated: "2018-12-19"

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

# API 시작하기
{: #gs-api}

이 짧은 튜토리얼에서는 {{site.data.keyword.discoveryshort}} API를 소개하고 개별 데이터 콜렉션 작성 및 검색 프로세스를 진행합니다.
{: shortdesc}

{{site.data.keyword.discoveryshort}} 도구 사용을 선호하는 경우 [시작하기](/docs/services/discovery?topic=discovery-getting-started#getting-started)를 참조하십시오.
{: tip}

## 시작하기 전에
{: #before-you-begin-api}

- 서비스 인스턴스 작성:
    1.  {{site.data.keyword.cloud_notm}} 카탈로그에서 [{{site.data.keyword.discoveryshort}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/catalog/services/discovery) 페이지로 이동하십시오.
        다른 리소스 그룹을 선택하지 않는 경우 서비스 인스턴스는 **기본** 리소스 그룹에 작성되고 나중에 변경할 *수 없습니다*. 이 그룹은 서비스를 시도하는 목적에 충분합니다.
        더욱 강력한 사용을 위해 인스턴스를 작성하는 경우 [리소스 그룹 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/docs/resources/bestpractice_rgs.html#bp_resourcegroups){: new_window}에 대해 자세히 알아보십시오.
    1.  무료 {{site.data.keyword.cloud_notm}} 계정을 등록하거나 로그인하십시오.
    1.  **작성**을 클릭하십시오. {{site.data.keyword.discoveryshort}} 서비스 인스턴스를 작성하면 서비스의 목록으로 이동합니다. 
- 인증할 인증 정보를 서비스 인스턴스에 복사:
    1.  [리소스 목록](https://{DomainName}/dashboard/)에서 {{site.data.keyword.discoveryshort}} 서비스 인스턴스를 클릭하여 {{site.data.keyword.discoveryshort}} 서비스 대시보드 페이지로 이동하십시오.
    1.  **관리** 페이지에서 **인증 정보 표시**를 클릭하여 인증 정보를 확인하십시오.
    1.  `API 키` 및 `URL` 값을 복사하십시오.

            일부 인스턴스에서는 기본 인증을 제공하여 인증합니다. 인증 정보의 `username` 및 `password`가 표시되면 이 튜토리얼의 예에서 `"apikey:{apikey}"` 대신 이 값을 사용하십시오.
        {: tip}

## 단계 1: 환경 작성
{: #create-an-environment}

bash 쉘 또는 이와 동등한 환경(예: `curl` 애플리케이션이 설치된 Cygwin)에서 `POST /v1/environments` 메소드를 사용하여 환경을 작성하십시오. 환경을 모든 문서 상자를 저장하는 창고로 간주하십시오.

이 튜토리얼에서는 API키를 사용하여 인증합니다. 프로덕션 사용을 위해서는 API 키 [우수 사례](/docs/services/watson/apikey-bp.html#api-bp)를 검토해야 합니다.
{: important}

1.  다음 명령을 실행하여 `my-first-environment`라는 환경을 작성하십시오. `{apikey}` 및 `{url}`을 이전에 복사한 API 키와 URL로 대체하십시오.

    ```bash
    curl -X POST -u "apikey:{apikey}" -H "Content-Type: application/json" -d "{\"name\":\"my-first-environment\", \"description\":\"exploring environments\"}" "{url}/v1/environments?version=2018-12-03"
    ```
    {: pre}

    API가 환경 ID, 환경 상태 및 환경에서 사용 중인 스토리지의 크기와 같은 정보를 리턴합니다.

1.  `active`의 상태가 표시될 때까지 주기적으로 환경 상태를 확인하십시오.

    환경 상태를 검색하려면 `GET /v1/environments/{environment_id}` 메소드에 대한 호출을 실행하십시오. `{apikey}`, `{url}` 및 `{environment_id}`를 사용자 정보로 대체하십시오. 

    ```bash
    curl -u "apikey:{apikey}" "{url}/v1/environments/{environment_id}?version=2018-12-03"
    ```
    {: pre}

    콜렉션을 작성하기 전에 상태는 `active`여야 합니다.

## 단계 2: 콜렉션 작성
{: #create-a-collection-api}

환경이 준비되었으므로 콜렉션을 작성할 수 있습니다. 콜렉션을 사용자의 환경에 문서를 저장하는 상자로 간주하십시오.

1.  먼저 기본 구성 ID가 필요합니다. 기본 `configuration_id`를 찾으려면 `GET /v1/environments/{environment_id}/configurations` 메소드를 사용하십시오. `{apikey}`, `{url}` 및 `{environment_id}`를 사용자 정보로 대체하십시오.
    ```bash
      curl -u "apikey:{apikey}" "{url}/v1/environments/{environment_id}/configurations?version=2018-12-03"
    ```
    {: pre}
1.  `POST /v1/environments/{environment_id}/collections` 메소드를 사용하여 **my-first-collection**이라는 콜렉션을 작성하십시오. `{apikey}`, `{url}`, `{environment_id}` 및 `{configuration_id}`를 사용자 정보로 대체하십시오.
    ```bash
    curl -X POST -u "apikey:{apikey}" -H "Content-Type: application/json" -d "{\"name\": \"my-first-collection\", \"description\": \"exploring collections\", \"configuration_id\":\"{configuration_id}\" , \"language": \"en_us\"}" "{url}/v1/environments/{environment_id}/collections?version=2018-12-03"
    ```
    {: pre}
    API가 콜렉션 ID, 콜렉션 상태 및 콜렉션에서 사용 중인 스토리지의 크기와 같은 정보를 리턴합니다.
1.  `active`의 상태가 표시될 때까지 주기적으로 콜렉션 상태를 확인하십시오.

    콜렉션의 상태를 검색하려면 `GET /v1/environments/{environment_id}/collections/{collection_id}` 메소드에 대한 호출을 실행하십시오.  다시 한 번, `{apikey}`, `{url}`, `{environment_id}` 및 `{configuration_id}`를 사용자 정보로 대체하십시오. 

    ```bash
    curl -u "apikey:{apikey}" "{url}/v1/environments/{environment_id}/collections/{collection_id}?version=2018-12-03"
    ```
    {: pre}

## 단계 3: 샘플 문서 다운로드
{: #download-sample-documents}

<a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/discovery/test-doc1.html" download>test-doc1.html <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/discovery/test-doc2.html" download>test-doc2.html <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/discovery/test-doc3.html" download>test-doc3.html <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘"></a> 및 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/discovery/test-doc4.html" download>test-doc4.html <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘"></a>의 샘플 문서를 다운로드하십시오.

일부 브라우저에서는 앞의 링크가 로컬에 저장되는 대신 새 창에서 열립니다. 이 경우, 브라우저의 `File` 메뉴에서 `Save As`를 선택하여 파일 사본을 저장하십시오.
{: tip}

## 단계 4: 문서 업로드
{: #upload-the-documents}

1.  이제 예제 문서를 콜렉션에 추가하십시오. 이 예에서는 **test-doc1.html** 문서를 콜렉션에 업로드합니다. `{apikey}`, `{url}`, `{environment_id}` 및 `{collection_id}`를 사용자 정보로 대체하십시오. `3test-doc1.html` 파일을 저장한 위치를 가리키도록 샘플 문서의 위치를 수정하십시오.
    - `POST /v1/environments/{environment_id}/collections/{collection_id}/documents` 메소드를 사용하십시오.

        ```bash
        curl -X POST -u "apikey:{apikey}" -F "file=@test-doc1.html" "{url}/v1/environments/{environment_id}/collections/{collection_id}/documents?version=2018-12-03"
        ```
        {: pre}

        또는 [API 참조 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/discovery){: new_window}에 나열된 SDK 중 하나를 사용하십시오.
    - Java:
      ```java
      Discovery discovery = new Discovery("2018-12-03");
      discovery.setEndPoint("{url}");

      IamOptions options = new IamOptions.Builder()
        .apiKey("{apikey}")
        .build();
      discovery.setIamCredentials(options);

      String environmentId = "{environment_id}";
      String collectionId = "{collection_id}";
      String documentJson = "{\"field\":\"value\"}";
      InputStream documentStream = new ByteArrayInputStream(documentJson.getBytes());

      CreateDocumentRequest.Builder builder = new CreateDocumentRequest.Builder(environmentId, collectionId);
      builder.inputStream(documentStream, HttpMediaType.APPLICATION_JSON);
      CreateDocumentResponse createResponse = discovery.createDocument(builder.build()).execute();
      ```
      {: codeblock}
    - Python:
      ```python
      import sys
      import os
      import json
      from watson_developer_cloud import DiscoveryV1

      discovery = DiscoveryV1(
          version='2018-12-03',
          iam_apikey='{apikey}',
          url='{url}'
      )
      with open((os.path.join(os.getcwd(), '{path_element}', '{filename}' as fileinfo:
        add_doc = discovery.add_document('{environment_id}', '{collection_id}', file_info=fileinfo)
      print(json.dumps(add_doc, indent=2))
      ```
      {: codeblock}

    - Node.js:
      ```javascript
      var DiscoveryV1 = require('watson-developer-cloud/discovery/v1');
      var fs = require('fs');

      var discovery = new DiscoveryV1({
        version_date: '2018-12-03',
        iam_apikey: '{apikey}',
        url: '{url}'
      });

      var file = fs.readFileSync('{/path/to/file}');

      discovery.addDocument({ environment_id: '{environment_id}', collection_id: '{collection_id}', file: file },
      function(error, data) {
        console.log(JSON.stringify(data, null, 2));
        }
      );
      ```
      {: codeblock}

1.  다른 세 가지 샘플 파일마다 이 프로세스를 반복하십시오.

## 단계 5: 콜렉션 조회
{: #query-your-collection}

마지막으로 `GET /v1/environments/{environment_id}/collections/{collection_id}/query` 메소드를 사용하여 문서의 콜렉션을 검색하십시오.

다음 예에서는 **IBM**이라고 하는 모든 엔티티를 리턴합니다. `{apikey}`, `{environment_id}` 및 `{collection_id}`를 사용자 정보로 대체하십시오.

```bash
curl -u "apikey:{apikey}" "{url}/v1/environments/{environment_id}/collections/{collection_id}/query?version=2018-12-03&query=enriched_text.entities.text:IBM"
```
{: pre}

## 다음 단계
{: #next-steps-api}

작성한 환경 및 콜렉션에서 문서 조회를 완료했습니다. 이제 더 많은 문서와 인리치먼트를 추가하여 콜렉션 사용자 정의와 변환 설정 사용자 정의를 시작할 수 있습니다.

- [API 참조 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/discovery){: new_window}에서 API 정보 읽기
- 서비스 [구성](/docs/services/discovery?topic=discovery-configservice#configservice)
- [IAM을 사용하여 인증 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/docs/services/watson/getting-started-iam.html#iam){: new_window}에 대해 자세히 알아보기
