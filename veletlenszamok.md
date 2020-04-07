
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
