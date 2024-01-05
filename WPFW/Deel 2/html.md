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

## HTML


## CSS
### Inline CSS
Inline CSS stijlen worden rechtstreeks in het HTML-element opgenomen met behulp van het style attirbuut `style="*styles*"`.
Stijlen die direct binnen het style-attribuut van een HTML-element worden gedefinieerd, hebben de hoogste specificiteit. Ze zijn zeer specifiek voor dat ene element.
```html
<p style="color: red; font-size: 16px;">Dit is een paragraaf met inline CSS</p>
```

### Internal CSS
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

### External CSS
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
### Impact
**Specificiteit**
- Inline: Heeft de hoogste specificiteit en zal de andere stijlen overschrijven.
- Internal: Heeft hogere specificiteit dan externe stijlen, maar wordt overschreven door inline stijlen.
- External: Heeft de laagste specificiteit en wordt overschreven door zowel inline als internal stijlen.

**Herbruikbaarheid**
- Inline: Moeilijker te hergebruiken en onderhouden omdat stijlen direct aan elementen zijn gekoppeld.
- Internal: Biedt enige mate van herbruikbaarheid en gemakkelijker onderhoud in vergelijking met inline stijlen.
- External: Biedt de beste herbruikbaarheid en eenvoudig onderhoud door stijlen centraal te beheren in een apart bestand.

### Selectors en declaraties
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
    background-color: blue;
}
```
```html
<div class="card">
    <h1>Card titel</h1>
    <p>Card paragraaf</p>
    <a href="https://www.youtube.com/watch?v=xvFZjo5PgG0">Gameplay video GTA VI</a>
</div>
```
De .card-selector is meer specifiek dan de div-selector, maar komt later in de CSS code. Dit betekent dat de declaratie voor de div-selector wordt toegepast op alle div-elementen, inclusief de "card". Daarom is de achtergrondkleur van de "card" rood.
