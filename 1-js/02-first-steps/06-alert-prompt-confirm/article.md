# Interactie: alert, prompt, confirm

Sinds we de browser als onze demo omgeving gaan gebruiken, laten we een paar functies bekijken om met de gebruiker te interacteren: `alert`, `prompt` en `confirm`.
## alert

Deze hebben we al een keer gezien. Het laat een notificatie zien and wacht voor de gebruiker om op "OK" te drukken.

Bijvoorbeeld:

```js run
alert("Hallo");
```

Het kleine venster met het bericht heet een *modaal venster*. Het woord "modaal" betekent dat de bezoeker niet met de rest van de pagina kan interacteren, andere knoppen klikken, etc, totdat ze klaar zijn met het venster. In dit geval -- totdat zij op "OK" drukken.

## prompt

De functie `prompt` accepteert twee argumenten:

```js no-beautify
resultaat = prompt(titel, [standaard]);
```

Het laat een modaal venster zien met een tekst bericht, een invoer veld voor de bezoeker, en de knoppen OK/Annuleer.

`titel`
: De tekst om aan de bezoeker te laten zien.

`standaard`
: Een tweede optionele parameter, de eerste waarde voor het invoer veld.

```smart header="De vierkante haakjes in de syntax `[...]`"
De vierkante haakjes om `standaard` heen in de syntax hierboven betekent dat de parameter optioneel is, niet vereist.
```

De bezoeker kan iets in het invoer veld van de prompt typen and dan op "OK" klikken. Dan krijgen we die tekst in de `resultaat`. Of ze kunnen het ingevoerde annuleren door op Annuleer of de `key:Esc` te klikken, dan krijgen we `null` als `resultaat`.

De oproep naar `prompt`  to `prompt` keert de tekst van het invor veld terug of `null` als de input was geannuleerd.

Bijvoorbeeld:

```js run
let age = prompt('How old are you?', 100);

alert(`You are ${age} years old!`); // You are 100 years old!
```

````warn header="In IE: always supply a `default`"
The second parameter is optional, but if we don't supply it, Internet Explorer will insert the text `"undefined"` into the prompt.

Run this code in Internet Explorer to see:

```js run
let test = prompt("Test");
```

Dus, zodat prompts er goed uitzien in IE, adviseren wij dat je altijd een tweede argument verstrekt.

```js run
let test = prompt("Test", ''); // <-- for IE
```
````

## confirm

The syntax:

```js
result = confirm(question);
```

The function `confirm` shows a modal window with a `question` and two buttons: OK and Cancel.

The result is `true` if OK is pressed and `false` otherwise.

For example:

```js run
let isBoss = confirm("Are you the boss?");

alert( isBoss ); // true if OK is pressed
```

## Summary

We covered 3 browser-specific functions to interact with visitors:

`alert`
: shows a message.

`prompt`
: shows a message asking the user to input text. It returns the text or, if Cancel button or `key:Esc` is clicked, `null`.

`confirm`
: shows a message and waits for the user to press "OK" or "Cancel". It returns `true` for OK and `false` for Cancel/`key:Esc`.

All these methods are modal: they pause script execution and don't allow the visitor to interact with the rest of the page until the window has been dismissed.

There are two limitations shared by all the methods above:

1. The exact location of the modal window is determined by the browser. Usually, it's in the center.
2. The exact look of the window also depends on the browser. We can't modify it.

That is the price for simplicity. There are other ways to show nicer windows and richer interaction with the visitor, but if "bells and whistles" do not matter much, these methods work just fine.
