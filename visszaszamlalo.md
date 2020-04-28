# Visszaszámláló JavaScript-ben

Páran jelezték, hogy ez a visszaszámláló nehezen akart kialakulni, ezért készítünk egy alap megoldást, és aztán majd mindenkinek meg kell próbálnia kiegészíteni.

A megoldás a következő: bekérjük prompt-al az a másodperc értéket, ahonnan vissza akarunk számolni, majd indul a visszaszámlálás. Ha az érték eléri a nullát, akkor bónuszként még beállítjuk az oldal háttérszínét pirosra, valamint töröljük az időzítést.

A kiinduló HTML oldal:
```HTML
<HTML>

<HEAD>
    <TITLE>
        Dátumok,dátumok mindenütt.
    </TITLE>
    <link rel="stylesheet" href="style.css" type="text/css">
</HEAD>

<BODY>
    <H1>Visszaszámláló</H1>
    <DIV id="fokeret">
        
        <P>
            
            <SPAN id="masodperc"></SPAN>

        </P>

    </DIV>
    
    
    <SCRIPT>
    </SCRIPT>
</BODY>

</HTML>

```

Nézzük, mi kerül a Script-be! 
Először is be kell kérni a másodperc értéket, ahonnan vissza kell számolni, valamint azt egy változóba el kell tárolni, és a weboldalba is bele kell írni.

```js
var startMasodperc=prompt("Honnan számolunk vissza?");
document.getElementById("masodperc").innerHTML=startMasodperc;
```
Ezt követi a **visszaszamlalo()** nevű függvény. Egyszerű a működése, a masodperc id-vel ellátott elemből kiolvassuk az aktuális másodperc értéket, csökkentjük, visszaírjuk. Ha elérte a nullát, akkor megváltoztatjuk a háttérszínt.

```js
function visszaszamlalo() {

     masodperc = document.getElementById("masodperc").innerHTML;
     masodperc = parseInt(masodperc);

     masodperc--;
            
     if (masodperc==0){
         document.body.style.backgroundColor="red";
         clearInterval(szamlalas);
     }
                                   
     document.getElementById("masodperc").innerHTML=masodperc;
}
```
Végül, indítjuk a számlálót:

```js
 var szamlalas=setInterval(visszaszamlalo, 1000);
```
Látható, hogy itt a setInterval(visszaszamlalo,1000)-is kap tulajdonképpen egy azonosítót, amire tudunk hivatkozni a leállításkor.

