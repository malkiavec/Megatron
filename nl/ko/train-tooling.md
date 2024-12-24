---

copyright:
  years: 2015, 2017
lastupdated: "2017-12-05"

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

# 도구로 결과 관련성 향상

자연어 조회 결과의 관련성은 도구를 사용하여 {{site.data.keyword.discoveryfull}} 서비스에서 향상될 수 있습니다. {{site.data.keyword.discoveryshort}} 도구 또는 {{site.data.keyword.discoveryshort}} API를 사용하여 개인용 콜렉션을 훈련시킬 수 있습니다. API 사용을 선호하는 경우 [API로 조회 결과의 관련성 향상](/docs/services/discovery/train.html)을 참조하십시오.
{: shortdesc}

관련성 훈련은 선택적입니다. 조회의 결과가 사용자의 요구사항을 충족하는 경우 추가 훈련이 필요하지 않습니다. 훈련에 대한 유스 케이스 빌드의 개요는 블로그 포스트 [How to get the most out of Relevancy Training ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.ibm.com/dwblog/2017/get-relevancy-training/){: new_window}을 참조하십시오. 

Watson을 훈련시키려면 다음을 수행해야 합니다. 

  -   사용자가 입력하는 조회를 나타내는 조회 예제를 제공합니다. 
  -   각 조회의 결과가 관련되거나 관련되지 않음을 표시하는 등급을 제공합니다. 

Watson에 충분한 훈련 입력이 있으면 각 조회에 대해 올바르고 잘못된 결과에 대해 사용자가 제공한 정보가 콜렉션에 대해 학습하는 데 사용됩니다. Watson은 단지 기억하지 못할 뿐이며, 개별 조회에 대한 특정 정보에서 학습하고 발견한 패턴을 모든 새 조회에 적용합니다. 컨텐츠 및 질문에서 신호를 찾는 기계 학습 Watson 기술을 사용하여 이를 수행할 수 있습니다. 훈련이 적용된 후 {{site.data.keyword.discoveryshort}}는 맨 위에 가장 관련성이 높은 결과를 표시하도록 조회 결과를 다시 정렬합니다. 더 많은 훈련 데이터를 추가할수록 {{site.data.keyword.discoveryshort}}는 조회 결과의 순위 지정 시 좀 더 정확해져야 합니다. 

훈련은 {{site.data.keyword.discoveryshort}}가 등급 적용을 시작하도록 다음 **최소** 요구사항을 충족해야 합니다. 

  - 최소 49개 이상의 조회를 훈련해야 합니다. Watson은 훈련을 위해 추가 조회가 필요한 경우 사용자에게 피드백을 제공합니다. 
  - `Relevant` 및 `Not relevant` 등급을 결과에 적용해야 합니다. `Relevant` 문서만 등급을 지정하면 필요한 데이터를 제공하지 않습니다. 

**참고:** 관련성 훈련은 수행되기 전에 특정 훈련 데이터 요구사항이 필요합니다. 서비스는 요구사항이 충족되는지와 모든 변경사항에 따라 자체적으로 자동 업데이트가 수행되는지 여부를 판별하기 위해 주기적으로 훈련 데이터를 확인합니다. 

**참고:** 관련성 훈련은 현재 개인용 콜렉션의 자연어 조회에만 적용됩니다. 구조화된 {{site.data.keyword.discoveryshort}} 조회 언어 조회와 함께 사용할 수 없습니다. {{site.data.keyword.discoveryshort}} 조회 언어에 대해 좀 더 알아보려면 [조회 개념](/docs/services/discovery/using.html)을 참조하십시오.

**참고:** 환경당 최대 네 개의 훈련된 콜렉션이 있습니다.   

## 조회 추가 및 결과의 관련성 등급 지정

훈련은 자연어 조회, 조회의 결과 및 해당 결과에 적용하는 등급으로 구성됩니다. 

1.  {{site.data.keyword.discoveryshort}} 도구의 **조회 빌드** 화면에서 콜렉션에 대한 훈련 페이지에 도달할 수 있습니다. 오른쪽 상단에 있는 **결과를 향상시키도록 Watson 훈련**을 클릭하십시오. 훈련을 시작하기 위해 **조회 빌드** 화면에 조회를 입력할 필요가 없습니다. 
1.  **Watson 훈련** 화면에서 **자연어 추가**를 클릭하고(예: "IBM Watson in healthcare") 이를 추가하십시오. 사용자가 요청한 방식으로 조회가 작성되는지 확인하십시오. 또한 조회와 원하는 답변 사이에 일부 용어 겹침을 포함하여 훈련 조회를 작성해야 합니다. 이를 통해 자연어 조회가 실행될 때 초기 결과가 향상됩니다. 관련성 훈련은 자연어 조회만 사용하므로 {{site.data.keyword.discoveryshort}} 조회 언어로 작성된 조회를 입력하지 마십시오. 
1.  조회의 결과를 보려면 옆에 있는 **결과 등급 지정** 단추를 클릭하십시오. 결과가 충분하지 않다고 간주되면 조회를 다시 작성하거나 **데이터 관리** 화면을 통해 더 많은 문서를 이 콜렉션에 추가하십시오. 
1.  `Relevant` 또는 `Not relevant`로 결과 등급 지정을 시작하십시오. 이를 수행한 후 **조회로 돌아가기**를 클릭하십시오. {{site.data.keyword.discoveryshort}} 도구에서 `Relevant`에는 `10`의 스코어가 있고 `Not relevant`에는 `0`의 스코어가 있습니다. API를 사용하여 이 콜렉션에 대한 결과의 등급 지정을 이미 시작했으며 다른 스코어링 스케일을 사용한 경우 이 문제를 해결하는 옵션과 함께 경고가 표시됩니다.
    화면의 맨 위에서 Watson은 사용자를 위해 훈련 상태를 추적하고 결과를 향상시키기 위해 수행할 수 있는 작업에 대한 팁을 제공합니다. "등급에 더 많은 다양성 추가" 는 `Relevant` 및 `Not relevant` 등급을 모두 사용해야 함을 의미합니다. 요구사항을 충족하면 훈련이 주기적으로 업데이트를 시작합니다. 업데이트를 시작한 후 완료하는 데 30분 미만이 소요되며 Watson 업데이트 시 작업을 계속 수행할 수 있습니다. 
1.  계속해서 조회를 추가하고 결과의 등급을 지정하십시오. 

언제든지 기본 **조회 빌드** 화면으로 돌아가려면 왼쪽 상단에 있는 **조회 빌드**를 클릭하십시오.
{: tip}
**데이터 관리** 화면으로 돌아가려면 오른쪽 상단에 있는 콜렉션의 이름을 클릭하십시오.
{: tip}

콜렉션의 모든 데이터를 동시에 삭제하려면 API를 통해 수행해야 합니다. 자세한 정보는 [콜렉션의 모든 훈련 데이터 삭제](http://www.ibm.com/watson/developercloud/discovery/api/v1/#delete-all-training-data)를 참조하십시오. API를 통한 훈련에 대한 자세한 정보는 [API로 조회 결과의 관련성 향상](/docs/services/discovery/train.html)을 참조하십시오.

## 결과의 관련성 테스트 및 반복

결과의 등급 지정을 완료하고 Watson이 훈련을 적용한 후 조회 결과가 향상되었는지 확인하기 위해 테스트해야 합니다. 이를 수행하려면 훈련 조회에 관련된(그러나 동일하지 않음) 테스트 조회를 실행하십시오. 테스트 조회의 결과가 향상되었는지 확인하십시오. 

테스트 후 추가로 결과를 향상시키려는 경우 다음을 수행할 수 있습니다. 
- 더 많은 문서를 콜렉션에 추가하십시오. 
- 더 많은 훈련 조회를 추가하십시오. 
- 더 많은 결과의 등급을 지정하여 `Relevant` 및 `Not relevant` 등급을 모두 사용하십시오. 

추가적인 훈련 지시사항은 [관련성 훈련 팁](/docs/services/discovery/train-tips.html#relevancy-tips)을 참조하십시오.

## 신뢰도 스코어
{: #confidence}

훈련된 콜렉션은 자연어 조회의 결과에 `confidence` 스코어를 리턴합니다. `confidence` 숫자는 훈련된 모델과 비교하여 평가할 결과가 얼마나 관련성이 있다고 추정되는지를 기반으로 계산됩니다. `confidence` 스코어는 `score`와 동일하지 **않습니다**. 신뢰도 스코어의 임계값 결정에 대한 자세한 정보는 [How to select a threshold for acting using confidence scores ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.ibm.com/watson/blog/2016/06/23/how-to-select-a-threshold-for-acting-using-confidence-scores/)를 참조하십시오. `score`는 상대 계산이므로 절대 임계값을 설정하는 데 사용하면 안 됩니다. 

`confidence`의 범위는 0.0 - 1.0입니다. 숫자가 클수록 문서 관련성이 높아집니다. 

`confidence` 스코어는 각 문서의 `result_metadata` 아래의 조회 결과에서 찾을 수 있습니다. 

```json
    "results": [
        {
            "id": "eea16dfd5fe6139a25324e7481a32f89_13",
            "result_metadata": {
                "confidence": 0.5893963975910735,
                "score": 0.5006834
            },
```
