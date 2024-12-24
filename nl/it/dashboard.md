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

# Visualizzazione delle metriche e miglioramento dei risultati della query con il dashboard Performance
{: #performance-dashboard}

Il dashboard Performance nella strumentazione {{site.data.keyword.discoveryshort}} può essere utilizzato per visualizzare le metriche della query, nonché per migliorare i risultati della query, inclusa la rilevanza della query.

Puoi accedere al dashboard Performance facendo clic sull'icona **View data metrics** sulla sinistra. Il dashboard non è disponibile in ambienti Premium o Dedicato.

Esistono due opzioni per migliorare i risultati della query in linguaggio naturale:
- [Correggi le query senza risultati aggiungendo ulteriori dati](/docs/services/discovery?topic=discovery-performance-dashboard#addmore)
- [Porta i risultati migliori all'inizio con la formazione dei tuoi dati ](/docs/services/discovery?topic=discovery-performance-dashboard#traindata)

Puoi visualizzare le metriche dei dati nella [panoramica della query](/docs/services/discovery?topic=discovery-performance-dashboard#overview). 

## Correggi le query senza risultati aggiungendo ulteriori dati
{: #addmore}

In questa sezione del dashboard, puoi esaminare le query che non hanno restituito risultati e aggiungere ulteriori dati in modo che la query restituirà risultati in futuro. Fai clic sul pulsante **View all and add data** per iniziare. 

## Porta i risultati migliori all'inizio con la formazione dei tuoi dati
{: #traindata}

In questa sezione, puoi preparare le tue raccolte per migliorare la pertinenza dei risultati della query in linguaggio naturale. Fai clic sul pulsante **View all and perform relevancy training** per iniziare. Poi consulta [Aggiungi le query e classifica la pertinenza dei risultati](/docs/services/discovery?topic=discovery-improving-result-relevance-with-the-tooling#results) per le istruzioni.

Per ulteriori informazioni sui requisiti di formazione e sulle opzioni, consulta [Miglioramento della pertinenza del risultato con la strumentazione](/docs/services/discovery?topic=discovery-improving-result-relevance-with-the-tooling#improving-result-relevance-with-the-tooling).

## Panoramica della query
{: #overview}

Viene visualizzata la sezione della panoramica della query:
- Il numero totale di query effettuate dagli utenti
- La percentuale di query con uno o più risultati selezionati
- La percentuale di query senza risultati selezionati
- La percentuale di query senza risultati restituiti
- Un grafico che visualizza questi risultati nel tempo, in modo che puoi tenere traccia del modo in cui aggiungere ulteriori dati e la formazione della pertinenza per migliorare le prestazioni

Questi risultati vengono raccolti utilizzando l'API Events e Feedback. Per ulteriori informazioni, consulta il [Riferimento API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/discovery#create-event).
