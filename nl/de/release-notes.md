---

copyright:
  years: 2015, 2017
lastupdated: "2017-12-15"

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

# Releaseinformationen

Die Releaseinformationen enthalten Angaben über Änderungen, die seit dem letzten Release am {{site.data.keyword.discoveryfull}}-Service vorgenommen wurden.
{: shortdesc}

## API-Versionierung des Service
{: shortdesc}

API-Anforderungen benötigen einen Versionsparameter, der ein Datum im Format `version=JJJJ-MM-TT` angibt. Bei jeder abwärtskompatiblen Änderung der API wird eine neue Unterversion der API freigegeben.

Senden Sie den Versionsparameter zusammen mit jeder API-Anforderung. Der Service verwendet die API-Version für das von Ihnen angegebene Datum oder die Version, die vor diesem Datum zuletzt freigegeben wurde. Verwenden Sie nicht das aktuelle Datum als Standardwert. Geben Sie stattdessen ein Datum für eine Version an, die mit Ihrer App kompatibel ist, und ändern Sie das Datum erst dann, wenn Ihre App zur Verwendung einer späteren Version bereit ist.

Die aktuelle Version ist `2017-11-07`.

## Features als Betaversion
{: #beta-features}

IBM gibt Services, Features und Sprachunterstützungen frei, die als Betaversion oder experimentell klassifiziert sind. Diese Funktionen können instabil sein und werden möglicherweise häufig geändert werden; ihre Verwendung und Unterstützung kann kurzfristig eingestellt werden. Sie werden bereitgestellt, damit Sie ihre Funktionalität bewerten können. Eine experimentelle oder Betaversionsfunktion bietet möglicherweise nicht dasselbe Leistungs- oder Kompatibilitätsniveau wie eine allgemein freigegebene Funktion. Solche Funktionen sind nicht zur Verwendung in einer Produktionsumgebung gedacht; ihre derartige Verwendung erfolgt auf eigenes Risiko. 


## Änderungen
{: #change-log}

Für den Service sind die folgenden neuen Features und Änderungen verfügbar.

## 15. Dezember 2017

- Die Aufbereitung für die **Elementklassifizierung** wurde freigegeben, die Elemente (Sätze, Listen, Tabellen) in behördlichen Dokumenten analysiert, um wichtige Kategorien und Typen zu klassifizieren. Weitere Informationen finden Sie unter [Elementklassifizierung](/docs/services/discovery/element-classification.html). Bei Serviceinstanzen, die den **Premium**-Plan abonniert haben, ist die Elementklassifizierung nicht verfügbar.
- Die Basissprachunterstützung wurde für vereinfachtes Chinesisch und Niederländisch hinzugefügt. Weitere Informationen finden Sie unter [Sprachunterstützung](/docs/services/discovery/language-support.html). Gegenwärtig müssen Sammlungen in vereinfachtem Chinesisch und in Niederländisch mithilfe der API erstellt werden.
- Es wurden die beiden neuen Parameter `proxy_host_port` und `read-timeout` für Data Crawler hinzugefügt. Details enthält der Abschnitt [Data Crawler konfigurieren](/docs/services/discovery/data-crawler-discovery.html).
- Beim Einpflegen von PDF-Dokumenten treten unter Umständen die folgenden Probleme auf:
  - Wenn Hinweise zum Einpflegen abgefragt werden, wird das Feld `file_type` für PDF-Dokumente mit dem Wert `html` zurückgegeben.
  - Das Feld `file_type` im Objekt `extracted_metadata` der Ergebnisse für PDF-Dokumente ist auf `html` gesetzt.
  - Die API für die Dokumentdetails gibt ebenfalls das Feld `file_type` für PDF-Dokumente als `html` zurück.

{{site.data.keyword.discoveryshort}}-Tools:

- Es wurde ein grafisch orientierter Abfragebuilder (Visual Query Builder) für die Betaversion von {{site.data.keyword.discoveryfull}} Knowledge Graph hinzugefügt. Weitere Informationen finden Sie unter [Knowledge Graph mit {{site.data.keyword.discoveryshort}}-Tools abfragen](/docs/services/discovery/building-kg.html#querying-kg).

## 30. November 2017

- Die experimentelle Version von {{site.data.keyword.discoveryfull}} Visual Insights wurde freigegeben. Mit Visual Insights können Sie Verbindungen grafisch orientiert untersuchen, die aufgrund des Verständnisses von {{site.data.keyword.discoveryshort}} für semantische Elemente, Beziehungen, Konzepte und anderes erkannt wurden. Weitere Informationen finden Sie unter [Visual Insights](/docs/services/discovery/visual-insights.html). Eine Aussage zu experimentellen Features und Features als Betaversion finden Sie [hier](/docs/services/discovery/release-notes.html#beta-features).
- Die Betaversion von {{site.data.keyword.discoveryfull}} Knowledge Graph wurde freigegeben, einem Feature, das neue Endpunkte für die dokumentübergreifende Abfrage von Entitäten und Beziehungen bereitstellt. Dies schließt kontextbasierte Suchvorgänge und Einstufung nach Relevanz ein. Dieses Betaversionsfeature ist nur für Benutzer mit dem **Advanced**-Plan verfügbar. In **dedizierten** Umgebungen ist es nicht verfügbar. Weitere Informationen finden Sie unter [{{site.data.keyword.discoveryfull}} Knowledge Graph](/docs/services/discovery/building-kg.html). Eine Aussage zu Features als Betaversion finden Sie [hier](/docs/services/discovery/release-notes.html#beta-features).
  - Bekanntes Problem in {{site.data.keyword.discoveryfull}} Knowledge Graph: Alle Namen von Entitätstypen und Beziehungstypen werden während des Einpflegens in Großbuchstaben konvertiert. Beispielsweise wird der Entitätstyp 'GeoPoliticalEntity' in 'GEOPOLITICALENTITY' und der Beziehungstyp 'partOf' in 'PARTOF' konvertiert."
- [{{site.data.keyword.discoverynewsfull}}](/docs/services/discovery/watson-discovery-news.html) wurde in zwei weiteren Sprachen freigegeben, nämlich Koreanisch (`collection_id`: `news-ko`) und Spanisch (`collection_id`: `news-es`). Die koreanische und spanische Version von {{site.data.keyword.discoverynewsfull}} kann nur über die API verwendet werden; Informationen zum Abfragen einer Sammlung über die API finden Sie in der [API-Referenz ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/discovery/api/v1/#query-collection){: new_window}. Die englische Version von {{site.data.keyword.discoverynewsfull}} hat nun für `collection_id` den Wert `news-en`. Zuvor wurde für `collection_id` der Wert `news` verwendet. Falls Sie den früheren Wert für `collection_id` verwendet haben, ist dies weiterhin möglich. Es kann jedoch sinnvoll sein, bei neuen Projekten auf den neuen Wert für `collection_id` umzusteigen.
- Abfrageergebnisse geben einen Wert für `score` zurück, der die relative Relevanz zwischen Abfrageergebnissen angibt. Ab dem 30. November 2017 hat sich die Berechnungsmethode für `score` geändert. Der Wert für `score` sollte nur zum Einstufen von Dokumenten in einer einzelnen Suche verwendet werden und nicht such- oder sitzungsübergreifend. Falls Sie eine Sammlung trainiert haben, wird der Wert für `score` in den Ergebnissen einer Abfrage in natürlicher Sprache zurückgegeben. Da der Wert für `score` die relative Relevanz zwischen Abfrageergebnissen angibt, sollte er nicht als Schwellenwert verwendet werden. Verwenden Sie zu diesem Zweck stattdessen `confidence`. Dieses Feld gibt die Relevanz des Ergebnisses in Bezug auf das trainierte Modell an. Weitere Informationen zum Festlegen von Schwellenwerten finden Sie unter [Konfidenzbewertungen](/docs/services/discovery/train-tooling.html#confidence).
- Ab diesem Release werden beim Passagenabruf Satzgrenzen erkannt. Es wird versucht, Passagen zurückzugeben, deren Anfang der Beginn eines Satzes und deren Ende das Satzende ist. Zuvor begannen und endeten viele Passagen mitten im Satz. Weitere Informationen zum Passagenabruf finden Sie unter [Passagen](/docs/services/discovery/query-parameters.html#passages).

## 15. November 2017

{{site.data.keyword.discoveryshort}}-Tools:

- Die Aufbereitung für die [Beziehungsextraktion](/docs/services/discovery/building.html#relation-extraction) wurde hinzugefügt, bei der auch die Möglichkeit besteht, ein mit {{site.data.keyword.knowledgestudiofull}} erstelltes angepasstes Beziehungsmodell zu integrieren.
- Die Aufbereitung für die [Entitätsextraktion](/docs/services/discovery/building.html#entity-extraction) der {{site.data.keyword.discoveryshort}}-Tools bietet nun die Möglichkeit, ein mit {{site.data.keyword.knowledgestudiofull}} erstelltes angepasstes Entitätsmodell zu integrieren.
- Die Option für die Erstellung einer Sammlung in Japanisch wurde aus den {{site.data.keyword.discoveryshort}}-Tools entfernt. Bei der {{site.data.keyword.discoveryshort}}-API gibt es jedoch weiterhin die Möglichkeit, eine Sammlung in Japanisch zu erstellen.
- Die {{site.data.keyword.discoveryshort}}-Tools unterstützen jetzt syndizierte Umgebungen.

## 10. November 2017

{{site.data.keyword.discoveryshort}}-Tools:

- Weitere Optionen für den Passagenabruf wurden zu den {{site.data.keyword.discoveryshort}}-Tools hinzugefügt. Bei einer Abfrage können Sie jetzt die Felder angeben, aus denen die Passagen zurückgegeben werden sollen, sowie die Anzahl der zurückzugebenden Passagen und die maximale Anzahl der Zeichen für die einzelnen Passagen. Informationen zu Grenzwerten, Minimalwerten und Maximalwerten finden Sie unter [Passagen](/docs/services/discovery/query-parameters.html#passages).

## 8. November 2017

Die Versionszeichenfolge für alle API-Aufrufe wurde von `2017-10-16` in `2017-11-17` geändert. Diese Version zeichnet sich durch Folgendes aus:
- Das Feld `score` in jedem Abfrageergebnis wurde in ein Objekt namens `results_metadata` verschoben.
- Falls die abgefragte Sammlung trainiert wurde und die Abfrage in natürlicher Sprache definiert ist, enthält das Objekt `results_metadata` ein Feld `confidence`, das die Konfidenzbewertung für dieses Ergebnis angibt. Details enthält der Abschnitt [Konfidenzbewertung](/docs/services/discovery/train-tooling.html#confidence).
- Felder, die Leerzeichen enthalten (z. B. `body.additional reading`) werden während des Einpflegens herausgefiltert. Der Abschnitt `notices` enthält die Angabe `The field 'additional reading' is invalid: whitespace, '.', '#' and ',' are invalid in a field name`.
- Das Feld `result_metadata` wird während des Einpflegens herausgefiltert.

## 16. Oktober 2017

- Die Versionszeichenfolge für alle API-Aufrufe wurde von `2017-09-01` in `2017-10-16` geändert. Bei dieser Version wird das Hochladen von neuen Dokumenten in vorhandene Sammlungen, die mit {{site.data.keyword.alchemylanguageshort}}-Aufbereitungen aufbereitet wurden, sowie die Erstellung neuer Sammlungen und deren Aufbereitung mit {{site.data.keyword.alchemylanguageshort}}-Aufbereitungen nicht mehr unterstützt. Vorhandene, mit {{site.data.keyword.alchemylanguageshort}} aufbereitete Sammlungen sollten baldmöglichst nach {{site.data.keyword.nlushort}}-Aufbereitungen migriert werden. Details finden Sie unter [Aufbereitungen nach {{site.data.keyword.nlushort}} migrieren](/docs/services/discovery/migrate-nlu.html#migrating-enrichments-to-natural-language-understanding). Die {{site.data.keyword.discoveryshort}}-Tools verwenden ebenfalls die Version `2017-10-16`; weitere Informationen finden Sie im nächsten Abschnitt.

{{site.data.keyword.discoveryshort}}-Tools:

- Die {{site.data.keyword.discoveryshort}}-Tools verwenden die API-Versionszeichenfolge `2017-10-16`. Wenn Sie die Tools verwenden, können Sie daher nach dem Datum `2017-10-16` nicht mehr Dokumente in bestehende {{site.data.keyword.alchemylanguageshort}}-Sammlungen hochladen oder neue mit {{site.data.keyword.alchemylanguageshort}}-Aufbereitungen aufbereitete Sammlungen erstellen. Falls Sie weiterhin die {{site.data.keyword.discoveryshort}}-Tools für die Aufbereitung von Sammlungen verwenden wollen, migrieren Sie zuerst Ihre Sammlungen nach {{site.data.keyword.nlushort}}. Details finden Sie unter [Aufbereitungen nach {{site.data.keyword.nlushort}} migrieren](/docs/services/discovery/migrate-nlu.html#migrating-enrichments-to-natural-language-understanding). 
- Der **Datenschemaexplorer** zeigt Beispielabfragen für verschiedene Aufbereitungen in der Sammlung '{{site.data.keyword.discoverynewsfull}}' an. Er enthält jetzt außerdem einen Link 'Weitere Werte anzeigen', der zusätzliche Beispielwerte für die jeweilige Aufbereitung in {{site.data.keyword.discoverynewsfull}} anzeigt.
- Es wurden mehrere Produktivitätserweiterungen umgesetzt, unter anderem die Kombination von Sammlungsstatistikdaten, Fehlern und Warnungen sowie Dateneinblicke in der Anzeige **Daten verwalten**.
- Es wurde eine Nachricht hinzugefügt, die einen Alert ausgibt, wenn die Verarbeitung von Dokumenten fertiggestellt ist.

## 9. Oktober 2017

- In der API ist die neue Aggregationsmetrik `unique_count` verfügbar. Sie gibt die Anzahl der eindeutigen Instanzen für ein angegebenes Feld in einer Sammlung zurück. Weitere Informationen finden Sie unter [unique_count](/docs/services/discovery/query-aggregations.html#unique_count).

{{site.data.keyword.discoveryshort}}-Tools:

- Histogramm- und Zeitscheibenaggregationen werden jetzt in **Visual Query Builder** unterstützt. Außerdem haben Sie die Möglichkeit, die Anomalieerkennung für Zeitscheibenabfragen zu aktivieren.
- Im **Datenschemaexplorer** werden Beispielabfragen für die ausgewählte Aufbereitung angezeigt. Er enthält jetzt außerdem einen Link 'Weitere Werte anzeigen', der zusätzliche Beispielwerte für die jeweilige Aufbereitung anzeigt.
- Es wurde ein Menüsymbol hinzugefügt, das die Navigation zu den Anzeigen **Daten verwalten**, **Datenschema anzeigen** und **Abfragen erstellen** beschleunigt.

### 3. Oktober 2017

- Die Dokumentsegmentierung ist jetzt verfügbar. Weitere Informationen finden Sie unter [Dokumente mittels Dokumentsegmentierung teilen](/docs/services/discovery/building.html#doc-segmentation).

### 29. September 2017

- {{site.data.keyword.discoveryshort}} wurde in der Region `Deutschland` am 29. September 2017 gestartet. Zur Einhaltung von EU-Datenverordnungen werden AlchemyLanguage-Aufbereitungen in dieser Region nicht unterstützt.
- Bekanntes Problem: Abfragefelder können keine Leerzeichen enthalten. Wenn eine Abfrage in {{site.data.keyword.discoveryshort}} geschrieben wird und Abfragefelder Leerzeichen enthalten (z. B. `body.additional reading`), empfangen Sie den Fehler `400: Invalid query syntax error`.

### 25. September 2017

- Es gibt jetzt einen Premium-Preisstrukturplan. Weitere Informationen enthält der Abschnitt [Preisstrukturpläne für {{site.data.keyword.discoveryshort}}](/docs/services/discovery/pricing-details.html).
- Die Möglichkeit zum sammlungsübergreifenden Abfragen und Auflisten von Feldern und Abfragehinweisen in derselben Umgebung wurde hinzugefügt. Details finden Sie unter [Mehrere Sammlungen abfragen](/docs/services/discovery/using.html#multiple-collections).
- Informationen zur Sprachunterstützung für {{site.data.keyword.discoveryshort}} sind unter [Sprachunterstützung](/docs/services/discovery/language-support.html) verfügbar.

{{site.data.keyword.discoveryshort}}-Tools:
- Visual Query Builder wurde vom Betaversionsstatus in den Status der allgemeinen Verfügbarkeit versetzt. Filter-, Zeitscheiben- und Histogrammaggregationen werden bei Visual Query Builder derzeit nicht unterstützt. Klicken Sie auf **Analyse der Ergebnisse einbeziehen** und anschließend auf **In Abfragesprache bearbeiten** in der Anzeige **Abfragen erstellen**, um solche Aggregationen zu schreiben.
- Die Betaversionsfunktion zur Deduplizierung bei Abfragen von {{site.data.keyword.discoverynewsfull}} wurde hinzugefügt.
- Neben Sammlungen in englischer, deutscher und spanischer Sprache können Sie Sammlungen jetzt in Arabisch, Französisch, Italienisch, Koreanisch und Portugiesisch (Brasilien) erstellen.
- Bekanntes Problem: {{site.data.keyword.discoveryshort}}-Tools unterstützen keine syndizierten Umgebungen.

### 14. September 2017

{{site.data.keyword.discoveryshort}}-Tools:

- Der Datenschemaexplorer wurde hinzugefügt, in dem die Felder und Werte in Ihren umgewandelten Dokumenten angezeigt werden. Diese Informationen können Ihnen ein Verständnis der Datenstruktur in Ihrer Sammlung vermitteln, bevor Sie in der Discovery-Abfragesprache Abfragen erstellen. Das Datenschema kann entweder nach Dokument (Dokumentansicht) oder nach Feld (Sammlungsansicht) angezeigt werden. Zum Zugriff auf den Datenschemaexplorer klicken Sie in der Anzeige **Einblick in eigene Daten** auf die Schaltfläche **Datenschema anzeigen** oder klicken Sie links auf das Symbol **Datenschema anzeigen**.

### 6. September 2017

- Es wurde die Betaversionsfunktionalität zur Deduplizierung von Dokumenten hinzugefügt, die von Ihrer Abfrage zurückgegeben wurden. Dieses Betaversionsfeature kann sowohl für private Sammlungen als auch für die Sammlung 'Watson Discovery News' verwendet werden. Details enthält der Abschnitt [Doppelte Dokumente aus Abfrageergebnissen ausschließen](/docs/services/discovery/query-parameters.html#deduplication).

Die Dokumentdeduplizierung wird gegenwärtig nur als Betafunktionalität unterstützt. Weitere Informationen können Sie der Aussage zu Betaversionen am Anfang dieses Dokuments entnehmen.

### 31. August 2017

- Die Versionszeichenfolge für alle API-Aufrufe wurde von `2017-08-01` in `2017-09-01` geändert. Diese Version enthält Aktualisierungen, die die folgenden ungültigen JSON-Felder während der Vorschau und des Einpflegens herausfiltern, damit nur gültige JSON-Felder eingepflegt werden. Aktualisieren Sie Ihre Versionszeichenfolge auf `2017-09-01`, um Konflikte und mögliche Fehler zu vermeiden.

   - `id`, `score` und `highlight` befinden sich auf der höchsten Ebene (Sie können weiterhin mit der Funktion `Dokument hinzufügen` Dokumente zu Ihrer Sammlung hinzufügen). Details enthält die [API-Referenz ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ibm.com/watson/developercloud/discovery/api/v1/#add-doc){: new_window}.
   - Mit dem Präfix `_` versehene Feldnamen befinden sich auf der höchsten Ebene (infolgedessen können Sie beim Abfragen einer Dokument-ID nach `id` anstelle von `_id` abfragen.)
   - `#` und `,` im Feldnamen.
   - Mit dem Präfix `+` und `-` versehene Feldnamen.
   - Leere Werte `"` `"` für einen Feldnamen.

**Hinweis:** Falls Ihr JSON-Dokument diese Zeichen in den Feldnamen oder `id`, `score` und `highlight` auf der höchsten Ebene enthält, müssen Sie diese entfernen, bevor Sie die Dokumente zu Ihrer Sammlung hinzufügen, da diese Felder andernfalls leer sind. Sie können eine angepasste Konfiguration erstellen und Ihr JSON-Dokument normalisieren, bevor Sie Dokumente zu Ihrer Sammlung hinzufügen, um dieses Problem zu vermeiden. Weitere Informationen finden Sie unter [Angepasste Konfiguration](/docs/services/discovery/building.html#custom-configuration).  Außerdem verursachen Dokumente, deren Dateinamen die Interpunktionszeichen `?`, `:` oder `#` enthalten, Fehler beim Einpflegen. Benennen Sie alle Dokumente, deren Namen diese Zeichen enthalten, vor dem Einpflegen um.

- Die Abrufmethoden für `natural_language_query` wurden aktualisiert, um die Relevanz der Ergebnisse durch übereinstimmende Wörter mit verwandter Semantik zu verbessern. Diese Aktualisierung betrifft nur Sammlungen, für die noch kein Relevanztraining durchgeführt wurde. Falls Sie `natural_language_query` verwenden und noch kein Relevanztraining erfolgt ist, wird die Reihenfolge der zurückgegebenen Ergebnisse möglicherweise verbessert.

{{site.data.keyword.discoveryshort}}-Tools:

- Änderungen am Abfragebuilder vereinfachen den Wechsel zwischen den Optionen für die Discovery-Abfragesprache und für Abfragen in natürlicher Sprache sowie zwischen Abfrage, Filterung und Aggregation.


### 25. August 2017

- Das Array `passages` enthält jetzt `field`, `start_offset` und `end _offset`. `field` gibt den Namen des Feldes an, aus dem die Passage extrahiert wurde. `start_offset` ist das erste Zeichen des Passagentextes innerhalb des Feldes. `end_offset` ist das letzte Zeichen des Passagentextes innerhalb des Feldes.

{{site.data.keyword.discoveryshort}}-Tools:
Diese Erweiterung der Abfrageerstellung finden Sie auf der Seite **Abfragen erstellen**.

-  Als Betaversion wurde die Möglichkeit hinzugefügt, Abfragen in der {{site.data.keyword.discoveryshort}}-Abfragesprache mit einem grafisch orientierten Builder zu schreiben. Klicken Sie in den Abschnitten **Nach Dokumenten suchen** und **Abzufragende Dokumente begrenzen** auf **Im visuellen Modus erstellen**, um diese Funktion auszuprobieren. Während Sie Ihre Abfrage visuell erstellen, wird sie darunter in der **{{site.data.keyword.discoveryshort}}-Abfragesprache** angezeigt.

   Visual Query Builder wird gegenwärtig nur als Betafunktionalität unterstützt. Weitere Informationen können Sie der Aussage zu Betaversionen am Anfang dieses Dokuments entnehmen.

### 18. August 2017

{{site.data.keyword.discoveryshort}}-Tools:

- Verschachtelte Aggregationen und Bedingungen werden jetzt in der Betaversion des grafisch orientierten Aggregationsbuilders unterstützt, die seit dem [11. August 2017](/docs/services/discovery/release-notes.html#11aug) verfügbar ist. Es besteht eine Begrenzung auf 3 Bedingungen pro Aggregationszeile.

   Der grafisch orientierte Aggregationsbuilder wird gegenwärtig nur als Betafunktionalität unterstützt. Weitere Informationen können Sie der Aussage zu Betaversionen am Anfang dieses Dokuments entnehmen.

### 11. August 2017
{: #11aug}

{{site.data.keyword.discoveryshort}}-Tools:

Die beiden folgenden Features stellen Erweiterungen für die Abfrageerstellung dar und befinden sich in der Anzeige **Abfragen erstellen**.

- Es wurde die Option zum Auswählen einer Abfrage aus einer Gruppe von vordefinierten Beispielabfragen und -aggregationen hinzugefügt. Klicken Sie in der rechten oberen Ecke auf **Beispielabfrage verwenden**, um auf die Liste zuzugreifen. Falls Sie eine private Sammlung abfragen, verwenden die Beispiele die in Ihrer Sammlung gefundenen Werte für `top entities`, `categories` usw. Diese Abfragen können Sie als Ausgangspunkt beim Schreiben Ihrer eigenen Abfragen verwenden. Beispielabfragen sind sowohl für {{site.data.keyword.discoverynewsfull}} als auch für private Sammlungen verfügbar.

-  Als Betaversion wurde die Möglichkeit hinzugefügt, Aggregationen mit einem grafisch orientierten Builder zu schreiben. Klicken Sie auf **Im visuellen Modus erstellen** über dem Feld **Aggregationsabfrage mit {{site.data.keyword.discoveryshort}}-Abfragesprache schreiben**, um den Builder auszuprobieren. Während Sie Ihre Aggregation visuell erstellen, wird die Abfrage darunter in der **{{site.data.keyword.discoveryshort}}-Abfragesprache** angezeigt.  

   Der grafisch orientierte Aggregationsbuilder wird gegenwärtig nur als Betafunktionalität unterstützt. Weitere Informationen können Sie der Aussage zu Betaversionen am Anfang dieses Dokuments entnehmen.

### 31. Juli 2017

- Eine neue Version von {{site.data.keyword.discoverynewsfull}} wurde freigegeben. Die ursprüngliche Version wurde in '{{site.data.keyword.discoverynewsfull}} Original' umbenannt und mit dem Servicedatum **15. Januar 2018** zurückgezogen. Anweisungen für die Migration finden Sie unter [Von Watson Discovery News Original migrieren](/docs/services/discovery/migrate-bwdn.html).
**Hinweis:** Falls Sie eine neue Instanz von {{site.data.keyword.discoveryshort}} erstellt haben, können Sie nur auf die neue Version von {{site.data.keyword.discoverynewsfull}} zugreifen. 

- Ein neuer Preisstrukturplan für {{site.data.keyword.discoveryfull}} wurde freigegeben. Details enthält der Abschnitt [Preisstrukturpläne für {{site.data.keyword.discoveryshort}}](/docs/services/discovery/pricing-details.html).

- Die Versionszeichenfolge für alle API-Aufrufe wurde von `2017-07-19` in `2017-08-01` geändert. Diese Version enthält Aktualisierungen für den neuen Preisstrukturplan und die neue Version von Watson Discovery News. Aktualisieren Sie die Versionszeichenfolge, um Konflikte und mögliche Fehler zu vermeiden.

### 19. Juli 2017

 - Im Rahmen der Preisänderung, die für den 1. August 2017 angekündigt wurde, werden Benutzer, die derzeit den veralteten Plan für den **dreißigtägigen kostenlosen Test** verwenden, automatisch auf den **Lite**-Plan migriert. Infolge dieser Überführung haben Bestandskunden möglicherweise die Begrenzung des Lite-Plans für Dokumente _(2000)_, Speicher _(200Mb)_ oder Anzahl der Sammlungen _(2)_ erreicht bzw. überschritten. Falls Sie die Begrenzung des **Lite**-Plans überschritten haben, können Sie keinen zusätzlichen Inhalt im Service hinzufügen, Ihre Sammlungen jedoch weiterhin abfragen. Den aktuellen Status aller dieser Grenzwerte können Sie mithilfe der {{site.data.keyword.discoveryshort}}-Tools oder der API anzeigen. Damit Sie das Hinzufügen von Inhalt zur {{site.data.keyword.discoveryshort}}-Instanz fortsetzen können, müssen Sie eine der folgenden Maßnahmen ergreifen:
   - Entfernen Sie Sammlungen und/oder Dokumente, damit die Begrenzungen des **Lite**-Plans nicht mehre überschritten werden.
    Dokumente können entweder einzeln über die API mit der Methode [delete-doc](https://www.ibm.com/watson/developercloud/discovery/api/v1/#delete-doc) oder als ganze Sammlungen mithilfe der Tools oder der API unter Verwendung der Methode [delete-collection](https://www.ibm.com/watson/developercloud/discovery/api/v1/#delete-collection) gelöscht werden.
   - Führen Sie für Ihren Plan ein Upgrade auf eine Stufe durch, die Ihren Speicherbedarf erfüllt.
 - Kunden mit Umgebungen der Größe **`1`**, **`2`** oder **`3`** werden automatisch auf den **Advanced**-Plan migriert.
  

### 17. Juli 2017

 - Die folgenden Funktionen wurden vom Betaversionsstatus in den Status der allgemeinen Verfügbarkeit versetzt: 

   - Relevanztraining
   - Abfrage in natürlicher Sprache 
   - Hervorhebung

 - Bei diesem Release ändert sich der Aufbereitungsmechanismus in {{site.data.keyword.discoveryfull}} von {{site.data.keyword.alchemylanguageshort}} in {{site.data.keyword.nlushort}}. {{site.data.keyword.alchemylanguageshort}} wird nicht weiterentwickelt; Sie sollten baldmöglichst {{site.data.keyword.nlushort}} verwenden. Details finden Sie unter [{{site.data.keyword.alchemylanguageshort}}-Aufbereitungen nach {{site.data.keyword.nlushort}}-Aufbereitungen migrieren](/docs/services/discovery/migrate-nlu.html).**Hinweis:** Bei der Integration mit Watson Knowledge Studio muss weiterhin die Konfiguration für die {{site.data.keyword.alchemylanguageshort}}-Aufbereitung verwendet werden. Details enthält der Abschnitt [Integration mit {{site.data.keyword.knowledgestudiofull}}](/docs/services/discovery/integrate-wks.html).

 - Die Versionszeichenfolge für alle API-Aufrufe wurde von `2017-06-25` in `2017-07-19` geändert. Diese Version aktiviert eine NLU-Standardkonfiguration bei der Sammlungserstellung. In vorherigen Versionen sollte weiterhin die Aufbereitung mit {{site.data.keyword.alchemylanguageshort}} möglich sein.

    Die Standardkonfiguration wurde für die Verwendung von {{site.data.keyword.nlushort}} aktualisiert. Aktualisieren Sie die Versionszeichenfolge baldmöglichst, um Konflikte und mögliche Fehler zu vermeiden.

 - Discovery-Tools:

    Die Erkenntniskarten für Sammlungen, die mit {{site.data.keyword.alchemylanguageshort}}-Aufbereitungen aufbereitet wurden, werden nicht mehr automatisch aktualisiert. Sie müssen Ihre Sammlung nach {{site.data.keyword.nlushort}}-Aufbereitungen migrieren, damit diese Karten aktualisiert werden.

    Falls Sie eine Sammlung vor dem **18. Juli 2017** erstellt und die **Standardkonfiguration** angewendet haben, wurde die Sammlung mit {{site.data.keyword.alchemylanguageshort}}-Aufbereitungen aufbereitet. Falls Sie die **Standardkonfiguration** nach diesem Datum auf eine Sammlung anwenden, werden die {{site.data.keyword.nlushort}}-Aufbereitungen verwendet (der Konfigurationsname ändert sich in den Tools in **Standardkonfiguration mit NLU**). Da die {{site.data.keyword.alchemylanguageshort}}-Aufbereitungen veraltet sind, sollten sie nicht für neue Sammlungen verwendet werden.

### 30. Juni 2017

 -  Die am 5. Mai 2017 als Betaversion eingeführte Funktion für die Entitätsnormalisierung wurde in den Status der allgemeinen Verfügbarkeit versetzt. Details finden Sie unter [Angepasste Konfiguration zur Normalisierung von Entitäten erstellen](/docs/services/discovery/normalize-entities.html).

### 23. Juni 2017

 - Die Versionszeichenfolge für alle API-Aufrufe wurde von `2017-12-01` in `2017-06-25` geändert. Die neue Versionszeichenfolge ermöglicht Aufbereitungen in Deutsch (`de`) oder Spanisch (`es`), falls für eine Sammlung eine dieser Sprachen definiert ist. Zuvor wurden alle Aufbereitungen ungeachtet der Spracheinstellung einer Sammlung in Englisch ausgeführt.

    Falls Sie Aufbereitungen in anderen Sprachen als Englisch nicht verwenden, können Sie weiterhin die Versionszeichenfolge `2016-12-01` verwenden. Sie sollten die Versionszeichenfolge jedoch baldmöglichst aktualisieren, um in der Zukunft mögliche Konflikte zu vermeiden.

 - Die Anomalieerkennung ist jetzt im Rahmen von Zeitscheibenaggregationen (Typ `timeslice`) als Funktionalität allgemein verfügbar. Details finden Sie unter [Anomalieerkennung in Zeitscheiben](/docs/services/discovery/query-aggregations.html#anomaly-detection). 

 - Discovery-Tools:

   - Die Möglichkeit zur Verbesserung der Abfrageergebnisrelevanz mithilfe der Discovery-Tools (Relevanztools) wurde als Betaversion hinzugefügt. Weitere Informationen finden Sie im Abschnitt [Relevanz von Abfrageergebnissen mithilfe der Discovery-Tools verbessern](/docs/services/discovery/train-tooling.html).

### 19. Juni 2017

  - Discovery-Tools:

    - Es wurde die Option hinzugefügt, in einer neuen Sammlung Englisch, Spanisch oder Deutsch als Sprache der Dokumente anzugeben. Wählen Sie hierzu **Sprache der Dokumente auswählen** im Dialogfeld **Benennen Sie Ihre neue Sammlung** aus.

    - Die Anzeige **Abfragen erstellen** wurde durch eine Registerkarte namens **Zusammenfassung** ergänzt. Auf der Registerkarte **Zusammenfassung** wird eine Übersicht über die vollständigen Abfrageergebnisse angezeigt, die auf der vorhandenen Registerkarte **JSON** bereitgestellt werden. Die Anzeige auf der Registerkarte **Zusammenfassung** variiert abhängig von Ihrer Abfrage und den verwendeten Aufbereitungen. Zu den Informationen, die angezeigt werden können, gehören der Dokumentname oder die ID,  die Aggregationsstatistik, Dokumentpassagen in der Reihenfolge ihrer Relevanz und Ergebnisse nach Aufbereitung.

    - Zur Anzeige **Abfragen erstellen** wurde eine Option 'Abfrage in natürlicher Sprache' hinzugefügt. Um diese Option zu verwenden, klicken Sie im Abschnitt **Nach Dokumenten suchen** auf **Frage in normaler Sprache stellen**. Daraufhin wird ein Feld angezeigt, in dem Sie Ihre Frage eingeben können. Auf das ursprüngliche Abfragefeld (zuvor mit **Abfrage oder Schlüsselwort eingeben** betitelt) können Sie jetzt zugreifen, indem Sie auf die Schaltfläche **Discovery-Abfragesprache verwenden** klicken.

    - Die Anzeige **Abfragen erstellen** wurde neu gestaltet, alle Felder und Optionen sind jedoch weiterhin verfügar. Nachfolgend sind die alten und neuen Namen für die Felder aufgeführt.

| **Alter Feldname**                                            | **Neuer Feld- oder Abschnittsname**                                                                                             |
|----------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| Abfrage schreiben und ausführen                          | Nach Dokumenten suchen                                                                                                |
| Abfrageergebnisse eingrenzen (Filter)                    | Abzufragende Dokumente begrenzen                                                                                      |
| Abfrageergebnisse gruppieren (Aggregation)               | Analyse der Ergebnisse einbeziehen                                                                                    |
| Anzuzeigende Felder                                      | Der Name wurde nicht geändert, aber das Feld in den neuen Abschnitt **Anzeigeoptionen anpassen** versetzt.|
| Anzahl zurückzugebender Dokumente (Zähler)               | Anzahl zurückzugebender Dokumente (Feld wurde in den Abschnitt **Anzeigeoptionen anpassen** versetzt)     |
| Übereinstimmende Passagen einbeziehen                    | Relevante Passagen einbeziehen (Feld wurde in den Abschnitt **Anzeigeoptionen anpassen** versetzt)        |
| Anzahl der anfangs zu überspringenden Abfragefelder (Offset) | Anzahl der anfangs zu überspringenden Abfrageergebnisse (Feld wurde in den Abschnitt **Anzeigeoptionen anpassen** versetzt) |

### 5. Juni 2017

 - Abfragen von Watson Discovery News zeigen jetzt nur die ersten 150 Wörter jedes Artikels in den JSON-Feldern `text` und `alchemyapi_text` an. Im Feld `blekko.snippet` wird nur der erste Satz des Ausschnittarrays angezeigt.

### 30. Mai 2017

 - Der Parameter `passages` für die Abfrage-API wurde vom Betaversionsstatus in den Status der allgemeinen Verfügbarkeit versetzt.

### 25. Mai 2017

 - Discovery-Tools: In diesem Release wurde die Hervorhebung für Abfragefelder hinzugefügt. Dieses Feature versieht Feldnamen in den JSON-Daten des Teilfensters 'Ergebnisse'  mit einer gelben Hervorhebung. Alle erforderlichen oder gefilterten Felder werden für jedes Ergebnis selbst dann hervorgehoben, wenn der Inhalt des Feldes nicht mit der Abfrage übereinstimmt. Alle in Aggregationen verwendeten Feldern werden in den Abfrageergebnissen ebenfalls hervorgehoben, aber nur die erste Aggregationsoperation wird hervorgehoben.

### 10. Mai 2017

 - Die Methoden `query` und `notices` unterstützen jetzt den Parameter `highlight`. Der Parameter ist boolesch. Wenn Sie eine Abfrage ausführen und für `highlight` den Wert `true` angeben, gibt der Service Ausgabe zurück, die ein neues Feld `highlight` enthält, in dem Wörter, die mit der Abfrage übereinstimmen, in HTML-Tags `*` (Hervorhebung) eingeschlossen sind. Details enthält der Abbschnitt [Abfrageparameter](/docs/services/discovery/query-parameters.html#highlight).

 - Es kann sein, dass die Löschung einer Umgebung nur teilweise ausgeführt wird. Dies führt zu einer Situation, in der eine neue Umgebung nicht erstellt werden kann, da nur eine einzige Umgebung pro Serviceinstanz zulässig ist. Falls Sie versuchen, eine Umgebung zu löschen und anschließend eine Umgebung zu erstellen, aber eine der Operationen im Status `pending` steckenbleibt, ist dieses Problem wahrscheinlich bei Ihnen aufgetreten. Zur Umgehung führen Sie die Löschoperation erneut aus, damit sie vollständig abgeschlossen wird, und erstellen Sie anschließend die neue Umgebung.

### 8. Mai 2017

 - Das Bewertungsmodell für die emotionale Tendenz wurde aktualisiert, um die Genauigkeit der Aufbereitungen für die Emotionsanalyse (`docEmotion`) zu verbessern. Der Trainingsdatenbestand wurde vergrößert und die Featureentwicklung wurde geändert. Im Ergebnis besitzt das Modell eine höhere Genauigkeit für den Vergleichsdatenbestand.

### 5. Mai 2017

 - Die Entitätsnormalisierung kann jetzt mit dem Discovery-Service verwendet werden, wenn ein durch Watson Knowledge Studio generiertes Modell eingesetzt wird. Die Entitätsnormalisierung fügt normalisierte (kanonische) Namen für verschiedene Verweise auf dieselbe Person oder dasselbe Objekt im Quellendokument ein. Details finden Sie unter [Angepasste Konfiguration zur Normalisierung von Entitäten erstellen](/docs/services/discovery/normalize-entities.html).

     **Hinweis:** Die Entitätsnormalisierung wird gegenwärtig nur als Betafunktionalität unterstützt. Weitere Informationen können Sie der Aussage zu Betaversionen am Anfang dieses Dokuments entnehmen.

 - Das Fehlerprotokoll für die Tools ist nicht mehr auf maximal acht (8) Seiten von Ergebnissen begrenzt. Im Fehlerprotokoll wird weiterhin die Dokument-ID angegeben, wenn der Dokumentname nicht verfügbar ist.

 - Konfigurationsnamen sind auf 50 Zeichen begrenzt und müssen aus den Zeichen `[a-zA-Z0-9-_]` bestehen.

 - Der zuvor nur über die API verfügbare Parameter `passages` ist jetzt auch in den Tools verfügbar.

### 25. April 2017

  - Der Service ermöglicht Ihnen nun die Bereitstellung von *Trainingsdaten*, um die Genauigkeit der Abfrageergebnisse zu verbessern. Wenn Sie eine Discovery-Instanz mit Trainingsdaten ausstatten, ermittelt der Service mithilfe von Watson-Algorithmen die relevantesten Ergebnisse. Je mehr Trainingsdaten Sie hinzufügen, desto genauer und ausgereifter wird die Serviceinstanz bei den zurückgegebenen Ergebnissen. Weitere Informationen finden Sie im Abschnitt [Relevanz von Abfrageergebnissen mithilfe der Discovery-Tools verbessern](/docs/services/discovery/train.html) und in der [API-Referenz ](http://www.ibm.com/watson/developercloud/discovery/api/v1/#training-data).

  - Die API unterstützt jetzt den Parameter `natural_language_query` als Betaversion. Mit diesem Parameter können Sie eine Abfage in natürlicher Sprache anstelle der Abfragesprache des Discovery-Service angeben. Informationen finden Sie in der API-Referenz unter [Sammlung abfragen](http://www.ibm.com/watson/developercloud/discovery/api/v1/#query-collection).

  - In diesem Release wurden Dokumentationsaktualisierungen und Erratakorrekturen vorgenommen.

### 14. April 2017

Die Abfrage-API (`GET /v1/environments/{umgebungs-id}/collections/{sammlungs-id}/query`) wurde erweitert. Informationen finden Sie in der API-Referenz unter [Sammlung abfragen](http://www.ibm.com/watson/developercloud/discovery/api/v1/#query-collection).

  - Die Abfrage-API unterstützt jetzt den Parameter `passages`. Falls der Parameter auf `true` gesetzt ist, gibt die Abfrage eine Gruppe der relevantesten Passaten aus den Dokumenten in Ihre Sammlung zurück. Die Passagen werden durch hoch entwickelte Watson-Algorithmen generiert, mit denen die besten Textpassagen aus allen durch die Abfrage zurückgegebenen Dokumenten ermittelt werden. Auf diese Weise können Sie Informationen und Kontext präziser ermitteln. Informationen finden Sie in der API-Referenz unter [Sammlung abfragen](http://www.ibm.com/watson/developercloud/discovery/api/v1/#query-collection).

    - Die Angabe von `passages=true` in Ihrer Abfrage kann die Leistung aufgrund einer erhöhten Verarbeitung für die Extraktion von Passagen beeinträchtigen. Bei größeren Umgebungen kann der Leistungseinfluss geringer sein.

    - Der Parameter `passages` wird nur für private Sammlungen unterstützt. Für die Sammlung 'Watson Discovery News' wird er nicht unterstützt.

    - Der Parameter `passages` gibt derzeit maximal 10 Ergebnisse zurück. Die Anzahl der zurückgegebenen Ergebnisse kann nicht geändert werden.

    - Der Parameter `passages` gibt aus jedem Dokument in der Sammlung maximal drei (3) Passagen zurück. Falls ein Dokument mehr als drei weitere relevante Passagen enthält, werden sie mit dem Parameter nicht zurückgegeben.

### 7. April 2017

- Die Abfrage-API (`GET /v1/environments/{umgebungs-id}/collections/{sammlungs-id}/query`) unterstützt jetzt den Parameter `sort`, mit dem Sie eine durch Kommas getrennte Liste der Felder im Dokument angeben können, nach denen die Sortierung vorgenommen werden soll. Informationen finden Sie in der API-Referenz unter [Sammlung abfragen](http://www.ibm.com/watson/developercloud/discovery/api/v1/#query-collection).
- Der Parameter `timeslice` für Abfrageaggregationen verarbeitet Daten im UNIX-Epochenformat jetzt ordnungsgemäß. Im Abschnitt [Abfragereferenz](/docs/services/discovery/query-reference.html#aggregations) finden Sie Informationen zu Aggregationen und zum Parameter `timeslice`.
- Es wurden Verbesserungen an den Fehlernachrichten vorgenommen.
- Das Java-SDK für den Service wurde aktualisiert. Details enthält die [API-Referenz](http://www.ibm.com/watson/developercloud/discovery/api/v1/?java).
- Die folgenden Einschränkungen für die Verwendung von Platzhaltern in Abfragen wurden gelöst und arbeiten jetzt ordnungsgemäß:

  - In einer Abfrage konnte jeweils nur ein einziger Platzhalter verwendet werden. Beispielsweise funktionierte `query-month:*ctober`, aber die Abfrage `query-month:*ctobe*` generierte einen Parsing-Fehler.
  - Platzhalter konnten nicht in Abfragen eingesetzt werden, die Großbuchstaben enthalten. Für das Schlüssel/Feld-Paar `{"borrower": "GOVERNMENT OF INDIA"}` gab beispielsweise `query-borrower:*ndia` Ergebnisse zurück, aber `query-borrower:*NDIA` nicht.

**Hinweis:** Platzhalter sind innerhalb von Ausdrücken in Abfragen nicht erforderlich. Für das Schlüssel/Feld-Paar `{"borrower": "GOVERNMENT OF TIMOR"}` gibt beispielsweise `query-borrower:"GOVERNMENT OF TIMOR"` Ergebnisse zurück, `query-borrower:"GOVERNMENT OF TI*OR"` jedoch nicht. Die Verwendung eines Platzhalters innerhalb von Ausdrücken ist nicht angebracht, weil alle Zeichen innerhalb der Anführungszeichen (`"`) eines Ausdrucks mit Escapezeichen versehen sind.

### 24. März 2017

- Zur Anzeige 'Einblicke in eigene Daten' in den Discovery-Tools wurde eine Filterung hinzugefügt.

### 15. März 2017

Die folgenden bekannten Probleme wurden festgestellt.

-  Alle aus HTML-, PDF- und Word-Dokumenten eingepflegten Felder werden mit dem Typ **string** versehen. JSON-Felder und berechnete Felder (z. B. Stimmungsbewertung) erhalten den definierten Typ.
- Die Operation `preview` führt derzeit keine Überprüfung auf verschachtelte JSON-Arrays in einem übergebenen JSON-Dokument durch. Der Service unterstützt derzeit keine verschachtelten JSON-Arrays. Ein Dokument mit verschachtelten Arrays kann daher die Operation `preview` erfolgreich durchlaufen, jedoch beim Einpflegeversuch fehlschlagen.
- Falls Sie beim Einpflegen Fehler mit der Nachricht `unsupported text language` feststellen, aktualisieren Sie Ihre Konfiguration mit der Aufbereitungsoption `"language": "english"`, damit der gesamte Text als Englisch interpretiert wird (siehe folgendes Beispiel).

```json
"enrichments": [
   {
     "enrichment": "alchemy_language",
     "source_field": "author.label",
     "options": {
       "extract": "taxonomy,entity,relation,doc-emotion,doc-sentiment,concept,keyword",
       "sentiment": true,
       "quotations": true,
       "language": "english"
     }
   }
 ]
```
{: codeblock}

Die folgenden Programmfehler wurden korrigiert.

- Die Leistung und Stabilität des Service wurde verbessert.

### 8. März 2017

 - Das Ausgabeprogramm wurde optimiert, unter anderem durch Hinzufügung neuer Zeitlimitwerte, um die Gesamtleistung zu verbessern.
 - Ein Programmfehler, der bewirkte, dass der Status für freie Umgebungen (Größe `0`) mit `pending` anstelle des echten Status gemeldet wurde, wurde behoben.
 - Die einzige Landessprache, die derzeit von {{site.data.keyword.discoveryshort}} unterstützt wird, ist Englisch (US) (`en_US`).

### 3. März 2017

- Die Anzeige 'Einblicke in eigene Daten' wurde zu den Discovery-Tools hinzugefügt.

### 26. Februar 2017

-     Die Leistung der {{site.data.keyword.discoverynewsshort}}-Umgebung wurde verbessert.
-  Der {{site.data.keyword.discoverynewsshort}}-Service gibt jeweils nur 50 Ergebnisse auf einmal zurück. Zur Umgehung verwenden Sie den Parameter `offset` in der Abfrage, um die Ergebnisse seitenweise zu ermitteln.
-  Sie können eine neue Konfiguration mit einem einzelnen Dokument übergeben, indem Sie den folgenden Befehl verwenden:

```bash
curl -X POST -u {benutzer}:{kennwort} -F "file=@wikipedia-sample.html" -F "configuration=$(cat config.json)" "https://gateway.watsonplatform.net/v1/environments/{umgebungs-id}/collections/{sammlungs-id}/documents?version=2016-12-01"
```
{: pre}
-  Die PDF- und Word-Konvertierungskomponenten des Service erzeugen als Zwischenschritt HTML. Der Service kann auf den HTML-Zwischenstand weitere Umwandlungen und Normalisierungen anwenden, bevor die abschließende Umwandlung in normalisiertes JSON stattfindet.

Die folgenden Programmfehler wurden korrigiert.

-  Fehlercodes wurden verbessert.
-  Verschiedene Errata in der Dokumentation wurden korrigiert.

### 16. Februar 2017

-  Mit CSS-Selektoren können Sie jetzt JSON-Felder auswählen, auf die Sie anschließend Aufbereitungen anwenden können. Informationen enthält der Abschnitt [Felder mittels CSS-Selektoren extrahieren](/docs/services/discovery/building.html#using-css).
-  Sie können nun die Größe einer Umgebung erhöhen, indem Sie den neuen Parameter `size: X` an die Methode [update-environment](http://www.ibm.com/watson/developercloud/discovery/api/v1/#update_environment) übergeben, wobei `X` für eine ganze Zahl zwischen 0 und 3 steht. Informationen zur Größe und zu den Attributen von Umgebungen enthält der Abschnitt über die Methode [create-environment](http://www.ibm.com/watson/developercloud/discovery/api/v1/#create_environment).

    **Hinweis:** Die Größe einer vorhandenen Umgebung kann nicht reduziert werden. Falls Sie Ihre Umgebung verkleinern wollen, bitten Sie den {{site.data.keyword.IBM}} Support um Unterstützung.

-  Ein neuer Abfrageoperator ist verfügbar. Der Operator `::!` wurde als monadischer Operator für 'Ist ungleich' hinzugefügt. Beispielsweise können Sie jetzt `query=feld::!wert` (ungleich) ausführen. Zuvor war `:!` der einzige ausschließende Operator für den Operator 'Enthält nicht' (z. B. `query=feld:!wert`).

Die folgenden Programmfehler wurden korrigiert.

-  Es wurden Sicherheitsupdates angewendet.
-  Die Statusnachrichten für Suchalerts wurden verbessert.

### 1. Februar 2017

Die folgenden Hinweise gelten speziell für Release 1.3.0 von Data Crawler.

-   Data Crawler zeichnet die Werte für `document_id`, die zum Hochladen von Dokumenten verwendet werden, und den Status des Uploads auf. Konvertierungshinweise werden außerhalb des Protokolls nicht gespeichert. Es gibt gegenwärtig kein Tool für die Interaktion mit diesen Daten. Sobald die Zeit es erlaubt, kann jedoch mit der Entwicklung solcher Tools gerechnet werden. Die Daten sind über eine H2-Datenbank zugänglich, die für die Verwendung eines fernen Datenbankmanagementsystems konfiguriert werden könnte.

### 16. Januar 2017

Die folgenden Hinweise gelten speziell für Release 1.2.5 von Data Crawler.

-  Data Crawler kann optional den Dokumentstatus sofort nach dem Hochladen einer Datei abfragen. Diese Prüfung gehört zum Dokumentuploadkonzept des Crawlers. Wenn sie aktiviert ist, ist es für den Crawler praktisch unmöglich, mehr Dokumente gleichzeitig hochzuladen, als der {{site.data.keyword.discoveryshort}}-Service parallel für den Benutzer verarbeiten kann.

    Als Nebeneffekt der Funktion `check_for_completion` kann der Crawler einen Benutzer auch darüber informieren, warum ein Dokument gegebenenfalls fehlgeschlagen ist. Alle Hinweise, die einem erfolgreich hochgeladenen, aber bei der Verarbeitung fehlgeschlagenen Dokument zugeordnet sind, werden im Crawlerprotokoll angezeigt. Die Hinweise werden nicht in eine verarbeitungsfähige Datei exportiert, aber IBM ist für einen entsprechenden Funktionsvorschlag offen.

### 5. Januar 2017

Die folgenden Hinweise beschreiben Probleme, die nach dem allgemein verfügbaren Release vom 15. Dezember 2016 festgestellt wurden.

-   Falls Sie ein Dokument mit einem Aufruf von `POST /v1/environments/{umgebungs-id}/collections/{sammlungs-id}/documents`
    oder `POST /v1/environments/{umgebungs-id}/collections/{sammlungs-id}/documents/[:{id}]` hinzufügen, gibt der Aufruf eine Dokument-ID und den Status **processing** zurück. Falls Sie anschließend das Dokument mit dem Aufruf `GET /v1/environments/{umgebungs-id}/collections/{sammlungs-id}/documents/[:{id}]` abfragen, verbleibt der Status bei **processing**, bis das Einpflegen abgeschlossen ist und sich der Status dann in **available** ändert.

    Falls Sie ein vorhandenes Dokument mit dem Aufruf `POST /v1/environments/{umgebungs-id}/collections/{sammlungs-id}/documents/[:{id}]` **aktualisieren**, gibt der entsprechende Aufruf **GET** den Status `available` selbst dann zurück, wenn der Service das aktualisierte Dokument noch nicht vollständig verarbeitet hat. Der Status `available` kann sich entweder auf das Originaldokument oder auf das aktualisierte Dokument beziehen. Sofern die Aktualisierungsoperation keinen Fehler zurückgibt, gibt es derzeit kein Verfahren, mit dem der Status des aktualisierten Dokuments ermittelt werden kann.

    Dieses Problem können Sie umgehen, indem Sie nach der Übergabe einer Dokumentaktualisierung bis zu 10 Minuten warten, bevor Sie versuchen, den aktualisierten Inhalt abzufragen.
-   Der Upload von JSON-Arrays ist nicht möglich. Um ein JSON-Array hochzuladen, müssen Sie jeden einzelnen Abschnitt separat hochladen. Beispielweise kann das folgende JSON-Array nicht in den Service hochgeladen werden:

    ```json
    [{
      "accepted": 1,
      "answer": "You shouldn't have any issues keeping it on all the time however some thing to consider is any counters you may have like the use of millis code . From the Arduino docs on millis a This number will overflow go back to zero after approximately 50 days. blockquote So for projects that are on for long periods of time you may not see an issue immediately but something like this could pop up and cause errors down the road. ",
      "answerScore": "49",
      "authorUserId": "3",
      "authorUsername": "Butzke",
      "downModVotes": 0,
      "id": 2,
      "subtitle": "I'm making a simple Arduino web server and I want to keep it turned on all the time. So it must endure to stay working continuously. I'm using an Arduino Uno with a Ethernet Shield. It's powered with a simple outlet power supply 5V 1A. My Questions Will I have any problems leaving the Arduino turned on all the time? li Is there some other Arduino board better recommended for this? li Are there any precautions that I need to heed regarding this? li ul ",
      "tags": "<arduino-uno><web-server><ethernet>",
      "title": "Is an Arduino capable of running 24 7?",
      "upModVotes": 49,
      "userId": "11",
      "userReputation": 4535,
      "username": "sachleen",
      "views": 3234
    }, {
      "accepted": 0,
      "answer": "A couple of things to keep in mind outside of Sachleen's mention of Milli's Like any electronics heat can be disruptive. The micro controller itself isn't likely going to be a huge issue from the perspective of heat but other components like the power supply might cause issues. li If your code uses EEPROMWrite a be aware that the EEPROM is only rated for something in the neighbourhood of 100 000 writes. li ul ",
      "answerScore": "24",
      "authorUserId": "3",
      "authorUsername": "Butzke",
      "downModVotes": 0,
      "id": 3,
      "subtitle": "I'm making a simple Arduino web server and I want to keep it turned on all the time. So it must endure to stay working continuously. I'm using an Arduino Uno with a Ethernet Shield. It's powered with a simple outlet power supply 5V 1A. My Questions Will I have any problems leaving the Arduino turned on all the time? li Is there some other Arduino board better recommended for this? li Are there any precautions that I need to heed regarding this? li ul ",
      "tags": "<arduino-uno><web-server><ethernet>",
      "title": "Is an Arduino capable of running 24 7?",
      "upModVotes": 24,
      "userId": "13",
      "userReputation": 489,
      "username": "Matthew G.",
      "views": 3234
    }]
    ```
    {: codeblock}

    Um diese Informationen in den Service hochzuladen, gliedern Sie das Array wie folgt auf und laden Sie jeden Abschnitt hoch:

    Abschnitt 1:

    ```json
    {
      "accepted": 1,
      "answer": "You shouldn't have any issues keeping it on all the time however some thing to consider is any counters you may have like the use of millis code . From the Arduino docs on millis a This number will overflow go back to zero after approximately 50 days. blockquote So for projects that are on for long periods of time you may not see an issue immediately but something like this could pop up and cause errors down the road. ",
      "answerScore": "49",
      "authorUserId": "3",
      "authorUsername": "Butzke",
      "downModVotes": 0,
      "id": 2,
      "subtitle": "I'm making a simple Arduino web server and I want to keep it turned on all the time. So it must endure to stay working continuously. I'm using an Arduino Uno with a Ethernet Shield. It's powered with a simple outlet power supply 5V 1A. My Questions Will I have any problems leaving the Arduino turned on all the time? li Is there some other Arduino board better recommended for this? li Are there any precautions that I need to heed regarding this? li ul ",
      "tags": "<arduino-uno><web-server><ethernet>",
      "title": "Is an Arduino capable of running 24 7?",
      "upModVotes": 49,
      "userId": "11",
      "userReputation": 4535,
      "username": "sachleen",
      "views": 3234
    }
    ```
    {: codeblock}

    Abschnitt 2:

    ```json
    {
      "accepted": 0,
      "answer": "A couple of things to keep in mind outside of Sachleen's mention of Milli's Like any electronics heat can be disruptive. The micro controller itself isn't likely going to be a huge issue from the perspective of heat but other components like the power supply might cause issues. li If your code uses EEPROMWrite a be aware that the EEPROM is only rated for something in the neighbourhood of 100 000 writes. li ul ",
      "answerScore": "24",
      "authorUserId": "3",
      "authorUsername": "Butzke",
      "downModVotes": 0,
      "id": 3,
      "subtitle": "I'm making a simple Arduino web server and I want to keep it turned on all the time. So it must endure to stay working continuously. I'm using an Arduino Uno with a Ethernet Shield. It's powered with a simple outlet power supply 5V 1A. My Questions Will I have any problems leaving the Arduino turned on all the time? li Is there some other Arduino board better recommended for this? li Are there any precautions that I need to heed regarding this? li ul ",
      "tags": "<arduino-uno><web-server><ethernet>",
      "title": "Is an Arduino capable of running 24 7?",
      "upModVotes": 24,
      "userId": "13",
      "userReputation": 489,
      "username": "Matthew G.",
      "views": 3234
    }
    ```
    {: codeblock}

### Allgemein verfügbares Release, 15. Dezember 2016

Die folgenden Hinweise gelten für das allgemein verfügbare Release des {{site.data.keyword.discoveryfull}}-Service.

#### Allgemeine Hinweise

-   Der Datentyp von Feldern kann derzeit nicht angegeben werden. Alle Felder werden als Text indexiert (Datentyp **string**).
-   Falls Sie zur Arbeit mit dem Service die API verwenden, müssen Sie bei jedem Aufruf die API-Version angeben. Die aktuelle API-Version ist **2016-12-01**.

    **Hinweis:** Die spezielle Version wird im allgemein verfügbaren Release nicht umgesetzt, muss jedoch aufgelistet sein, um die Kompatibilität mit künftigen Releases zu ermöglichen.

-   Sie können den Service mit einem in {{site.data.keyword.knowledgestudiofull}} erstellten angepassten Modell nutzen. Das angepasste Modell kann verwendet werden, um eingepflegte Dokumente aufzubereiten. Sie müssen die API verwenden, um das angepasste Modell in den {{site.data.keyword.discoveryshort}}-Service zu integrieren; die Integration mithilfe der Tools ist nicht möglich. Details enthält der Abschnitt [Integration mit {{site.data.keyword.knowledgestudiofull}}](/docs/services/discovery/integrate-wks.html "Sie können ein angepasstes  Modell aus {{site.data.keyword.knowledgestudiofull}} beim {{site.data.keyword.discoveryshort}}-Service integrieren, um angepasste Aufbereitungen bereitzustellen.").

#### Datenmanagement

-   Suchindizes werden nicht verschlüsselt.
-   Die Funktionen für Sicherung und Wiederherstellung können nicht durch den Benutzer gesteuert werden.

#### Umgebungen

-   Pro Serviceinstanz können Sie nur eine einzige Umgebung für das Hochladen von eigenen Daten erstellen.
-   Der {{site.data.keyword.discoveryshort}}-Service befindet sich in einer einzigen Verfügbarkeitszone (US South).
-   Derzeit sind keine Pläne des Typs 'Dedicated' und 'Premium' verfügbar.

#### Umgebungsgröße

-   Eine Umgebungsgröße können Sie nur beim Erstellen einer neuen Umgebung auswählen. Benutzer haben derzeit nicht die Möglichkeit, die Größe einer Umgebung zu ändern.
-   Die Auswahl einer Umgebungsgröße mit mehr Hauptspeicher erhöht die Leistung.
-   Es gibt gegenwärtig keine vorschriftsmäßigen Größenempfehlungen für bestimmte Anwendungsfälle.
-   Die angepasste Dimensionierung von {{site.data.keyword.knowledgestudiofull}}-Modellen können Sie nicht eigenständig vornehmen. Weitere Informationen erhalten Sie bei Ihrem {{site.data.keyword.IBM}} Ansprechpartner.

#### Einschränkungen für das Einpflegen

-   Die Einpflegerate ist gegenwärtig auf 100 gleichzeitige Operationen für das Einpflegen von Dokumenten begrenzt. Eine Anwendung, die Dokumente zum Einpflegen an den Service übergibt, muss HTTP-Fehler des Typs 429 beachten und die Einpflegeanforderungen entsprechend drosseln.
-   {{site.data.keyword.alchemylanguageshort}}-Aufbereitungen sind auf die ersten 50 KB pro Feld begrenzt.
-   Aufbereitungen aus angepassten {{site.data.keyword.knowledgestudiofull}}-Modellen sind nicht begrenzt, teilen Dokumente jedoch in 10-KB-Blöcke auf. Beziehungen werden nicht blockübergreifend annotiert.

#### Einschränkungen für Abfragen

-   Eine exzessive Arbeitslast durch Abfragen kann einen automatischen Neustart für den Suchindexprozess auslösen.
-   Anwendungen, die Abfragen ausgeben, müssen angemessene Grenzwerte für die Anzahl gleichzeitiger Abfagen umsetzen.

### Bekannte Probleme

-   Sie können ein Dokument nicht mithilfe der Tools löschen. Falls Sie ein Dokument löschen müssen, müssen Sie die in der API-Referenz unter [Dokument löschen](http://www.ibm.com/watson/developercloud/discovery/api/v1/#delete-doc) beschriebene API-Methode verwenden.

-   Die API unterstützt derzeit nicht das Abrufen einer Liste mit Hinweisen (Fehler und Warnungen), die während des Einpflegens von Dokumenten generiert wurden. Die Tools können daher keine Liste von Hinweisen für das Einpflegen anzeigen und es kann nicht ohne Aufwand ermittelt werden, welche Dokumente, die durch Data Crawler durchsucht wurden, gegebenenfalls nicht eingepflegt werden konnten.
-   Die Informationen zum Dokumentstatus sind nicht immer präzise.
    -   Falls eine Operation zum Einpflegen länger als das konfigurierte Zeitlimit von 10 Minuten dauert, meldet der Service, dass er das Dokument nicht kennt, bis die Operation zum Einpflegen vollständig ausgeführt wurde. Nach Abschluss der Operation ist der Dokumentstatus verfügbar und korrekt.
    -   Dokumente, die erfolgreich indexiert wurden, jedoch Fehler generiert haben, können kurzzeitig den Status **failed** aufweisen, bis sie vollständig im Index festgeschrieben worden sind. Nach dem Festschreiben des Dokuments im Index ist der aufgelistete Status korrekt.
-   Das Ersetzen eines bestimmten Dokuments mithilfe der Tools ist nicht möglich. Falls Sie dies versuchen, wird das zweite Dokument als separates Dokument hochgeladen. Wenn Sie die API verwenden und die ID des zu ersetzenden Dokuments kennen, können Sie diese Operation ausführen. Entsprechende Anweisungen finden Sie in der API-Referenz unter [Dokument aktualisieren](http://www.ibm.com/watson/developercloud/discovery/api/v1/#update-doc). Bei Verwendung von Data Crawler wird durch den Upload eines aktualisierten Dokuments über dieselbe URL wie ein vorheriges Dokument das Originaldokument ersetzt.
-   Falls Sie die Tools verwenden, um die Aufbereitungen in Ihrer Konfiguration zu bearbeiten, können Sie nur Aufbereitungen bearbeiten, die für eine Extraktion verwendet werden. Wenn Sie andere Aufbereitungen hinzufügen oder bearbeiten wollen (z. B. angepasste Aufbereitungen aus einem {{site.data.keyword.knowledgestudiofull}}-Modell), müssen Sie die API verwenden. Informationen finden Sie in der API-Referenz unter [Konfiguration aktualisieren](http://www.ibm.com/watson/developercloud/discovery/api/v1/#replace_configuration).
-   Die folgenden Hinweise gelten speziell für Data Crawler.
    -   Data Crawler versucht, Uploads zu wiederholen, bis ein Uploadfehler festgestellt wird.
    -   Data Crawler kann die Wiederholung nicht für Dokumente ausführen, die erfolgreich hochgeladen wurden, deren Konvertierung oder Indexierung jedoch fehlgeschlagen ist.
    -   Data Crawler besitzt keine Funktion für die Überprüfung des nachgelagerten Status und versucht, später fehlgeschlagene URLs erneut hochzuladen.
    -   Es kann nicht ohne Aufwand ermittelt werden, welche Dokumente durch Data Crawler eingepflegt wurden. Wenn Sie Data Crawler beispielsweise für eine Gruppe von 500 Dokumenten ausführen, meldet Data Crawler möglicherweise Fehler bei der Übergabe von 65 Dokumenten für eine Sammlung von insgesamt 212 Dokumenten. Der Status der übrigen 223 Dokumente ist unbestimmt.

        Eine Ausweichlösung ist verfügbar, jedoch komplex und umfasst einen direkten Aufruf der API. Bitten Sie in einem solchen Fall den {{site.data.keyword.IBM}} Support um Unterstützung.-   Die Java-, Python- und Node.js-SDKs für {{site.data.keyword.discoveryshort}} bieten nicht die gesamte Funktionalität, die von der REST-Standard-API (cURL) bereitgestellt wird. Es gibt nicht für alle cURL-Methoden funktionale Entsprechungen in den anderen SDKs und nicht alle Methoden der anderen SDKs bieten dieselben Funktionen wie ihre cURL-Äquivalente. Anders ausgedrückt bieten die Java-, Python- und Node.js-SDKs derzeit nur eine Untergruppe der Funktionalitäten der cURL-API.
-   Falls Sie die Word-Konvertierungskomponente verwenden, ist ein Überschriftenabgleich mit dem Schlüssel `style` genauer und effizienter als die Verwendung des Schlüssels `level`.
