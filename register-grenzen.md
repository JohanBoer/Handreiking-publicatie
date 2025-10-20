[---]:
[title: De omgeving en grenzen van een register]:
[draft: true]:
[description: Wat is de omgeving van een register en waar liggen de grenzen van een register]:
[preliminary: true]:
[---]

# De omgeving en grenzen van een register

**Een register heeft betekenis door het proces dat het ondersteunt.** Om te begrijpen waar de grenzen liggen, beginnen
we bij het [vijflaagsmodel van Common Ground](https://www.gemmaonline.nl/wiki/Common_Ground_vijflaagsmodel):

|  Laag  | Naam                 | Wat                                                       |
| :----: | -------------------- | --------------------------------------------------------- |
| **5**  | **Interactie**       | Gebruikersinterfaces, kanalen en toegang                  |
| **4**  | **Procesinrichting** | Bedrijfsprocessen, bedrijfsregels en informatiestructuren |
| **3**  | **Connectiviteit**   | Veilige verbindingen                                      |
| **2**  | **Diensten**         | Datadiensten, APIs en services                            |
| **1**  | **Databronnen**      | Registers, bijhouding en vastlegging                      |
| (**0** | **Infrastructuur**   | Hardware en infrastructuur)                               |

Een register bevindt zich in laag 1 (databronnen) en laag 2 (diensten). Een register sluit aan bij laag 4
(procesinrichting) door de **informatiestructuren** van het proces: de conceptuele modellen die beschrijven welke
informatie het proces nodig heeft en produceert.

## Autonomie en gemeenschappelijkheid

Binnen Common Ground ligt de **autonomie van gemeenten** bij de interactielaag (hoe burgers worden
bediend) en de procesbesturing (hoe het werk wordt georganiseerd). Elke gemeente kan eigen keuzes maken in werkwijze en
gebruikersinteractie.

De **_common ground_** - wat gemeenschappelijk is - ligt bij het domeinmodel: welke acties mogelijk zijn binnen een
domein en welke gevolgen deze hebben. Dit zorgt voor interoperabiliteit terwijl gemeenten hun autonomie behouden.

Gemeenten zijn gebruikt hier als voorbeeld, want dit geldt voor alle organisaties waar autonomie en
gemeenschappelijkheid een rol spelen, oftewel een gedeeld domein betreffen.

## Uitvoeringsproces op hoofdlijnen

Het uitvoeringsproces binnen een domein volgt een herkenbaar patroon. Door dit patroon te begrijpen, wordt duidelijk
waar het register precies bijdraagt en waar de grenzen liggen.

// **TODO** Vereenvoudigd plaatje van een administratief uitvoeringsproces (process flow plaatje?): Signaal -> Taak ->
Gevolg -> Presentatie

**Stap 1: Signaal ontvangen** Een proces start altijd met een signaal - een melding dat er iets is gebeurd wat aandacht
vraagt. Dit signaal kan van buiten het domein komen (bijvoorbeeld een melding van een burger) of van binnen
(bijvoorbeeld een (automatische) controle die iets detecteert).

**Stap 2: Taken creëren** Het proces beoordeelt het signaal en bepaalt welke acties nodig zijn. Deze acties worden
vastgelegd als taken. Een signaal kan leiden tot één taak, meerdere taken, of soms geen taken als geen actie nodig is.

**Stap 3: Taken uitvoeren** Elke taak wordt uitgevoerd volgens de regels van het domein. Dit kan handmatige verificatie
inhouden, automatische berekeningen, of andere domeinspecifieke activiteiten.

**Stap 4: Gevolgen vastleggen** Het uitvoeren van taken levert gevolgen op - dit zijn de definitieve veranderingen die
het domein accepteert als geldig. Deze gevolgen vormen de waarheid voor dit domein. Ze beschrijven wat er is gebeurd:
een persoon is verhuisd, een huwelijk is voltrokken, een kind is geboren, een bedrijf is ingeschreven, een eigendom is
overgedragen.

**Stap 5: Presentatie opmaken** De gevolgen worden niet rechtstreeks gedeeld, maar gebruikt om projecties op te maken
die aansluiten bij specifieke informatiebehoeften. Een verhuizing kan bijvoorbeeld leiden tot verschillende
presentaties: een uittreksel voor de gemeente, een adreswijziging voor de belastingdienst, of een notificatie voor de
zorgverzekeraar. Elke presentatie[^1] toont alleen de informatie die relevant is voor de ontvangende partij.

Deze cyclus vormt de kern van elk register-ondersteund proces. Het register bewaart de gevolgen en stelt ze beschikbaar
voor raadpleging.

![Gedetailleerd uitvoeringsproces dat het register ondersteunt](/assets/uitvoeringsproces.svg)
_Figuur 2: Gedetailleerd uitvoeringsproces dat het register ondersteunt_

### Het domeinmodel als kern

Het **domeinmodel** definieert wat binnen het domein mogelijk is. Het beschrijft:

- **Taakdefinities**: Welke acties mogelijk zijn binnen het domein
- **Taakverwerkingsregels**: Hoe taken worden uitgevoerd en welke gevolgen ze hebben
- **Presentatiedefinities**: Welke informatie in welke vorm beschikbaar gesteld wordt
- **Presentatieverwerkingsregels**: Hoe gevolgen worden omgezet naar specifieke informatiebehoeften

**Signaalverwerking staat buiten het domeinmodel.** Allerlei signalen kunnen op het proces afkomen. De signaalverwerking
interpreteert deze naar het domeinmodel toe: welke van de beschikbare taken moet worden uitgevoerd?

Het domeinmodel vormt de kern van wat het register ondersteunt - de mogelijke acties en hun gevolgen.

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

Het uitvoeringsproces krijgt concrete vorm in een applicatiearchitectuur. Het register ondersteunt dit proces door de
juiste componenten en datastromen in te richten. Ultiem is een (business) domeinmodel gelijk aan een register, één
_bounded context_ met eigen regels en begrippen, zoals bedoeld in [[Domain-Driven Design]]. Veel vaker is het zo dat er
meerdere bounded contexten te onderscheiden zijn in één business domeinmodel[^2]. Dit heeft te maken met
verantwoordelijkheden en technologie _stacks_ en hebben vaak ook historische redenen; de verzameling van applicaties die
door de tijd heen ontwikkeld zijn. Toch tekenen we hier de eenvoudige en ultieme situatie als uitgangspunt.

![Applicatieve ondersteuning en architectuurelementen waaruit het register bestaat](/assets/registeranatomie.svg)
_Figuur 3: Applicatieve ondersteuning en architectuurelementen waaruit het register bestaat_

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

- **Commands**: De opdrachten aan het register, aangeboden met de intentie daarin een verandering aan te brengen
- **Effecten**: De waarheid van het domein - wat er werkelijk is gebeurd
- **Projecties**: Verschillende views op deze waarheid voor verschillende gebruikers

**Syntheses**[^3] (views die meerdere domeinen combineren) vallen buiten het register en verdienen eigen architectuur.

[^1]: Dit is conceptueel juist, maar zeker geen dagelijkse praktijk. In de informatiebehoeften van verschillende
    afnemers zijn vaak overeenkomstigheden te vinden, zodat groepering voor de hand. Richtlijnen en overwegingen gaan
    nog (elders) beschreven worden.

[^2]: [No, Your Domains and Bounded Contexts Don’t Map 1 on
    1](https://verraes.net/2025/08/domain-and-bounded-contexts-dont-map-one-on-one/) - Mathias Verraes.

[^3]: Naar [Chronolexografie](https://chronolexografie-3e7a8b.gitlab.io/), een conceptueel model en specifieke
    architectuur voor het digitaal vastleggen en bijhouden van de rechtstoestand. De _projecties_ in bovenstaand artikel
    zijn te relateren aan de _reductie_ uit Chronolexografie. Met _synthese_ wordt in beide artikelen geduid op analyse
    en _view_ op meer dan alleen projecties en reducties uit registers. Het betreft vaak uitgebreidere verwerkingen,
    transformaties en combinatie met meerdere projecties uit verschillende registers.
