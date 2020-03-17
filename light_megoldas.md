
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
    
    
