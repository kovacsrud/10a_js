# Az aktuális időt megjelenítő egyszerű honlapot fogunk készíteni.

Ebben a honlapban már arra is igyekszünk adni, hogy valahogy nézzen is ki, így CSS stílusfájlt is készítünk.
A feladat, hogy egy sorban látszódjon az **év-hónap-nap** információ, alatta pedig az **óra:perc:másodperc**. Az óra nézzen ki rendes órának, tehát az értékek megfelelően változzanak, az oldal újratöltése nélkül.

Az infókat egy keretbe tesszük (\<DIV> tag), ezen belül egy-egy bekezdés lesz (\<P>), és a bekezdéseken belül \<SPAN> tagokkal biztosítjuk a karakterformázást. Minden elemhez id-t rendelünk, hogy a script-ből könnyen el lehessen érni őket.
  
Az első feladat, hogy létre kell hozni egy stíluslapot ***style.css***  néven. A tartalma a következő legyen:

```css
#fokeret {
    margin: auto;
    width: 500px;
    font-size: 50;
    text-align: center;
    font-family: sans-serif;
    font-weight:bold;
    color: burlywood;
}

h1{
    text-align: center;
    color: brown;
}
```
A következő legyen az ***ora.html*** fájl létrehozása:

```html
<HTML>

<HEAD>
    <TITLE>
        Dátumok,dátumok mindenütt.
    </TITLE>
    <link rel="stylesheet" href="style.css" type="text/css">
</HEAD>

<BODY>
    <H1>Óra JavaScript-ben</H1>
    <DIV id="fokeret">
        <P>
            <SPAN id="ev">2000</SPAN>
            <SPAN id="elvalaszto">-</SPAN>
            <SPAN id="honap">01</SPAN>
            <SPAN id="elvalaszto">-</SPAN>
            <SPAN id="nap">01</SPAN>
        </P>
        
            <P>
                <SPAN id="ora">01</SPAN>
                <SPAN id="elvalaszto">:</SPAN>
                <SPAN id="perc">10</SPAN>
                <SPAN id="elvalaszto">:</SPAN>
                <SPAN id="masodperc">22</SPAN>
            </P>
        
    </DIV>
</BODY
</HTML>  
```
Látszik, hogy a \<HEAD> részben lévő \<LINK> utasítás betölti a stíluslapot. Az oldalban egyenlőre azok az idő értékek jelennek meg, amik kézzel be lettek írva, ennek pusztán csak annyi jelentősége van, hogy látjuk a stíluslap által alkalmazott formázásokat.

A \</DIV> után hozzuk létre a \<SCRIPT></SCRIPT> tagot, minden ami ezután következik, ebbe kerüljön!

Először le kell kérdezni a dátumot:

```javascript
 var datum = new Date();
```
A dátumból kiolvassuk az évet:

```js
 var ev = datum.getFullYear();
```
Ezt követi a hónap, azonban a hónap esetében(is) szembesülünk azzal, hogy 10-nél kisebb értékek esetén, nincs 0 az érték előtt, tehát pl. 03 helyett csak 3-at kapunk, ha március van. Ez így nem szép, gondoskodjuk a bevezető 0-ról is! Ne feledük, hogy a hónaphoz 1-et hozzá kell adni.

```js
var honap = datum.getMonth() + 1;

  if (parseInt(honap) < 10) {
    honap = "0" + honap;
  }
```
A nap egyszerű:

```js
var nap = datum.getDate();
``` 
Az óra hasonló, itt is gondoskodni kell bevezető 0-ról, ha az érték 10 alatt van:

```js
var ora = datum.getHours();
        
  if(parseInt(ora)<10) {
    ora = "0" + ora;
  }
```
Percek:
```js
var perc = datum.getMinutes();
        
  if(parseInt(perc)<10){
      perc = "0" + perc;
  }
```

Másodpercek:
```js
var masodperc = datum.getSeconds();
  if(parseInt(masodperc)<10){
    masodperc = "0" + masodperc;
  }
```           
A változók megvannak, nézzük hogy hogyan tudjuk a weboldalba beleírni a változó értékét. A weboldalban minden elemnek adtunk **id**-t, hogy könnyen elérhetőek legyenek, ezt használjuk fel. A **getElementById** segítségével tudunk **id** alapján elérni és módosítani egy elemet. Maga az érték az **innerHTML**-ben található, ez lekérdezhető, vagy éppen átírható. A következő utasítással a weboldalban szereplő **ev** értékét az előbb létrehozott változó értékére módosítjuk:

```js
document.getElementById("ev").innerHTML=ev;
```

A többit is az előzőhöz hasonlóan:

```js
document.getElementById("honap").innerHTML=honap;
document.getElementById("nap").innerHTML=nap;
document.getElementById("ora").innerHTML=ora;
document.getElementById("perc").innerHTML=perc;
document.getElementById("masodperc").innerHTML=masodperc;
```
Így már az oldal letöltésekor aktuális időt láthatjuk. Minden egyes újratöltéskor látni fogjuk, hogy frissül az idő értéke. 
Ez már majdnem jó, de ugye nem akarjuk kézzel frissíteni az oldalt. Vajon hogyan lehet elérni azt, hogy ez bizonyos időközönként automatikusan megtörténjen? 
A megoldás a JavaScript **setInterval** időzítő funkciója. Ez egy függvényt automatikusan meg tud hívni, a megadott időközönként, pl. másodpercenként.

például:
```js
setInterval(ido,1000);
```
Ebben az esetben az **ido** nevű függvény hajtódna végre, minden másodpercben (a setInterval-nél milisec-ben kell megadni a kívánt értéket)

Viszont jelenleg nincsen **ido** nevű függvény. Létre kell hoznunk, és minden műveletet ebbe bele kell tennünk.

```js
function ido() {
  //ide jöjjön az összes művelet
}
```

A kész **ido()** függvény így kell hogy kinézzen:

```js
function ido() {

  var datum = new Date();
  var ev = datum.getFullYear();
  var honap = datum.getMonth() + 1;

    if (parseInt(honap) < 10) {
      honap = "0" + honap;
    }
    
  var nap = datum.getDate();
  var ora = datum.getHours();
        
    if(parseInt(ora)<10){
      ora = "0" + ora;
    }
        
  var perc = datum.getMinutes();
        
    if(parseInt(perc)<10){
       perc = "0" + perc;
    }
        
  var masodperc = datum.getSeconds();
    if(parseInt(masodperc)<10){
       masodperc = "0" + masodperc;
    }
        
  document.getElementById("ev").innerHTML=ev;
  document.getElementById("honap").innerHTML=honap;
  document.getElementById("nap").innerHTML=nap;
  document.getElementById("ora").innerHTML=ora;
  document.getElementById("perc").innerHTML=perc;
  document.getElementById("masodperc").innerHTML=masodperc;

}
```
Már csak annyi kell, hogy beállítsuk, hogy az ido() függvény minden egyes másodpercben fusson le:

```js
setInterval(ido,1000);
```
Kész is van.
