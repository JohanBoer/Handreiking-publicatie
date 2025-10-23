# Domain Driven Design

**Domain Driven Design**, afgekort DDD, is een methodiek waarin de nadruk ligt op het business domein, een business
domein gedreven ontwerp.

Een van de kernprincipes van DDD is dat er **ubiquitous language** gebruikt wordt. Hiermee wordt bedoeld dat er een
gemeenschappelijke taal is die door zowel ontwikkelaars als domeinexperts wordt gebruikt. Deze dient als basis voor de
terminologie en structuren in gesprekken, in ontwerpen én in de code.

Gedreven door het business domein en het scherp opdelen van een complex domein in logische subdomeinen, ontstaan ook
duidelijke verantwoordelijkheden. Met DDD worden deze subdomeinen gevolgd in het ontwerp van systemen. Zo'n subdomein
en/of hoe gekozen wordt om verantwoordelijkheden in één systeem te beheren, wordt in DDD een **bounded context**
genoemd.

In DDD draait alles om het bouwen van een model dat direct de zakelijke regels en begrippen van het domein weerspiegelt;
alles draait om een goede **afstemming op domeinmodellen**. [[cqrs]] past hier goed bij, omdat meestal verschillende
modellen bestaan voor **lees- en schrijfbewerkingen** binnen een complex domein. Het command-model in CQRS kan zich
bijvoorbeeld richten op de werkelijke bedrijfslogica voor het wijzigen van de status, terwijl het query-model puur is
geoptimaliseerd voor het ophalen van gegevens.

[[event-sourcing]] is geen vereiste voor DDD en/of CQRS, maar sluit wel heel goed aan. In DDD worden gebeurtenissen
(events) vaak gebruikt om veranderingen binnen een bounded context te modelleren. Event sourcing gaat nog een stap
verder door deze gebeurtenissen als bron van waarheid te beschouwen. Het sluit naadloos aan op DDD, omdat gebeurtenissen
domeinspecifiek zijn en betekenisvol voor zowel het business- als ontwikkelteam.

Kortom, [[domain-driven-design]] biedt het conceptuele kader, een methodiek en de terminologie om gedreven rondom een
business domein tot goede ontwerpen te komen. [[cqrs]] en [[event-sourcing]] zijn architectuurpatronen die dit goed
ondersteunen en bieden principes voor effectief implementatie.

## Referenties

Meer informatie Domain Driven Design:

1. **Wikipedia** over [Domain Driven Design](https://en.wikipedia.org/wiki/Domain-driven_design)

2. **AxonIQ Docs** | [Domain Driven Design](https://www.axoniq.io/concepts/domain-driven-design)

    AxonIQ is het bedrijf achter het Axon Framework, een Java framework om Event Sourcing systemen te
   bouwen. Lees bijvoorbeeld:

3. **Books**:

   - <span id="the-blue-book" >**'The blue book'**</span>: _“[Domain-Driven Design: Tackling Complexity in the Heart of Software](https://www.domainlanguage.com/ddd/blue-book/)”_ door
     Eric Evans
   - <span id="the-red-book" >**'The red book'**</span>: _“[Implementing Domain-Driven
     Design](https://www.dddcommunity.org/book/implementing-domain-driven-design-by-vaughn-vernon/)”_
     door Vaughn Vernon
   - _“Patterns, Principles, and Practices of Domain Driven Design”_ door Scott Millett en Nick Tune

