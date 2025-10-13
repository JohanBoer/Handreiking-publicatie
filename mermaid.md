# Het VNG-R Respec proces

Onderstaande flowchart beschrijft het proces zoals we dat binnen VNG Realisatie hanteren om tot Respec documentatie te komen. Daarnaast is het echter ook een voorbeeld van het gebruik van de Mermaid syntax voor het vervaardigen van zo'n flowchart. 

<figure>
    
```mermaid
%%{init: {"flowchart": {"defaultRenderer": "elk"}} }%%
graph TD
    A([Start])---->B{"<b>1</b><br/>Eerste versie<br/>van Respec<br/>documentatie?"}
    B{"<b>1</b><br/>Eerste versie<br/>van Respec<br/>documentatie?"}--Nee-->C("...")
    C("...")---->D("<b>3</b><br/>Creëer nieuwe content of pas content aan")
    C("...")---->E("<b>5</b><br/>Pas basisstructuur aan voor versie")
    D("<b>3</b><br/>Creëer nieuwe content of pas content aan")---->I("<b>4</b><br/>Assembleer document")
    I("<b>4</b><br/>Assembleer document")---->J("<b>5</b><br/>Pas document configuratie properties aan")
    B{"<b>1</b><br/>Eerste versie<br/>van Respec<br/>documentatie?"}--Ja-->F("...")
    F("...")---->G("<b>2</b><br/>Creëer en configureer project repo")
    F("...")---->H("<b>6</b><br/>Creëer basisstructuur in publicatie repo")
    G("<b>2</b><br/>Creëer en configureer project repo")---->D("<b>3</b><br/>Creëer nieuwe content of pas content aan")
    H("<b>6</b><br/>Creëer basisstructuur in publicatie repo")---->E("<b>7</b><br/>Pas basisstructuur aan voor versie")
    E("<b>7</b><br/>Pas basisstructuur aan voor versie")---->K("<b>8</b><br/>Plaats gegenereerde documenten in publicatie repo")
    K("<b>8</b><br/>Plaats gegenereerde documenten in publicatie repo")---->L("<b>9</b><br/>Gebruik publicatie link Respec doc in GH Pages")
    J("<b>5</b><br/>Pas document configuratie properties aan")---->K("<b>8</b><br/>Plaats gegenereerde documenten in publicatie repo")
    L("<b>9</b><br/>Gebruik publicatie link Respec doc in GH Pages")---->M([Stop])
```

<figcaption>Het VNG-R Respec proces (Mermaid voorbeeld)</figcaption>
</figure><br/><br/>

Zie de '[GitHub documentatie](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-diagrams#creating-mermaid-diagrams)' voor een uitleg van de Mermaid syntax.

**Aandachtspunten m.b.t. Mermaid**

* In de code van het  bovenstaand voorbeeld is de mermaid code binnen een `figure` element geplaatst'. Let daarbij op dat er voorafgaand aan de eerste en na de laatste ```` ``` ```` code een lege regel wordt geplaatst. Het `figure` element mag dus niet direct aansluiten op de ```` ``` ```` code.
* Vermijd markdown frontmatter secties zoals<br/><code>---</code><br/><code>title: Animal example</code><br/><code>---</code><br/>De ervaring is dat deze een goede verwerking van de Mermaid code verhinderd.
* Er is blijkbaar een verschil tussen het gebruik van pijlen met 6 `-` streepjes met tekst zoals `--- Ja --->` en pijlen met maar 4 streepjes met tekst zoals `-- Ja -->`.
Zodra je de eerste variant gebruikt en een bepaalde pijl komt meerdere keren voor dan wordt deze in de gegenereerde flowchart ook meerdere keren gebruikt. Dat kan resulteren in een woud aan lijnen wat wellicht niet de bedoeling is, zie onderstaand voorbeeld:

<figure>
    
```mermaid
%%{init: {"flowchart": {"defaultRenderer": "elk"}} }%%
graph TD
    A([Start])---->B("`**1.** Is er sprake van hergebruik in de zin van de Who?
    Zie paragraaf 1.1.`")

    B("`**1.** Is er sprake van hergebruik in de zin van de Who?
    Zie paragraaf 1.1.`")--- Nee --->L("`**Wijs het verzoek af**`")

    B("`**1.** Is er sprake van hergebruik in de zin van de Who?
    Zie paragraaf 1.1.`")--- Ja --->C("`**2.** Is het verzoek gericht tot een met een publieke taak belaste instelling?
    Zie paragraaf3.1.`")

    C("`**2.** Is het verzoek gericht tot een met een publieke taak belaste instelling?
    Zie paragraaf3.1.`")--- Nee --->L("`**Wijs het verzoek af**`")

    C("`**2.** Is het verzoek gericht tot een met een publieke taak belaste instelling?
    Zie paragraaf3.1.`")
--- Ja --->D("`**3.** Is het verzoek afkomstig van een andere met een publieke taak belaste instelling? De uitwisseling van informatie tussen met een publieke taak belaste instellingen onderling is geen hergebruik van overheidsinformatie in de zin van de Who.`")

    D("`**3.** Is het verzoek afkomstig van een andere met een publieke taak belaste instelling? De uitwisseling van informatie tussen met een publieke taak belaste instellingen onderling is geen hergebruik van overheidsinformatie in de zin van de Who.`")--- Nee --->L("`**Wijs het verzoek af**`")

    D("`**3.** Is het verzoek afkomstig van een andere met een publieke taak belaste instelling? De uitwisseling van informatie tussen met een publieke taak belaste instellingen onderling is geen hergebruik van overheidsinformatie in de zin van de Who.`")--- Ja --->E("`**4.** Berust de gevraagde informatie bij de met een publieke taak belaste instelling waartoe het verzoek is gericht? Indien mogelijk verwijst u door naar de instelling waar de informatie wel berust.`")

    E("`**4.** Berust de gevraagde informatie bij de met een publieke taak belaste instelling waartoe het verzoek is gericht? Indien mogelijk verwijst u door naar de instelling waar de informatie wel berust.`")--- Nee --->L("`**Wijs het verzoek af**`")

    E("`**4.** Berust de gevraagde informatie bij de met een publieke taak belaste instelling waartoe het verzoek is gericht? Indien mogelijk verwijst u door naar de instelling waar de informatie wel berust.`")--- Ja ---> F("`**5.** Is de informatie vergaard in het kader van een publieke taak? Het gaat om openbare informatie verkregen in het kader van de publieke taak van een met een publieke taak belaste instelling; direct of als bijproduct. Het gaat niet om informatie die voor interne bedrijfsvoering wordt gebruikt.`")

    F("`**5.** Is de informatie vergaard in het kader van een publieke taak? Het gaat om openbare informatie verkregen in het kader van de publieke taak van een met een publieke taak belaste instelling; direct of als bijproduct. Het gaat niet om informatie die voor interne bedrijfsvoering wordt gebruikt.`")--- Nee --->L("`**Wijs het verzoek af**`")

    F("`**5.** Is de informatie vergaard in het kader van een publieke taak? Het gaat om openbare informatie verkregen in het kader van de publieke taak van een met een publieke taak belaste instelling; direct of als bijproduct. Het gaat niet om informatie die voor interne bedrijfsvoering wordt gebruikt.`")--- Ja --->G("`**6.** Valt de verzochte informatie onder het toepassingsbereik van de Who? Uitgezonderde categorieën informatie zijn: a. Informatie die berust bij een publieke omroep, met een publieke omroeptaak belaste instelling of een instelling werkzaam onder de verantwoordelijkheid van een van deze instellingen; b. Informatie die berust bij een onderwijs- of onderzoeksinstelling; c. Informatie die berust bij andere culturele instellingen dan musea, bibliotheken (inclusief universiteitsbibliotheken) en archieven; d. Informatie die slechts logo’s of wapens en insignes of bevat.`")

    G("`**6.** Valt de verzochte informatie onder het toepassingsbereik van de Who? Uitgezonderde categorieën informatie zijn: a. Informatie die berust bij een publieke omroep, met een publieke omroeptaak belaste instelling of een instelling werkzaam onder de verantwoordelijkheid van een van deze instellingen; b. Informatie die berust bij een onderwijs- of onderzoeksinstelling; c. Informatie die berust bij andere culturele instellingen dan musea, bibliotheken (inclusief universiteitsbibliotheken) en archieven; d. Informatie die slechts logo’s of wapens en insignes of bevat.`")-- Nee --->L("`**Wijs het verzoek af**`")
---->X([Stop])

```

<figcaption>Eerste Mermaid voorbeeld met pijlen met 6 streepjes.</figcaption>
</figure><br/><br/>

Om dit te voorkomen kun je 2 dingen doen:
* De tekst in de pijlen uniek maken, bijv. met nummers zoals hieronder:

<figure>
    
```mermaid
%%{init: {"flowchart": {"defaultRenderer": "elk"}} }%%
graph TD
    A([Start])---->B("`**1.** Is er sprake van hergebruik in de zin van de Who?
    Zie paragraaf 1.1.`")

    B("`**1.** Is er sprake van hergebruik in de zin van de Who?
    Zie paragraaf 1.1.`")--- 1.Nee --->L("`**Wijs het verzoek af**`")

    B("`**1.** Is er sprake van hergebruik in de zin van de Who?
    Zie paragraaf 1.1.`")--- 1.Ja --->C("`**2.** Is het verzoek gericht tot een met een publieke taak belaste instelling?
    Zie paragraaf3.1.`")

    C("`**2.** Is het verzoek gericht tot een met een publieke taak belaste instelling?
    Zie paragraaf3.1.`")--- 2.Nee --->L("`**Wijs het verzoek af**`")

    C("`**2.** Is het verzoek gericht tot een met een publieke taak belaste instelling?
    Zie paragraaf3.1.`")
--- 2.Ja --->D("`**3.** Is het verzoek afkomstig van een andere met een publieke taak belaste instelling? De uitwisseling van informatie tussen met een publieke taak belaste instellingen onderling is geen hergebruik van overheidsinformatie in de zin van de Who.`")

    D("`**3.** Is het verzoek afkomstig van een andere met een publieke taak belaste instelling? De uitwisseling van informatie tussen met een publieke taak belaste instellingen onderling is geen hergebruik van overheidsinformatie in de zin van de Who.`")--- 3.Nee --->L("`**Wijs het verzoek af**`")

    D("`**3.** Is het verzoek afkomstig van een andere met een publieke taak belaste instelling? De uitwisseling van informatie tussen met een publieke taak belaste instellingen onderling is geen hergebruik van overheidsinformatie in de zin van de Who.`")--- 3.Ja --->E("`**4.** Berust de gevraagde informatie bij de met een publieke taak belaste instelling waartoe het verzoek is gericht? Indien mogelijk verwijst u door naar de instelling waar de informatie wel berust.`")

    E("`**4.** Berust de gevraagde informatie bij de met een publieke taak belaste instelling waartoe het verzoek is gericht? Indien mogelijk verwijst u door naar de instelling waar de informatie wel berust.`")--- 4.Nee --->L("`**Wijs het verzoek af**`")

    E("`**4.** Berust de gevraagde informatie bij de met een publieke taak belaste instelling waartoe het verzoek is gericht? Indien mogelijk verwijst u door naar de instelling waar de informatie wel berust.`")--- 4.Ja ---> F("`**5.** Is de informatie vergaard in het kader van een publieke taak? Het gaat om openbare informatie verkregen in het kader van de publieke taak van een met een publieke taak belaste instelling; direct of als bijproduct. Het gaat niet om informatie die voor interne bedrijfsvoering wordt gebruikt.`")

    F("`**5.** Is de informatie vergaard in het kader van een publieke taak? Het gaat om openbare informatie verkregen in het kader van de publieke taak van een met een publieke taak belaste instelling; direct of als bijproduct. Het gaat niet om informatie die voor interne bedrijfsvoering wordt gebruikt.`")--- 5.Nee --->L("`**Wijs het verzoek af**`")

    F("`**5.** Is de informatie vergaard in het kader van een publieke taak? Het gaat om openbare informatie verkregen in het kader van de publieke taak van een met een publieke taak belaste instelling; direct of als bijproduct. Het gaat niet om informatie die voor interne bedrijfsvoering wordt gebruikt.`")--- 5.Ja --->G("`**6.** Valt de verzochte informatie onder het toepassingsbereik van de Who? Uitgezonderde categorieën informatie zijn: a. Informatie die berust bij een publieke omroep, met een publieke omroeptaak belaste instelling of een instelling werkzaam onder de verantwoordelijkheid van een van deze instellingen; b. Informatie die berust bij een onderwijs- of onderzoeksinstelling; c. Informatie die berust bij andere culturele instellingen dan musea, bibliotheken (inclusief universiteitsbibliotheken) en archieven; d. Informatie die slechts logo’s of wapens en insignes of bevat.`")

    G("`**6.** Valt de verzochte informatie onder het toepassingsbereik van de Who? Uitgezonderde categorieën informatie zijn: a. Informatie die berust bij een publieke omroep, met een publieke omroeptaak belaste instelling of een instelling werkzaam onder de verantwoordelijkheid van een van deze instellingen; b. Informatie die berust bij een onderwijs- of onderzoeksinstelling; c. Informatie die berust bij andere culturele instellingen dan musea, bibliotheken (inclusief universiteitsbibliotheken) en archieven; d. Informatie die slechts logo’s of wapens en insignes of bevat.`")-- 6.Nee --->L("`**Wijs het verzoek af**`")
---->X([Stop])

```

<figcaption>Tweede Mermaid voorbeeld met pijlen met 6 streepjes.</figcaption>
</figure><br/><br/>

* of pijlen met maar vier streepjes gebruiken zoals hieronder:

<figure>
    
```mermaid
%%{init: {"flowchart": {"defaultRenderer": "elk"}} }%%
graph TD
    A([Start])---->B("`**1.** Is er sprake van hergebruik in de zin van de Who?
    Zie paragraaf 1.1.`")

    B("`**1.** Is er sprake van hergebruik in de zin van de Who?
    Zie paragraaf 1.1.`")-- Nee -->L("`**Wijs het verzoek af**`")

    B("`**1.** Is er sprake van hergebruik in de zin van de Who?
    Zie paragraaf 1.1.`")-- Ja -->C("`**2.** Is het verzoek gericht tot een met een publieke taak belaste instelling?
    Zie paragraaf3.1.`")

    C("`**2.** Is het verzoek gericht tot een met een publieke taak belaste instelling?
    Zie paragraaf3.1.`")-- Nee -->L("`**Wijs het verzoek af**`")

    C("`**2.** Is het verzoek gericht tot een met een publieke taak belaste instelling?
    Zie paragraaf3.1.`")
-- Ja -->D("`**3.** Is het verzoek afkomstig van een andere met een publieke taak belaste instelling? De uitwisseling van informatie tussen met een publieke taak belaste instellingen onderling is geen hergebruik van overheidsinformatie in de zin van de Who.`")

    D("`**3.** Is het verzoek afkomstig van een andere met een publieke taak belaste instelling? De uitwisseling van informatie tussen met een publieke taak belaste instellingen onderling is geen hergebruik van overheidsinformatie in de zin van de Who.`")-- Nee -->L("`**Wijs het verzoek af**`")

    D("`**3.** Is het verzoek afkomstig van een andere met een publieke taak belaste instelling? De uitwisseling van informatie tussen met een publieke taak belaste instellingen onderling is geen hergebruik van overheidsinformatie in de zin van de Who.`")-- Ja -->E("`**4.** Berust de gevraagde informatie bij de met een publieke taak belaste instelling waartoe het verzoek is gericht? Indien mogelijk verwijst u door naar de instelling waar de informatie wel berust.`")

    E("`**4.** Berust de gevraagde informatie bij de met een publieke taak belaste instelling waartoe het verzoek is gericht? Indien mogelijk verwijst u door naar de instelling waar de informatie wel berust.`")-- Nee -->L("`**Wijs het verzoek af**`")

    E("`**4.** Berust de gevraagde informatie bij de met een publieke taak belaste instelling waartoe het verzoek is gericht? Indien mogelijk verwijst u door naar de instelling waar de informatie wel berust.`")-- Ja --> F("`**5.** Is de informatie vergaard in het kader van een publieke taak? Het gaat om openbare informatie verkregen in het kader van de publieke taak van een met een publieke taak belaste instelling; direct of als bijproduct. Het gaat niet om informatie die voor interne bedrijfsvoering wordt gebruikt.`")

    F("`**5.** Is de informatie vergaard in het kader van een publieke taak? Het gaat om openbare informatie verkregen in het kader van de publieke taak van een met een publieke taak belaste instelling; direct of als bijproduct. Het gaat niet om informatie die voor interne bedrijfsvoering wordt gebruikt.`")-- Nee -->L("`**Wijs het verzoek af**`")

    F("`**5.** Is de informatie vergaard in het kader van een publieke taak? Het gaat om openbare informatie verkregen in het kader van de publieke taak van een met een publieke taak belaste instelling; direct of als bijproduct. Het gaat niet om informatie die voor interne bedrijfsvoering wordt gebruikt.`")-- Ja -->G("`**6.** Valt de verzochte informatie onder het toepassingsbereik van de Who? Uitgezonderde categorieën informatie zijn: a. Informatie die berust bij een publieke omroep, met een publieke omroeptaak belaste instelling of een instelling werkzaam onder de verantwoordelijkheid van een van deze instellingen; b. Informatie die berust bij een onderwijs- of onderzoeksinstelling; c. Informatie die berust bij andere culturele instellingen dan musea, bibliotheken (inclusief universiteitsbibliotheken) en archieven; d. Informatie die slechts logo’s of wapens en insignes of bevat.`")

    G("`**6.** Valt de verzochte informatie onder het toepassingsbereik van de Who? Uitgezonderde categorieën informatie zijn: a. Informatie die berust bij een publieke omroep, met een publieke omroeptaak belaste instelling of een instelling werkzaam onder de verantwoordelijkheid van een van deze instellingen; b. Informatie die berust bij een onderwijs- of onderzoeksinstelling; c. Informatie die berust bij andere culturele instellingen dan musea, bibliotheken (inclusief universiteitsbibliotheken) en archieven; d. Informatie die slechts logo’s of wapens en insignes of bevat.`")-- Nee -->L("`**Wijs het verzoek af**`")
---->X([Stop])

```

<figcaption>Eerste Mermaid voorbeeld met pijlen met 4 streepjes.</figcaption>
</figure><br/><br/>

Hieronder nog een aantal Mermaid voorbeelden.

<figure>

```mermaid
%%{init: { "sequence": { "useMaxWidth": true } } }%%
sequenceDiagram
    participant dotcom
    participant iframe
    participant viewscreen
    dotcom->>iframe: loads html w/ iframe url
    iframe->>viewscreen: request template
    viewscreen->>iframe: html & javascript
    iframe->>dotcom: iframe ready
    dotcom->>iframe: set mermaid data on iframe
    iframe->>iframe: render mermaid
```

<figcaption>Sequence diagram</figcaption>
</figure>

<figure>

```mermaid
stateDiagram-v2
    [*] --> Still
    Still --> [*]

    Still --> Moving
    Moving --> Still
    Moving --> Crash
    Crash --> [*]
```

<figcaption>state diagram</figcaption>
</figure>

<figure>

```mermaid
erDiagram
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ LINE-ITEM : contains
    CUSTOMER }|..|{ DELIVERY-ADDRESS : uses
```

<figcaption>ER diagram</figcaption>
</figure>

<figure>

```mermaid
journey
    title My working day
    section Go to work
      Make tea: 5: Me
      Go upstairs: 3: Me
      Do work: 1: Me, Cat
    section Go home
      Go downstairs: 5: Me
      Sit down: 5: Me
```

<figcaption>Journey diagram</figcaption>
</figure>

<figure>

```mermaid
gantt
    title A Gantt Diagram
    dateFormat YYYY-MM-DD
    section Section
        A task          :a1, 2014-01-01, 30d
        Another task    :after a1, 20d
    section Another
        Task in Another :2014-01-12, 12d
        another task    :24d
```

<figcaption>Gantt chart</figcaption>
</figure>

<figure>

```mermaid
pie title Pets adopted by volunteers
    "Dogs" : 386
    "Cats" : 85
    "Rats" : 15
```

<figcaption>Pie charts</figcaption>
</figure>
