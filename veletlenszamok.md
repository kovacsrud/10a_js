
### Véletlen számok generálása JavaScriptben

Hozzuk létre az alábbi weboldalt:
```HTML
<HTML>
    <HEAD>
        <TITLE>Függvények, függvények mindenütt!
        </TITLE>
        
    </HEAD>
    <BODY>
        <H1>Véletlen számok generálása</H1>
        
        
        
        <SCRIPT>               
            
        </SCRIPT>
    </BODY>
</HTML>
```
A véletlen számok generálására a Javascriptben a a **Math.random()** függvény használatos. Ez egy 0 és 1 közötti véletlen számot ad vissza.

A \<SCRIPT> tag még üres, írjuk bele a következőt:

```js
 document.write(Math.random());   
```
Az eredmény nem nagyon emlékeztet a C#-ban tanultakra, mert ilyet kapunk pl:0.3204727667114817

Mi a helyzet, ha 1 fölötti számot szeretnénk? Változtassuk meg a függvényt!

```jsd
 document.write(Math.random()*10);  
```
Így már jobb, de a szám nem egész szám, pedig a legtöbb esetben ilyenre van szükség. Viszont lehet a JS-ben is használni kerekítést, az segíthet.

```js
document.write(Math.floor(Math.random()*10));  
```
Így már sokkal jobb, 0 és 9 közötti egész számot kapunk. Mi a helyzet, ha 1 és 10 közötti számot szeretnénk? Hozzá kell adni egyet!
```js
document.write(Math.floor(Math.random()*10)+1);  
```
0 és 100 között?
```js
document.write(Math.floor(Math.random()*101));  
```
1 és 100 között?
```js
document.write(Math.floor(Math.random()*100)+1);  
```
10 és 100 között?
```js
document.write(Math.floor(Math.random()*90)+10);
```
10 és 50 között?
```js
document.write(Math.floor(Math.random()*40)+10);
```

Általánosságban megfogalmazhatjuk a következő összefüggést, ha min az alsó határ, és max a felső határ, akkor a véletlenszám generálás logikája:

**Math.floor(Math.random(max-min)+min)**

Készítsen egy függvényt, amely megadott határok pl. (10,30) közötti véletlen egész számot ad vissza!
