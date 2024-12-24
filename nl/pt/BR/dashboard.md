---

copyright:
  years: 2015, 2018
lastupdated: "2018-06-25"

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

# Visualizando métricas e melhorando os resultados da consulta com o painel Desempenho
{: #performance-dashboard}

O painel Desempenho no conjunto de ferramentas do {{site.data.keyword.discoveryshort}} pode ser usado para visualizar métricas de consulta, bem como melhorar os resultados da consulta, incluindo a relevância da consulta.

É possível acessar o painel Desempenho, clicando no ícone **Visualizar métricas de dados** à esquerda. O painel não está disponível nos ambientes Premium ou Dedicado.

Há duas opções para melhorar os resultados da consulta de língua natural:
- [Corrigir consultas sem resultados incluindo mais dados](/docs/services/discovery?topic=discovery-performance-dashboard#addmore)
- [Trazer resultados relevantes para a parte superior treinando seus dados](/docs/services/discovery?topic=discovery-performance-dashboard#traindata)

É possível visualizar as métricas de dados na [visão geral da consulta](/docs/services/discovery?topic=discovery-performance-dashboard#overview). 

## Corrigir consultas sem resultados incluindo mais dados
{: #addmore}

Nesta seção do painel, é possível revisar as consultas que retornaram resultados zero e incluir mais dados para que a consulta retorne resultados no futuro. Clique no botão **Visualizar todos e incluir dados** para começar. 

## Trazer resultados relevantes para a parte superior treinando seus dados
{: #traindata}

Nesta seção, é possível treinar suas coleções para melhorar a relevância dos resultados da consulta de língua natural. Clique no botão **Visualizar todos e executar treinamento de relevância** para começar. Em seguida, veja [Incluindo consultas e classificando a relevância de resultados](/docs/services/discovery?topic=discovery-improving-result-relevance-with-the-tooling#results) para obter instruções.

Para obter mais informações sobre os requisitos do treinamento e as opções, veja [Melhorando a relevância de resultados com o conjunto de ferramentas](/docs/services/discovery?topic=discovery-improving-result-relevance-with-the-tooling#improving-result-relevance-with-the-tooling).

## Visão Geral da Consulta
{: #overview}

A seção Visão Geral da Consulta é exibida:
- O número total de consultas feitas pelos usuários
- A porcentagem de consultas com um ou mais resultados clicados
- A porcentagem de consultas sem resultados clicados
- A porcentagem de consultas sem resultados retornados
- Um gráfico que exibe esses resultados ao longo do tempo, de modo que seja possível rastrear como a inclusão de mais dados e o treinamento de relevância estão melhorando o desempenho

Esses resultados são reunidos usando a API de Eventos e feedback. Veja a [Referência da API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/discovery#create-event) para obter mais informações.
