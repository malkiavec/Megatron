---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-15"

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

# Tipos de relación

En la siguiente tabla hay una lista de los posibles tipos de relación que devuelve el enriquecimiento de [Extracción de relaciones](/docs/services/discovery/building.html#relation-extraction).
{: shortdesc}

| Relación | Descripción |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| affectedBy      | Existe entre una entidad y un suceso que tiene una clara direccionalidad y que afecta a la entidad. |
| affiliatedWith  | Existe entre dos entidades que tienen una afiliación o están relacionadas de forma similar. |
| ageOf           | Relaciona una edad con una entidad. |
| agentOf         | Existe entre una entidad y un suceso en el que la entidad desempeña el rol más activo según el texto. No debería ser necesario más información de contexto adicional.|
| authorOf        | Existe entre una persona y un TitleWork que dicha persona ha creado. |
| awardedBy       | Existe entre un Award o Degree y la persona u organización por la que fue premiada o titulada. |
| awardedTo       | Existe entre un Award o Degree y la persona u organización que fue premiada o titulada. |
| basedIn         | Existe entre una organización y el lugar donde principalmente, únicamente o intrínsecamente se encuentra. |
| before          | Indica la relación temporal "before" (antes) entre dos Times o Events. Se indica únicamente cuando el texto claramente especifica la relación. |
| bornAt          | Existe entre una Person o Animal y el lugar en donde nació. |
| bornOn          | Existe entre una Person o Animal y la Date o Time en que nació. |
| capitalOf       | Existe entre una capital y su país, estado o provincia. Se indica únicamente cuando el texto explícitamente indica la relación (no se base en el conocimiento exterior). |
| citizenOf       | Existe entre una persona y la GeopoliticalEntity de la que es ciudadano la persona. |
| clientOf        | Existe entre dos entidades cuando una corresponde a un cliente directo de negocio de la otra (es decir, paga determinados servicios o productos). |
| colleague       | Existe entre dos People que son parte de la misma Organization. |
| competitor      | Existe entre dos GeopoliticalEntities u Organizations involucradas en una competición económica. |
| contactOf       | Indica información de contacto con una entidad. |
| diedAt          | Existe entre un Person o Animal y el lugar donde murió. |
| diedOf          | Existe entre un Person o Animal y la causa por la que murió.|
| diedOn          | Existe entre un Person o Animal y la Date o Time en la que murió. |
| dissolvedOn     | Existe entre una entidad como, por ejemplo, una Organization y la Date o Time en la que fue disuelta. |
| educatedAt      | Existe entre una Person y la Organization en la que se formó. |
| employedBy      | Existe entre dos entidades cuando una paga a la otra por determinados servicios o por un trabajo. Debe existir una recompensa económica. En muchos casos, indicar esta relación precisa de un conocimiento exterior. |
| foundedOn       | Existe entre una entidad como, por ejemplo, una Organization y la Date o Time en la que fue fundada. |
| founderOf       | Existe una Person o GeopoliticalEntity y una entidad como, por ejemplo, la Organization que fundó. |
| hasDisease      | Indica una Person o Animal que tiene o ha tenido una Disease. |
| hasMoney        | Indica una entidad como, por ejemplo una persona, que tiene o ha tenido Money. |
| instrumentOf    | Existe entre una entidad como, por ejemplo, una Weapon y un Event en el que la entidad es o fue utilizada para que ocurriese. |
| locatedAt       | Existe entre una entidad y su ubicación física. |
| managerOf       | Existe entre una Person y otra entidad como, por ejemplo, una Person u Organization que se encarga de gestionar su trabajo. |
| measureOf       | Indica una Measure concreta como, por ejemplo, el peso o altura, de una entidad. |
| memberOf        | Existe entre una entidad como, por ejemplo, una Person, Organization, o GeopoliticalEntity y otra entidad a la que pertenece. |
| near            | Existe entre dos entidades que se encuentran cerca entre sí físicamente. |
| overlaps        | Indica que dos Times o Events se solapan temporalmente. Se indica únicamente cuando el texto claramente especifica la relación. |
| ownerOf         | Existe entre una entidad como, por ejemplo, una Person, Organization, o GeopoliticalEntity y una entidad que la posee de forma permanente o temporal. |
| parentOf        | Existe entre una Person o Animal y sus hijos o hijastros. |
| participantIn   | Existe entre un participante como, por ejemplo, una Person, Animal, Organization o GeopoliticalEntity y un suceso en la que la entidad participa o ha participado. |
| partner         | Existe entre dos GeopoliticalEntities u Organizations involucradas en una cooperación económica. |
| partOf          | Existe entre una entidad pequeña y otra mayor del mismo tipo o de un tipo relacionado en el que la segunda entidad incluye a la primera. Si las entidades son Events, el primero debe darse dentro del intervalo de tiempo del segundo. |
| partOfMany      | Existe entre entidades pequeñas y grandes del mismo tipo o de tipos relacionados en los que la segunda entidad, que debe ser plural, incluye la primera, y que a su vez puede estar formada por una o varias entidades. |
| playsRoleOf     | Existe entre una Persona y un rol específico en el que dicha persona participa o ha participado un acto. |
| populationOf    | Existe entre un Cardinal y una entidad como, por ejemplo una organización o país al que el número representa.    |
| productOf       | Existe entre un Product o TitleWork y la Organization que lo ha creado. |
| quantityOf      | Indica un cardinal que corresponde a la cantidad o el importe de una segunda entidad. |
| rateOf          | Existe entre un Rate y un suceso cuya frecuencia de aparición especifica. |
| relative        | Existe entre un Person o Animal y otra Person o Animal con una relación de parentesco cuando no es aplicable una relación más específica. |
| residesIn       | Existe entre una entidad viva y la ubicación en la que reside de forma permanente. |
| shareholdersOf  | Existe entre una Person, Organization o GeopoliticalEntity y una Organization en la que la primera entidad participa. |
| siblingOf       | Existe entre una Person o Animal y sus hermanos o hermanastros. |
| spokespersonFor | Existe entre una Person y una entidad a la que representa. Se indica únicamente cuando el texto explícitamente indica la relación (no se base en el conocimiento exterior). |
| spouseOf        | Existe entre dos People que forman una relación formal. |
| subsidiaryOf    | Existe entre dos Organizations cuando la primera es una subsidiaria de la segunda, es decir, que la primera entidad tiene una autonomía considerable a pesar de estar bajo el control de la segunda. |
| timeOf          | Indica la Date, Time o Duration en la que se ha producido un suceso; se ha publicado, realizado o difundido un TitleWork; o se ha elaborado un borrador, se ha creado, se ha aprobado o se ha abolido una ley.     

## Tipos de entidad específicos a la extracción de relaciones
{: #specific-entity-types}

El enriquecimiento de relaciones puede identificar a las siguientes entidades: 

|Tipo de entidad|
|---|
|Age|
|Anatomy|
|Animal|
|Award|
|Cardinal|
|Crime|
|Date|
|Degree|
|Duration|
|EmailAddress|
|Event|
|EventBusiness|
|EventCommunication|
|EventCustody|
|EventDemonstration|
|EventEducation|
|EventElection|
|EventGathering|
|EventLegal|
|EventLegislation|
|EventMeeting|
|EventPerformance|
|EventPersonnel|
|EventViolence|
|Facility|
|Food|
|GeographicFeature|
|GeopoliticalEntity|
|HealthCondition|
|Law|
|Location|
|Money|
|Measure|
|NaturalEvent|
|Organización|
|Ordinal|
|Percent|
|Person|
|Phone|
|Plant|
|Product|
|SportingEvent|
|Substance|
|Ticker|
|Time|
|TitleWork|
|Vehicle|
|Weapon|
|Weather|
|Web|
