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

# Affichage de métriques et amélioration des résultats de requête avec le tableau de bord Performance
{: #performance-dashboard}

Le tableau de bord Performance des outils {{site.data.keyword.discoveryshort}} peut être utilisé pour afficher des métriques de requête, ainsi que pour améliorer les résultats de requête, notamment la pertinence de requête.

Vous pouvez accéder au tableau de bord Performance en cliquant sur l'icône **View data metrics** située sur la gauche. Le tableau de bord n'est pas disponible dans les environnements Premium ou Dedicated.

Deux options permettent d'améliorer les résultats de requête en langage naturel :
- [Fix queries with no results by adding more data](/docs/services/discovery?topic=discovery-performance-dashboard#addmore)
- [Bring relevant results to the top by training your data](/docs/services/discovery?topic=discovery-performance-dashboard#traindata)

Vous pouvez afficher les métriques de données dans la [présentation des requêtes](/docs/services/discovery?topic=discovery-performance-dashboard#overview). 

## Corriger les requêtes sans résultat en ajoutant davantage de données (Fix queries with no results by adding more data)
{: #addmore}

Dans cette section du tableau de bord, vous pouvez examiner des requête qui n'ont renvoyé aucun résultat et ajouter des données supplémentaires afin que la requête renvoie des résultats à l'avenir. Cliquez sur le bouton **View all and add data** pour commencer. 

## Faire apparaître les résultats pertinents en premier via l'entraînement de vos données (Bring relevant results to the top by training your data)
{: #traindata}

Dans cette section, vous pouvez entraîner vos collections pour améliorer le niveau de pertinence des résultats de requête en langage naturel. Cliquez sur le bouton **View all and perform relevancy training** pour commencer. Consultez ensuite [Ajout de requêtes et évaluation de la pertinence des résultats](/docs/services/discovery?topic=discovery-improving-result-relevance-with-the-tooling#results) pour des instructions.

Pour plus d'informations sur les options et exigences en matière d'apprentissage, voir [Amélioration de la pertinence des résultats à l'aide des outils](/docs/services/discovery?topic=discovery-improving-result-relevance-with-the-tooling#improving-result-relevance-with-the-tooling).

## Présentation des requêtes (Query overview)
{: #overview}

La section de présentation des requêtes affiche :
- Le nombre total de requêtes effectuées par des utilisateurs
- Le pourcentage des requêtes avec un ou plusieurs résultats cliqués
- Le pourcentage des requêtes sans résultat cliqué
- Le pourcentage des requêtes sans résultat renvoyé
- Un diagramme représentant ces résultats dans le temps, afin de vous permettre de suivre la façon dont l'ajout de données supplémentaires et l'entraînement de pertinence améliorent les performances.

Ces résultats sont collectés à l'aide de l'API Events and Feedback. Voir [API reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/discovery#create-event) pour plus d'informations.
