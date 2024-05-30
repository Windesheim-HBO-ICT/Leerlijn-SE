---
title: 1. Basis syntax
tags:
  - JS/Variablen
  - page
difficulty: 2
---

# Inleiding
In JavaScript worden de keywords `var`, `let`, of `const` gebruikt om variabelen te declareren. Een variabele is iets wat een waarde kan opslaan, zoals een **number**, een **string**, etc.

>Dit eerste hoofdstuk is redelijk lang. Het is echter een essentieel deel van developen met JavaScript. Niet bekend zijn met het gedrag van deze keywords gaat leiden tot onverwachte resultaten.

# Syntax (var)

```javascript
var naam = "John Doe";
var leeftijd = 25;
var isStudent = true;
```

```javascript runner
var naam = "John Doe";
var leeftijd = 25;
var isStudent = true;

console.log(`${naam} is ${leeftijd} jaar oud.`)
```

## Probeer het

```javascript sandbox
var naam = "John Doe";
var leeftijd = 25;
var isStudent = true;

console.log(`${naam} is ${leeftijd} jaar oud.`)
```

## Kenmerken
1. **Functie scoped** Een variabele gedeclareerd met var is function-scoped. Dit betekent dat als een variabele binnen een functie wordt gedeclareerd, deze alleen binnen die functie beschikbaar is.

```javascript
function functieNaam() {
  var lokaal = "T5.32";
  console.log(lokaal); // Dit werkt
}
console.log(lokaal); // Dit geeft een foutmelding
```

2. **Hoisting** Variabelen gedeclareerd met var worden 'gehoist', wat betekent dat de declaratie naar de top van hun scope wordt verplaatst, maar niet de toewijzing.

```javascript
console.log(naam); // undefined
var naam = "Ernst";
console.log(naam); // "Ernst"
```

In dit voorbeeld wordt de declaratie var naam; naar boven verplaatst (gehoist), maar de waarde wordt pas toegewezen wanneer de toewijzing `naam = "Ernst` wordt uitgevoerd. Wat er eigenlijk staat:

```javascript
var naam;
console.log(naam); // undefined
var naam = "John Doe";
console.log(naam); // "Ernst"
```

3. **Globale scope**
Als var buiten een functie wordt gedeclareerd, is het een globale variabele en dus beschikbaar in het hele script.
```javascript
var globaal = "Ik ben een globale variable";

function functieNaam() {
  console.log(globaal); // "Ik ben een globale variable"
}

functieNaam();
console.log(globaal); // "Ik ben een globale variable"
```

## Beperkingen
Hoewel var lang de standaard was voor het declareren van variabelen, heeft het enkele beperkingen die het gebruik van `let` en `const` hebben gestimuleerd:
- Scoping problemen: Omdat `var` function-scoped is en niet block-scoped (zoals binnen een if-statement of for-loop), kan dit leiden tot onvoorziene fouten en moeilijkheden bij het debuggen. Voorbeeld:

```javascript runner
if (true) {
  var blockScoped = "Hey! Ik ben hierbuiten ook beschikbaar";
}
console.log(blockScoped); 
```
- Hoisting verwarring: Hoisting kan soms leiden tot verwarring en bugs, omdat variabelen beschikbaar zijn voordat ze gedeclareerd lijken te zijn.


# Syntax (let)

```javascript
let naam = "John Doe";
let leeftijd = 25;
let isStudent = true;
```

```javascript runner
let naam = "John Doe";
let leeftijd = 25;
let isStudent = true;

console.log(`${naam} is ${leeftijd} jaar oud.`)
```

## Probeer het

```javascript sandbox
let naam = "John Doe";
let leeftijd = 25;
let isStudent = true;

console.log(`${naam} is ${leeftijd} jaar oud.`)
```

## Kenmerken
1. **Block Scope** Een van de belangrijkste voordelen van `let` is dat het block-scoped is. Dit betekent dat een variabele gedeclareerd met `let` alleen toegankelijk is binnen het blok waarin het is gedeclareerd.

```javascript
if (true) {
  let locatie = "Brug T5";
  console.log(locatie); // Dit werkt
}
console.log(locatie); // Dit geeft een foutmelding
```

2. **Geen Hoisting zoals bij `var`** Hoewel let ook gehoist wordt, is het niet op dezelfde manier als var. Variabelen gedeclareerd met let zijn niet toegankelijk voordat de declaratie wordt uitgevoerd, wat leidt tot een ReferenceError als je probeert om de variabele te gebruiken voordat deze gedeclareerd is.

```javascript
console.log(naam); // Uncaught ReferenceError: naam is not defined
let naam = "John Doe";
console.log(naam);
```

3. **Geen herhaalde declaratie binnen dezelfde scope** Met `let` kun je een variabele niet meer dan eens binnen dezelfde scope declareren, wat helpt om fouten te vermijden.

```javascript
let leeftijd = 25;
let leeftijd = 30; // SyntaxError: Identifier 'leeftijd' has already been declared
```

# Syntax (const)

```javascript
const naam = "John Doe";
const leeftijd = 25;
const isStudent = true;
```

```javascript runner
const naam = "John Doe";
const leeftijd = 25;
const isStudent = true;

console.log(`${naam} is ${leeftijd} jaar oud.`)
```

## Probeer het

```javascript sandbox
const naam = "John Doe";
const leeftijd = 25;
const isStudent = true;

console.log(`${naam} is ${leeftijd} jaar oud.`)
```

## Kenmerken
1. **Block Scope**: Net als `let` is een variabele gedeclareerd met `const` block-scoped. Dit betekent dat de variabele alleen toegankelijk is binnen het blok waarin het is gedeclareerd.

```javascript
if (true) {
  const locatie = "Brug T5";
  console.log(locatie); // Dit werkt
}
console.log(locatie); // Dit geeft een foutmelding
```

2. **Constante Binding**: De waarde van een `const` variabele kan niet opnieuw worden toegewezen. Dit betekent dat zodra je een waarde aan een `const` hebt toegewezen, je deze niet meer kunt veranderen.

```javascript
const leeftijd = 25;
leeftijd = 30; // TypeError: Assignment to constant variable.
```

3. **Initieel Verplicht**: Je moet een `const` variabele gelijk een waarde geven op het moment dat je deze declareert. Het achterwege laten van een initiële waarde leidt tot een fout.

```javascript
const naam; // SyntaxError: Missing initializer in const declaration
```

# `const` met objecten en arrays
Hoewel je de referentie van een `const` variabele niet kunt hernoemen of opnieuw kunt toewijzen, kun je wel de inhoud van objecten en arrays die met `const` zijn gedeclareerd, wijzigen.

```javascript runner
// Dit mag
const persoon = {
  naam: "John Doe",
  leeftijd: 25
};

persoon.leeftijd = 26;
console.log(persoon.leeftijd); // 26
```

```javascript runner
// Dit mag niet
const persoon = {
  naam: "John Doe",
  leeftijd: 25
};

persoon = { naam: "Jane Doe", leeftijd: 30 }; // TypeError: Assignment to constant variable.
```

In het eerste voorbeeld wordt het memory adres (naar het object) niet aangepast. Dit is nog steeds hetzelfde object. We passen alleen een property binnen het object aan. In het tweede voorbeeld wordt er geprobeerd een nieuw object aan `persoon` te declareren. Omdat dit een nieuw object is, en daardoor ook een ander memory adresis, mag dit niet. 
