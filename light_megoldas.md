
# Light feladat
## Elemek tulajdonságainak elérése és módosítása JavaScript-ben

A korábbi alkalommal is láttunk példát HTML elemek elérésére és módosítására. Nem csak az elem tartalma, hanem az elem paraméterei is elérhetőek, módosíthatóak.

Ebben a feladatban 4 db képfájl segítségével kell megvalósítani egy olyan weboldalt, ahol egy kapcsoló segítégével tudunk egy égőt ki és bekapcsolni.

Az egyes állapotok megjelenítésére képfájlokat használunk (kapcsolo_be.png,kapcsolo_ki.png,bulb_on.png,bulb_off.png)

A feladatot egy JavaScript függvény segítségével fogjuk megoldani.

Először a html fájlt kell elkészíteni a neve legyen **light.html**. Egy táblázatba kerül a két kép, egymás alá, középre igazítva.

Tartalma a következő legyen:

```HTML
<HTML>

<head>
    <title>
        Light feladat
    </title>
</head>

<Body>
    <table align=center>
        <tr>
            <td align=center><img id="bulb" src="bulb_off.png"></td>
        </tr>
        <tr>
            <td align=center>
                <img id="kapcsolo" src="kapcsolo_ki.png" >
            </td>
        </tr>

    </table>
       
        
    
</Body>

</HTML>
```

A **</TABLE>** alá kerüljön a <SCRIPT></SCRIPT> elem, ebbe kerül a JS függvény.

```HTML
<SCRIPT>
    function kapcsol(){
    
    
    }

</SCRIPT>    
```

Minden további utasítás a függvényen belülre kell hogy kerüljön!

Először meg kell szereznünk azt az információt, hogy jelenleg melyik kép van betöltve. Az egyes képekhez id van rendelve, az égő képét tartalmazó <IMG> elemnél "bulb", a kapcsolónál pedig "kapcsolo" az id értéke.
    
A **bulb** változóba beolvassuk a "bulb azonosítójú elemet".

```Javascript
var bulb=document.getElementById("bulb");
```
A **kapcsolo** változóba pedig a "kapcsolo" azonosítójú elemet.

```Javascript
var kapcsolo=document.getElementById("kapcsolo");
```
Ezeknél a változókon belül az src tartalmazza a kép elérési útvonalát (pl. bulb.src). Ügyelni kell arra, hogy annak ellenére, hogy a weboldalban realtív megadással van megadva a kép elérési útja, a változóban teljes elérési utat kapunk, meghajtóval, mappanevekkel, viszont nekünk csak a fájlnév kell.

Mi a megoldás? Kezeket fel!

Igen, a "/" karakterek mentén felvágjuk az elérési utat, ennek eredménye egy tömb, és csak az utolsó elemet használjuk majd fel összehasonlításra. Ezeket eltároljuk külön változókba:

```javascript
var bulb_src=bulb.src.split("/");
bulb_src=bulb_src[bulb_src.length-1];

 var kapcsolo_src=kapcsolo.src.split("/");
 kapcsolo_src=kapcsolo_src[kapcsolo_src.length-1];

```

Már csak egy elágazásra van szükség a be ill. a kikapcsolt állapot megkülönböztetésére. Ha a kikapcsolt állapot az aktuális, akkor betöltjük a bekapcsolt állapotot jelentő képeket az égőhöz illetve a kapcsolóhoz, és fordítva (az egyes <IMG> elemek src paraméterét változtatjuk gyakorlatilag).

```javascript
 if(bulb_src=="bulb_off.png"){
            
     bulb.src="bulb_on.png";
     kapcsolo.src="kapcsolo_be.png";
           
} 
else {
            
      bulb.src="bulb_off.png";
      kapcsolo.src="kapcsolo_ki.png";
      
}
```

A függvény kész mást nem kell írni bele, azonban ahhoz hogy működjön a kapcsolót megjelenítő <IMG> elem onclick eseményéhez hozzá is kell rendelni az alábbi módon.
    
```HTML
<img id="kapcsolo" src="kapcsolo_ki.png" onclick="kapcsol()">
```

Készen is van.
