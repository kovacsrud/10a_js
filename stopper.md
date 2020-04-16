# Stopper készítés

Ez a honlap egy minimalista stoppert fog megvalósítani.
A megjelenített idő az **óra:perc:másodperc** formában fog kinézni. 

Az infókat egy keretbe tesszük (\<DIV> tag), ezen belül egy-egy bekezdés lesz (\<P>), és a bekezdéseken belül \<SPAN> tagokkal biztosítjuk a karakterformázást. Minden elemhez id-t rendelünk, hogy a script-ből könnyen el lehessen érni őket.

Az előző feladatnál létrehozott stílusfájlt használjuk, nem muszáj újra elkészíteni, ha megvan.
Ha nincs meg, akkor létre kell hozni ***style.css***  néven. A tartalmát kiegészítjük néhány új dologgal, a **reszido** és a **gomb** id-k hoz rendelünk egy-egy stílust.

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

#reszido {
    margin: auto;
    width: 500px;
    font-size: 20;
    text-align: center;
    font-family: sans-serif;
    font-weight:bold;
    color: burlywood;
}

#gomb {
	margin:auto;
    text-align: center;
}

h1{
    text-align: center;
    color: brown;
}
```
A következő legyen az ***stopper.html*** fájl létrehozása:

```html
<HTML>

<HEAD>
    <TITLE>
        Stopper
    </TITLE>
    <link rel="stylesheet" href="style.css" type="text/css">
</HEAD>

<BODY>
<H1>Óra JavaScript-ben</H1>
    <DIV id="fokeret">
        
        <P>
            <SPAN id="ora">00</SPAN>
            <SPAN id="elvalaszto">:</SPAN>
            <SPAN id="perc">00</SPAN>
            <SPAN id="elvalaszto">:</SPAN>
            <SPAN id="masodperc">00</SPAN>

        </P>

    </DIV>
    <div id=gomb><input type="button" name="Részidő" value="Részidő" onclick=reszido()>
    <input type="button" name="Törlés" value="Törlés" onclick=reszido_torles()></div>
    <div id=reszido>
        
    </div>    
</BODY
</HTML>  
```
Látszik, hogy a \<HEAD> részben lévő \<LINK> utasítás betölti a stíluslapot. Az oldalban egyenlőre azok az idő értékek jelennek meg, amik kézzel be lettek írva, ennek pusztán csak annyi jelentősége van, hogy látjuk a stíluslap által alkalmazott formázásokat.

A **fokeret** id-vel jelzett \<DIV> tartalmazza az aktuális időt. A gombokat egy **gomb** id-vel ellátott \<DIV> jelzi. A részidők majd a **reszido** id-vel azonosított \<DIV>-be kerülnek.

A \</DIV> után hozzuk létre a \<SCRIPT></SCRIPT> tagot, minden ami ezután következik, ebbe kerüljön!

Három függvényt készítünk. Az első feladata az idő lekérdezése, és frissítése. A második függvény segítségével rögzítjük a részidőt, a harmadik függvény pedig a részidők törlését fogja elvégezni.

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
