
# Dátumok a JavaScript-ben

Egy weboldal esetében gyakran van szükség dátumok megjelenítésére, időmérésre stb. A mai példa a dátumkezeléssel foglalkozik.

A kiinduló weboldal:

```HTML
<HTML>
    <HEAD>
    <TITLE>
           Dátumok,dátumok mindenütt!
    </TITLE>
        
    </HEAD>
    <BODY>
        <H1>Dátumok JavaScript-ben</H1>
        <SCRIPT>
        
        </SCRIPT>
    </BODY>
</HTML>
```
A **Script** tag be írjuk be a következő utasításokat:

```javascript
var datum=new Date();
document.write(datum);

```
Az eredmmény egy hasonló szöveg lesz:
**Wed Mar 25 2020 10:39:26 GMT+0100 (közép-európai téli idő)**

Ebben benne van a lényeg, de nem tűnik túl használhatónak, hiszen mi van, ha csak az év kell, stb.

Számos függvény van, amellyel idővel kapcsolatos információkat lehet lekérdezni. 
A legfontosabbak:
 - getFullYear() ->évek lekérdezése
 - getMonth() -> a hónap számmal, 0-11 közötti érték, tehát a valós hónaphoz a kapott értékhet 1-et hozzá kell adni!
 - getDate() -> a nap száma, 1-31 közötti érték
 - getHours() -> az aktuális óra, 0-23 közötti érték
 - getMinutes() -> percek, 0-59 közötti érték
 - getSeconds() -> másodpercek, 0-59 közötti érték
 - getMilliseconds() -> miliszekundumok, 0-999 közötti érték
 
 
 Állítsunk össze egy emészthetőbb dátumot!
 **Év:**
 
 ```js
 var ev=datum.getFullYear();
 ```
**Hónap**, itt egyet hozzá kell adnunk a kapott értékhez.

```js
var honap=datum.getMonth()+1;
```
**Nap**

```js
var nap=datum.getDate();
```
**Óra**
```js
var ora=datum.getHours();
```

**Perc**
```js
var perc=datum.getMinutes();
```

**Másodperc**
```js
var masodperc=datum.getSeconds();
```

