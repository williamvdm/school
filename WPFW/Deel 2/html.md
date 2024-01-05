# HTML, CSS, JavaScript (D-1)
Je kent de syntax van CSS, je kent de impact
van het verschil tussen inline, internal en
external definities van CSS, je kunt correcte
selectors en declaraties formuleren, je kent
de impact van (de volgorde van) die selectors
benoemen en je kunt CSS (her-)schrijven
om een gewenst resultaat te bereiken. Je
kent het verschil tussen ‘block’ en ‘inline’ en
kent het standaard box-model (met border,
margin en padding) en flexbox (en daarbinnen
de sleutelwoorden diplay, flex-direction, flexwrap, flex-flow, flex, align-items en justifycontent met bijbehorende mogelijke values).
Je kunt deze CSS combineren met een
gegeven HTML-pagina en daarmee de
elementen op die pagina ordenen volgens
een grafisch ontwerp (uit bijv. Figma) (waarbij
je gebruik kunt maken van de eenheid px). Je
kunt JavaScript gebruiken om de bestaande
opmaak van een pagina m.b.v. DOMmanipulatie te veranderen

# HTML


# CSS
## Inline CSS
Inline CSS stijlen worden rechtstreeks in het HTML-element opgenomen met behulp van het style attirbuut `style="*styles*"`.
Stijlen die direct binnen het style-attribuut van een HTML-element worden gedefinieerd, hebben de hoogste specificiteit. Ze zijn zeer specifiek voor dat ene element.
```html
<p style="color: red; font-size: 16px;">Dit is een paragraaf met inline CSS</p>
```

## Internal CSS
Internal CSS-stijlen worden gedefinieerd binnen de \<style>-tags in de \<head>-sectie van het HTML-document. Ze beïnvloeden alle elementen op de pagina.
Stijlen binnen de \<style>-tags in de \<head>-sectie van het HTML-document hebben een lagere specificiteit dan inline stijlen. Ze gelden echter voor alle elementen op de pagina.
```html
<head>
  <!-- Internal CSS start hier -->  
  <style>
    h1 { color: blue; }
    p { font-size: 14px; }
  </style>
  <!-- Internal CSS eindigt hier -->
</head>
<body>
  <h1>Dit is een kop met internal CSS</h1> <!-- Hier wordt de style 'h1' uit de internal CSS toegepast -->
  <p>Dit is een paragraaf met internal CSS</p> <!-- Hier wordt de style 'p' uit de internal CSS toegepast -->
</body>
```

## External CSS
Externe CSS-stijlen worden in een apart CSS-bestand geplaatst en vervolgens gekoppeld aan het HTML-document. Dit maakt hergebruik van stijlen en onderhoud eenvoudiger.
Stijlen die zijn gedefinieerd in een extern CSS-bestand hebben de laagste specificiteit. Ze gelden voor alle elementen en kunnen worden overschreven door zowel inline als interne stijlen.
```html
<!-- In het HTML-bestand -->
<link rel="stylesheet" type="text/css" href="style.css">
```
```css
/* In het externe CSS-bestand (style.css) */
h1 { color: green; }
p { font-size: 18px; }
```
## Impact
**Specificiteit**
- Inline: Heeft de hoogste specificiteit en zal de andere stijlen overschrijven.
- Internal: Heeft hogere specificiteit dan externe stijlen, maar wordt overschreven door inline stijlen.
- External: Heeft de laagste specificiteit en wordt overschreven door zowel inline als internal stijlen.

**Herbruikbaarheid**
- Inline: Moeilijker te hergebruiken en onderhouden omdat stijlen direct aan elementen zijn gekoppeld.
- Internal: Biedt enige mate van herbruikbaarheid en gemakkelijker onderhoud in vergelijking met inline stijlen.
- External: Biedt de beste herbruikbaarheid en eenvoudig onderhoud door stijlen centraal te beheren in een apart bestand.

## Selectors en declaraties
CSS-code bestaat uit selectoren en declaraties. Selectoren worden gebruikt om de elementen te selecteren waarop de declaraties van toepassing zijn. Declaraties worden gebruikt om de eigenschappen van de geselecteerde elementen te beschrijven.  
Een selector kan een elementnaam zijn, een klassenaam, een ID of een combinatie van deze. Een declaratie bestaat uit een eigenschap en een waarde. De eigenschap beschrijft wat de waarde bepaalt, de waarde is de daadwerkelijke waarde.
```css
/* Selector: Alle div-elementen */
div {
  /* Declaratie: Stel de lettergrootte in op 16px */
  font-size: 16px;

  /* Declaratie: Stel de kleur in op zwart */
  color: black;

  /* Declaratie: Stel de achtergrondkleur in op wit */
  background-color: white;
}

/* Selector: Alle div-elementen met de klassenaam my-class */
.my-class {
  /* Declaratie: Stel de lettergrootte in op 20px */
  font-size: 20px;

  /* Declaratie: Stel de kleur in op blauw */
  color: blue;
}
```
De volgorde van selectors kan impact hebben op de manier waarop de CSS wordt toegepast. Als bijvoorbeeld een selector voor een element wordt gedefinieerd vóór een selector voor een element dat zich binnen het eerste element bevindt, dan worden de declaraties van de eerste selector ook toegepast op het tweede element.

Bijvoorbeeld:
```css
div {
    background-color: red;
}

.card {
    width: 4rem;
    height: 2rem;
    border: 1px solid black;
}
```
```html
<div>
    <p>Stukje tekst</p>
</div>
<div class="card">
    <h1>Card titel</h1>
    <p>Card paragraaf</p>
    <a href="https://www.youtube.com/watch?v=xvFZjo5PgG0">Gameplay video GTA VI</a>
</div>
```
Beide hebben nu een rode achtergrond terwijl je dat misschien helemaal niet wilt.
## Block en Inline
**Block-elementen**
- Beginnen standaard op een nieuwe lijn
- Voegen witruimte aan de randen van het blok toe
- Neemen de volledige breedte van het ouderelement in beslag
- De hoogte past zich aan aan de inhoud

Bijvoorbeeld: p, h1, div, img

**Inline-elementen**
- Worden opgenomen in de lijn van de tekst en breken ze dus niet op
- Voegen nergens witruimte toe
- De breedte past zich aan aan de inhoud

Bijvoorbeeld a, i, b, span

## Standaard box-model
Het standaard box-model bestaat uit vijf onderdelen:
- Padding: De ruimte tussen de rand van het element en de inhoud.
- Border: De rand van het element.
- Margin: De ruimte tussen het element en andere elementen.
- Content: De werkelijke inhoud van het element.
- Width: De breedte van het element.
- Height: De hoogte van het element.

```css
div {
  padding: 10px;
  border: 1px solid black;
  margin: 10px;
  width: 100px;
  height: 100px;
}
```

## Flexbox
### Display
<img src="https://css-tricks.com/wp-content/uploads/2018/10/01-container.svg" alt="drawing" width="400"/>

Dit definieert een flex-container; inline of block, afhankelijk van de opgegeven waarde. Het maakt een flex-context mogelijk voor al zijn directe childs.```css
```css
.container {
  display: flex; /* of inline-flex */
}
```
### Flex-direction
<img src="https://css-tricks.com/wp-content/uploads/2018/10/flex-direction.svg" alt="drawing" width="400"/>

Dit stelt de horizontale axis vast en definieert daarmee de richting waarin flex-items worden geplaatst in de flex-container. Flexbox is, afgezien van optioneel wrappen, een lay-outconcept in één richting. Denk aan flex-items die zich hoofdzakelijk uitlijnen in horizontale rijen of verticale kolommen.
- row (standaard): van links naar rechts in ltr (left-to-right); van rechts naar links in rtl (right-to-left)
- row-reverse: van rechts naar links in ltr; van links naar rechts in rtl
- column: hetzelfde als row, maar van boven naar beneden
- column-reverse: hetzelfde als row-reverse, maar van onder naar boven

```css
.container {
  flex-direction: row | row-reverse | column | column-reverse;
}
```
### Flex-wrap
<img src="https://css-tricks.com/wp-content/uploads/2018/10/flex-wrap.svg" alt="drawing" width="400"/>

Standaard proberen alle flex-items op één regel te plaatsen. Je kunt dit veranderen en de items laten wrappen zoals nodig met deze eigenschap.
- nowrap (standaard): alle flex-items worden op één regel geplaatst
- wrap: flex-items worden op meerdere regels geplaatst, van boven naar beneden
- wrap-reverse: flex-items worden op meerdere regels geplaatst, van onder naar boven

Demo: [flex-wrap](https://css-tricks.com/almanac/properties/f/flex-wrap/)
```css
.container {
  flex-wrap: nowrap | wrap | wrap-reverse;
}
```

### Flex-flow
Dit is een afkorting voor de eigenschappen flex-direction en flex-wrap, die samen de hoofd- en dwarsas van de flexcontainer definiëren. De standaardwaarde is row nowrap.
```css
.container {
  flex-flow: column wrap; /* standaard row nowrap */
}
```

### Justify-content
<img src="https://css-tricks.com/wp-content/uploads/2018/10/justify-content.svg" alt="drawing" width="400"/>

Dit definieert de uitlijning langs de horizontale axis. Het helpt extra vrije ruimte te verdelen die overblijft wanneer alle flex itemen op een lijn inflexibel zijn, of flexibel zijn maar hun maximale grootte hebben bereikt. Het oefent ook enige controle uit over de uitlijning van items wanneer ze over de lijn heen lopen.

Veiligste om te gebruiken: flex-start, flex-end, and center.
```css
.container {
  justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right ... + safe | unsafe;
}
```

### Align-items
<img src="https://css-tricks.com/wp-content/uploads/2018/10/align-items.svg" alt="drawing" width="400"/>

Dit definieert het standaardgedrag voor hoe flex-items langs de verticale axis op de huidige lijn. Zie het als de justify-content versie voor de verticale axis (loodrecht op de horizontale axis).

```css
.container {
  align-items: stretch | flex-start | flex-end | center | baseline | first baseline | last baseline | start | end | self-start | self-end + ... safe | unsafe;
}
```

### Align-content
<img src="https://css-tricks.com/wp-content/uploads/2018/10/align-content.svg" alt="drawing" width="400"/>

Dit lijnt de lijnen van een flexcontainer uit wanneer er extra ruimte in de verticale axis is, vergelijkbaar met hoe justify-content lijnt individuele items uit binnen de horizontale axis.

```css
.container {
  align-content: flex-start | flex-end | center | space-between | space-around | space-evenly | stretch | start | end | baseline | first baseline | last baseline + ... safe | unsafe;
}
```

### Align-self
<img src="https://css-tricks.com/wp-content/uploads/2018/10/align-self.svg" alt="drawing" width="400"/>

Hierdoor kan de standaarduitlijning (of degene gespecificeerd door align-items) worden overschreven voor individuele flexitems.

```css
.item {
  align-self: auto | flex-start | flex-end | center | baseline | stretch;
}
```

### Flex-grow
<img src="https://css-tricks.com/wp-content/uploads/2018/10/flex-grow.svg" alt="drawing" width="400"/>

Dit definieert de mogelijkheid voor een flex item om te groeien als dat nodig is. Het accepteert een eenheidsloze waarde die als verhouding dient. Het bepaalt hoeveel van de beschikbare ruimte in de flexcontainer het item moet innemen.

Als alle items zijn flex-grow ingesteld op 1, wordt de resterende ruimte in de container gelijkelijk verdeeld over alle childs. Als een van de childs de waarde heeft van 2, zou dat child twee keer zoveel ruimte in beslag nemen als een van de anderen (of het zal het in ieder geval proberen).

```css
.item {
  flex-grow: 4; /* default 0 */
}
```

### Flex-shrink
Dit definieert de mogelijkheid voor een flex item om indien nodig te krimpen.
```css
.item {
  flex-shrink: 3; /* default 1 */
}
```

### Flex-basis
Dit bepaalt de standaardgrootte van een element voordat de overgebleven ruimte wordt verdeeld. Het kan een lengte zijn (bijvoorbeeld 20%, 5rem, etc.) of een trefwoord. Het trefwoord "auto" betekent "kijk naar mijn breedte- of hoogte-eigenschap"
```css
.item {
  flex-basis:  | auto; /* default auto */
}
```

### Flex
Dit is de verkorte notatie voor flex-grow, flex-shrink en flex-basis gecombineerd. De tweede en derde parameters (flex-shrink en flex-basis) zijn optioneel. De standaardinstelling is 0 1 auto, maar als je het instelt met een enkel getal, bijvoorbeeld flex: 5;, verandert de flex-basis naar 0%, dus het komt overeen met het instellen van flex-grow: 5; flex-shrink: 1; flex-basis: 0%;.
```css
.item {
  flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
}
```