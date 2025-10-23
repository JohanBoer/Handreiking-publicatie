# De omgeving en grenzen van een register

**Een register heeft betekenis door het proces dat het ondersteunt.** Om te begrijpen waar de
grenzen liggen, beginnen we bij het [vijflaagsmodel van Common
Ground](https://www.gemmaonline.nl/wiki/Common_Ground_vijflaagsmodel):

|  Laag  | Naam                 | Wat                                                       |
| :----: | -------------------- | --------------------------------------------------------- |
| **5**  | **Interactie**       | Gebruikersinterfaces, kanalen en toegang                  |
| **4**  | **Procesinrichting** | Bedrijfsprocessen, bedrijfsregels en informatiestructuren |
| **3**  | **Connectiviteit**   | Veilige verbindingen                                      |
| **2**  | **Diensten**         | Datadiensten, APIs en services                            |
| **1**  | **Databronnen**      | Registers, bijhouding en vastlegging                      |
| (**0** | **Infrastructuur**   | Hardware en infrastructuur)                               |

Een register bevindt zich in laag 1 (databronnen) en laag 2 (diensten). Een register sluit aan bij
laag 4 (procesinrichting) door de **informatiestructuren** van het proces: de conceptuele modellen
die beschrijven welke informatie het proces nodig heeft en produceert.

## Autonomie en gemeenschappelijkheid

Binnen [Common Ground](https://commonground.nl/) ligt de **autonomie van gemeenten** bij de
interactielaag (hoe burgers worden bediend) en de procesbesturing (hoe het werk wordt
georganiseerd). Elke gemeente kan eigen keuzes maken in werkwijze en gebruikersinteractie.

De **_common ground_** - wat gemeenschappelijk is - ligt bij het domeinmodel: welke acties mogelijk
zijn binnen een domein en welke gevolgen deze hebben. Dit zorgt voor interoperabiliteit terwijl
gemeenten hun autonomie behouden.

Gemeenten zijn gebruikt hier als voorbeeld, want dit geldt voor alle organisaties waar autonomie en
gemeenschappelijkheid een rol spelen, oftewel een gedeeld domein betreffen.

## Registergrenzen: domein

Een register is een verzameling geordende informatie. De grenzen van de verzameling worden net als
de betekenis en samenhang van de in het register opgeslagen informatie bepaald vanuit het **domein**
dat voor het register verantwoordelijk is. Anders dan in de
[wiskunde](https://nl.wikipedia.org/wiki/Domein_(wiskunde)) kunnen we voor registers niet precies
aangeven waar het ene domein ophoudt en het volgende begint. Analoog aan de definitie van [Eric
Evans in de context van Domain Driven Design](https://en.wikipedia.org/wiki/Domain-driven_design)
beschouwen we een domein daarom als "een sfeer van kennis, invloed of activiteit". Deze definitie
veronderstelt een zekere mate van samenhang. Tegelijkertijd kan het binnen één domein voorkomen dat:

- dezelfde concepten verschillend geïnterpreteerd worden,
- regels en gedrag niet consistent zijn, en
- bedrijfsprocessen niet op elkaar zijn afgestemd.

Voor wie zoekt naar aanknopingpunten over welke informatie binnen 'hoort' binnen een te ontwerpen
register en welke buiten de registergrenzen zou moeten vallen, biedt het denken in 'sferen'
onvoldoende aanknopingspunten. Daarom introduceren we **bounded context** als begrenzend begrip. Ook
dit concept is ontleend aan [Domain Driven
Design](https://en.wikipedia.org/wiki/Domain-driven_design)

## Bounded context

Binnen een domein kunnen meerdere subdomeinen of taakgebieden bestaan. Daarbij horen
verantwoordelijkheden, die zijn toegekend aan specifieke teams, afdelingen of bedrijfseenheden. Zij
worden ondersteund door eigen semantiek, processen en regels. Deze zaken kunnen worden beschreven in
een **model**: een systeem van abstracties dat beschrijft hoe men vanuit een taakgebied naar de
wereld kijkt en reageert op veranderingen in de buitenwereld. Zo'n model is beschreven in
**gemeenschappelijke taal** die binnen het hele taakgebied begrepen wordt. Model en taal beschrijven
dus een voor betrokkenen herkenbare 'blauwdruk' van het taakgebied, die (onder andere) de basis kan
vormen voor het ontwerp van een register. Een in gemeenschappelijke taal ondubbelzinnig en
samenhangend gemodelleerd taakgebied noemen we een '**bounded context**'.

Het belang van het erkennen van bounded contexten wordt door Eric Evans in ['the Blue
Book'](https://www.oreilly.com/library/view/domain-driven-design-tackling/0321125215/) als volgt
beschreven:

> "A bounded context delimits the applicability of a particular model so that team members have a
clear and shared understanding of what has to be consistent and how it relates to other contexts.
Within that context, work to keep the model logically unified, but do not worry about applicability
outside those bounds. In other contexts, other models apply, with differences in terminology, in
concepts and rules, and in dialects of the ubiquitous language _[red. gemeenschappelijke taal]_. By
drawing an explicit boundary, you can keep the model pure, and therefore potent, where it is
applicable. At the same time, you avoid confusion when shifting your attention to other contexts.
Integration across the boundaries necessarily will involve some translation, which you can analyze
explicitly."

Uit het bovenstaande blijkt dat de ambiguïteiten die we op domeinniveau nog konden tegenkomen binnen
een bounded context (idealiter) verdwijnen. Hier geldt (zoveel mogelijk) dat:

- dezelfde concepten eenduidig geïnterpreteerd worden (op basis van gemeenschappelijke taal),
- regels en gedrag consistent zijn, en
- bedrijfsprocessen op elkaar aansluiten.

## 'Wellbounded' registers

Bestaande registers bestrijken vaak meerdere bounded contexten. Zo zou je bijvoorbeeld binnen de
Basisregistratie Personen (BRP) bijgehouden informatie over verblijfplaats, verblijfsrecht,
kiesrecht en reisdocumenten ieder als 'eigen' bounded context kunnen beschouwen. Als je dat
onderschrijft en op basis daarvan nieuwe registers zou gaan ontwerpen en ontwikkelen, loop je tegen
een aantal (nieuwe) problemen aan:

- **Integratiecomplexiteit** (met name ten opzichte van registers met een 'breder' bereik).
  Registers moeten worden verbonden middels API's, events of gegevenssynchronisatie.
- **Hoge initiële leercurve.** Ontwerp en ontwikkeling van registers vereist diepgaande
  domeinkennis.
- **Lagere ontwikkelsnelheid.** Opdoen van domeinkennis en omzetten daarvan naar modellen en code
  vraagt tijd.

Tegelijkertijd worden aan overheidsregisters bijzondere eisen gesteld, onder meer als het gaat om
kwaliteit en betrouwbaarheid. Onderstaande voordelen van het koppelen van registers aan een (of één)
bounded context ondersteunen deze eisen, en wegen wat ons betreft zwaarder dan de nadelen:

- **Duidelijkheid**. Registers omvatten ondubbelzinnige terminologie en logica.
- **Consistentie**. Registers omvatten logisch consistente set regels en modellen.
- **Autonomie**. Registers in verschillende bounded contexten kunnen onafhankelijk van elkaar werken
  en (door)ontwikkeld worden.

Daarom doen we de volgende aanbevelingen voor het begrenzen van registers:

1. Een register valt samen met een (en één) bounded context, en dus
2. bepalen de bijhoudingsverantwoordelijke(n) de registergrenzen

## Bepalen van de 'bounds'

In de praktijk laten de 'bounds' van een context zich niet altijd gemakkelijk herkennen en
afbakenen. Bovendien kunnen bounded contexten onder invloed van impliciete of uitgesproken belangen
worden 'opgerekt' of juist verkleind. In algemene zin is moeilijk te zeggen wanneer voor een
register de 'ideale' bounded context is gevonden. Wel zijn enkele aanwijzingen voor een te ruime of
te krappe afbakening te geven. Deze zijn hieronder beschreven.

Indicatoren en symptomen (van sterk naar zwakker) voor een te ruime bounded context:

1. **Gebrek aan gemeenschappelijke taal.** Er is discussie over concepten en betekenis, betrokkenen
   hanteren verschillend jargon.
2. **Regels en gedrag niet in samenhang te brengen.** Het lukt niet tot een samenhangend model te
   komen.
3. **Afwijkende werkwijze(n).** Bedrijfsprodcessen zijn niet te verenigen.
4. **Ontwerp-/owikkeltraject heeft onwenselijke overhead.** Het ontwerp-/ontwikkelteam is te groot
   (geworden).
5. **(Vermijdbare) overschrijding van team- en/of organisatiegrenzen.** Conflict tussen eigenaren
   en/of verantwoordelijken.
6. **Registeronderdelen vereisen verschillende opslag- en/of integratietechniek.** Niet-verenigbare
   technische vereisten.

Indicatoren en symptomen (van sterk naar zwakker) voor een te krappe bounded context:

1. **Registeroverstijgende consistentiewaarborgen vereist.**
   [Saga's](https://www.baeldung.com/cs/saga-pattern-microservices) zijn nodig om transacties
   gedistribueerd af te handelen.
2. **Model beschrijft domein zonder zelfstandig bestaansrecht.** Gegevens in een register hebben
   ‘los’ geen enkel bestaansrecht en zijn niet te generaliseren voor gebruik in andere domeinen.

## Uitvoeringsproces op hoofdlijnen

Het uitvoeringsproces binnen een domein volgt een herkenbaar patroon. Door dit patroon te begrijpen,
wordt duidelijk waar het register precies bijdraagt en waar de grenzen liggen.

// **TODO** Vereenvoudigd plaatje van een administratief uitvoeringsproces (process flow plaatje?):
Signaal -> Taak -> Gevolg -> Presentatie

**Stap 1: Signaal ontvangen** Een proces start altijd met een signaal - een melding dat er iets is
gebeurd wat aandacht vraagt. Dit signaal kan van buiten het domein komen (bijvoorbeeld een melding
van een burger) of van binnen (bijvoorbeeld een (automatische) controle die iets detecteert).

**Stap 2: Taken creëren** Het proces beoordeelt het signaal en bepaalt welke acties nodig zijn. Deze
acties worden vastgelegd als taken. Een signaal kan leiden tot één taak, meerdere taken, of soms
geen taken als geen actie nodig is.

**Stap 3: Taken uitvoeren** Elke taak wordt uitgevoerd volgens de regels van het domein. Dit kan
handmatige verificatie inhouden, automatische berekeningen, of andere domeinspecifieke activiteiten.

**Stap 4: Gevolgen vastleggen** Het uitvoeren van taken levert gevolgen op - dit zijn de definitieve
veranderingen die het domein accepteert als geldig. Deze gevolgen vormen de waarheid voor dit
domein. Ze beschrijven wat er is gebeurd: een persoon is verhuisd, een huwelijk is voltrokken, een
kind is geboren, een bedrijf is ingeschreven, een eigendom is overgedragen.

**Stap 5: Presentatie opmaken** De gevolgen worden niet rechtstreeks gedeeld, maar gebruikt om
projecties op te maken die aansluiten bij specifieke informatiebehoeften. Een verhuizing kan
bijvoorbeeld leiden tot verschillende presentaties: een uittreksel voor de gemeente, een
adreswijziging voor de belastingdienst, of een notificatie voor de zorgverzekeraar. Elke
presentatie[^1] toont alleen de informatie die relevant is voor de ontvangende partij.

Deze cyclus vormt de kern van elk register-ondersteund proces. Het register bewaart de gevolgen en
stelt ze beschikbaar voor raadpleging.

![Gedetailleerd uitvoeringsproces dat het register ondersteunt](/assets/uitvoeringsproces.svg)
_Figuur 2: Gedetailleerd uitvoeringsproces dat het register ondersteunt_

### Het domeinmodel als kern

Het **domeinmodel** definieert wat binnen het domein mogelijk is. Het beschrijft:

- **Taakdefinities**: Welke acties mogelijk zijn binnen het domein
- **Taakverwerkingsregels**: Hoe taken worden uitgevoerd en welke gevolgen ze hebben
- **Presentatiedefinities**: Welke informatie in welke vorm beschikbaar gesteld wordt
- **Presentatieverwerkingsregels**: Hoe gevolgen worden omgezet naar specifieke informatiebehoeften

**Signaalverwerking staat buiten het domeinmodel.** Allerlei signalen kunnen op het proces afkomen.
De signaalverwerking interpreteert deze naar het domeinmodel toe: welke van de beschikbare taken
moet worden uitgevoerd?

Het domeinmodel vormt de kern van wat het register ondersteunt - de mogelijke acties en hun
gevolgen.

### Signaal ontvangen en interpreteren

- Een gebeurtenis binnen of buiten het domein leidt tot een _Signaal_
- _Signaalverwerking_ beoordeelt of dit signaal relevant is voor het domein
- Relevante signalen worden vertaald naar acties die het domein kan uitvoeren

### Taken definiëren en uitvoeren

- Uit het signaal ontstaan één of meerdere _Taken_ die binnen het domein uitgevoerd kunnen worden
- _Taakuitvoering_ voert deze taken uit volgens de regels van het _Domeinmodel_
- Taken volgen _Taakdefinities_ en _Taakverwerkingsregels_ uit het domeinmodel

### Gevolgen vastleggen

- Uitgevoerde taken leiden tot _Gevolgen_ - de daadwerkelijke veranderingen in het domein
- Deze gevolgen vormen de nieuwe waarheid voor dit domein

### Informatie beschikbaar stellen

- _Presentatieopmaking_ creëert verschillende _Presentaties_ op basis van de gevolgen
- Elke presentatie is afgestemd op specifieke informatiebehoeften volgens _Presentatiedefinities_ en
  _Presentatieverwerkingsregels_ uit het domeinmodel
- Presentaties kunnen als nieuwe signalen dienen voor vervolgprocessen in eigen of andere domeinen

## Applicatieve ondersteuning met het register

Het uitvoeringsproces krijgt concrete vorm in een applicatiearchitectuur. Het register ondersteunt
dit proces door de juiste componenten en datastromen in te richten. Ultiem is een (business)
domeinmodel gelijk aan een register, één _bounded context_ met eigen regels en begrippen, zoals
bedoeld in [[Domain-Driven Design]]. Veel vaker is het zo dat er meerdere bounded contexten te
onderscheiden zijn in één business domeinmodel[^2]. Dit heeft te maken met verantwoordelijkheden en
technologie _stacks_ en hebben vaak ook historische redenen; de verzameling van applicaties die door
de tijd heen ontwikkeld zijn. Toch tekenen we hier de eenvoudige en ultieme situatie als
uitgangspunt.

![Applicatieve ondersteuning en architectuurelementen waaruit het register
bestaat](/assets/registeranatomie.svg) _Figuur 3: Applicatieve ondersteuning en
architectuurelementen waaruit het register bestaat_

### Van proces naar applicatie

Het abstracte proces wordt concreet door deze architectuurcomponenten:

### Notificatie → Command (Signaalverwerking)

- **Notificatieprocessor** ontvangt _notificaties_ van binnen en buiten het domein
- Beoordeelt relevantie voor het eigen domein door raadpleging van projecties
- Vertaalt relevante notificaties naar _commands_ volgens domeinconventies

### Command → Effecten (Taakuitvoering)

- **Commandprocessor** ontvangt commands en bepaalt welke _effecten_ ontstaan
- Voert domeinregels uit en valideert tegen bestaande gegevens via projecties
- Effecten beschrijven de daadwerkelijke veranderingen binnen het domein

### Effecten → Projecties (Presentatieopmaking)

- **Effectprocessor** maakt _projecties_ op basis van effecten
- Projecties bevatten alleen informatie uit het eigen domein ('data bij de bron')
- Elke projectie is afgestemd op specifieke (groepen van)[^1] informatiebehoeften

### Register = Commands + Effecten + Projecties

Het register bestaat uit:

- **Commands**: De opdrachten aan het register, aangeboden met de intentie daarin een verandering
  aan te brengen
- **Effecten**: De waarheid van het domein - wat er werkelijk is gebeurd
- **Projecties**: Verschillende views op deze waarheid voor verschillende gebruikers

**Syntheses**[^3] (views die meerdere domeinen combineren) vallen buiten het register en verdienen
eigen architectuur.

[^1]: Dit is conceptueel juist, maar zeker geen dagelijkse praktijk. In de informatiebehoeften van
    verschillende afnemers zijn vaak overeenkomstigheden te vinden, zodat groepering voor de hand.
    Richtlijnen en overwegingen gaan nog (elders) beschreven worden.

[^2]: [No, Your Domains and Bounded Contexts Don’t Map 1 on
    1](https://verraes.net/2025/08/domain-and-bounded-contexts-dont-map-one-on-one/) - Mathias
    Verraes.

[^3]: Naar [Chronolexografie](https://chronolexografie-3e7a8b.gitlab.io/), een conceptueel model en
    specifieke architectuur voor het digitaal vastleggen en bijhouden van de rechtstoestand. De
    _projecties_ in bovenstaand artikel zijn te relateren aan de _reductie_ uit Chronolexografie.
    Met _synthese_ wordt in beide artikelen geduid op analyse en _view_ op meer dan alleen
    projecties en reducties uit registers. Het betreft vaak uitgebreidere verwerkingen,
    transformaties en combinatie met meerdere projecties uit verschillende registers.
