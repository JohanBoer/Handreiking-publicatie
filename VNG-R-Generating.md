# Respec m.b.v. Imvertor

## Documentatie generatie

Het is mogelijk om met Imvertor Respec documentatie te genereren van een model. Voorwaarde is wel dat het model MIM compliant is. Bij het genereren spelen de volgende Imvertor configuratieproperties (<b>LET OP!</b> Dus niet een van de Respec property bestanden) een rol:

| Configuratieproperty | Mogelijke waarden | Uitleg |
| --- | --- | -- |
| createoffice | html, doc, none | Hiermee geef je aan of je een documentatie bestand wil genereren en zo ja in welk formaat (html of MsWord). De defaultwaarde is 'none', behalve in het geval van een SIM, daar is de default 'html'. De 'doc' optie is nog niet geïmplementeerd. |
| createofficeanchor | name, id | Geeft aan op welke basis hyperlink anchors moeten worden gegenereerd (op basis van id's of op basis van namen). De default is 'name'. Vooralsnog maakt het  niet uit welke variant je voor deze property kiest, beide varianten leiden tot hetzelfde resultaat. |
| createofficemode | plain, click | Definieert of er in het te genereren bestand hyperlinks moeten worden gegenereert. Bij de waarde 'click' is dat het geval. De defaultwaarde is 'plain'. |
| createofficevariant | respec, msword | Definieert het type te genereren document. Een Respec html document of een MsWord html variant. |

Voor het genereren van Respec documentatie is het essentieel om in je lokale Imvertor property bestand de property 'createofficevariant' de waarde 'respec' te geven. Normaliter zal je dan ook de property 'createofficemode' de waarde 'click' geven.
Dit resulteert er in dat in de folder 'app/cat' 2 Respec bestanden geplaatst, 1 in html en de ander in xhtml.

## Diagrammen als clickable images

Indien op de juiste wijze geconfigureerd en aangeroepen (zie [hier](https://imvertor.armatiek.nl/imvertor-executor/dashboard/wiki?key=info-IMAGEMAPS)) zet Imvertor alle in Enterprise Architect gedefinieerde diagrammen om naar PNG images. 
Deze images worden echter niet als `img` elementen opgenomen in de gegenereerde (x)html. Indien dat gewenst is dan zul je ze zelf moeten opnemen. (**TODO** Onderzoeken of dit wel klopt)
Het is echter wel mogelijk om deze diagrammen automatisch als clickable images in de gegenereerde (x)html op te nemen. Om dat te kunnen doen moet wel aan een aantal voorwaarden worden voldaan.

1. Alleen diagrammen die direct geplaatst zijn in de root folder (Stereotype = 'Basismodel') of in de folder waarin (de folder met) de componenten staan worden daarbij meegenomen of binnen de entiteittypes zelf. Ze mogen dus ook niet in een subfolder van deze folders worden geplaatst. De plaatsing in het model bepaald tevens de plaatsing van het diagram in het (x)html bestand.  (**TODO** Onderzoeken wat de exacte regels zijn);
2. De diagrammen moeten class diagrams zijn;
3. De naam van de diagrammen moet als suffix '`- overzicht`' of '`- detail`' hebben;

Tenslotte is de onderstaande Imvertor configuratieproperty nog van belang.

| Configuratieproperty | Mogelijke waarden | Uitleg |
| --- | --- | -- |
| createimagemap | yes, no | Definieert of van de Diagrammen een imagemap moet worden gegenereerd en of de gegenereerde PNG images als `img` element in de (x)html images worden opgenomen. De default is 'yes'.|

Als deze de waarde 'yes' heeft of niet geconfigureerd is worden er in de (x)html bestanden `img` elementen met referenties naar de juiste images en imagemap elementen opgenomen.

**LET OP!** Maak de in Respec op te nemen diagrammen zoveel als mogelijk in portrait mode op. Dat voorkomt dat je nodeloos diep op het Respec document moet inzoomen.

### Clickable images en pdf

In het evt. te genereren pdf bestand worden de clickable images natuurlijk niet clickable opgenomen. Het kan echter wel zijn dat de images van de pagina's aflopen. Dit is eenvoudig te voorkomen door in het html bestand waarin de images staan bij de `img` elementen het volgende attribute op te nemen:

`style="width: 50em;"`

Nadeel daarvan is echter dat de imagemaps in het html bestand niet meer overeenkomen met de geplaatste images. De volgende workaround zorgt er voor dat je in de publicatie omgeving beschikt over zowel correcte clickable images als een pdf waarin de images niet van de pagina's aflopen. Helaas zal in de werkomgeving de pdf mogelijk wel images bevatten die van de pagina's aflopen.

**Workaround:**
1. Creëer een kopie van het door Imvertor gegenereerde html bestand;
2. Plaats in die kopie bij de `img` elementen het attribute `style="width: 50em;"` en bewaar het bestand;
3. Refereer in het `index.html` bestand naar de zojuist vervaardigde html kopie i.p.v. naar het origineel daarvan en bewaar het bestand;
4. Check zonodig beide bestanden in;
5. Na de build en deployment moeten er in het gegenereerde pdf bestand geen images meer van de pagina's aflopen. Hernoem dat pdf bestand naar `[originele naam]-2.pdf`;
6. Refereer in het `index.html` bestand weer naar het origenele door Imvertor gegenereerde html bestand en bewaar het bestand weer;
7. Check zonodig beide bestanden in;
6. Bij de publicatie in de publicatie omgeving (zie [verderop in deze handleiding](./#publ)) maak je gebruik van het laatst gegenereerde `snapshot.html` bestand en het `[originele naam]-2.pdf` bestand.
