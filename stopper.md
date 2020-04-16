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

Az idő meghatározása nagyon hasonló, csak éppen 0 másodpercről nő az idő értéke, ha eléri a 60-at, akkor a másodpercet nullázzuk, a percet 1-el növeljük és így tovább. Ezt végzi el a **stopper()** függvény.

```javascript
 function stopper() {

            ora = document.getElementById("ora").innerHTML;
            perc = document.getElementById("perc").innerHTML;
            masodperc = document.getElementById("masodperc").innerHTML;

            ora = parseInt(ora);
            perc = parseInt(perc);
            masodperc = parseInt(masodperc);

            masodperc++

            if (masodperc > 59) {
                masodperc = 0;
                perc++;
            }

            if (ora < 10) {
                ora = "0" + ora;
            }
            document.getElementById("ora").innerHTML = ora;

            if (perc < 10) {
                perc = "0" + perc;
            }

            document.getElementById("perc").innerHTML = perc;

            if (masodperc < 10) {
                masodperc = "0" + masodperc;
            }

            document.getElementById("masodperc").innerHTML = masodperc;

        }
```

A következő feladat az aktuális időpont lekérdezése és új elembe helyezése. Itt bejönnek a képbe új dolgok.
Tanulták (tanítottam), hogy a HTML egy fa struktúrájú dokumentum. Az egyes elemeknek lehetnek szülő ill. gyerek elemeik is.
A weboldalban már van egy reszido azonosítójú <\DIV> elem, ami pillanatnyilag üres. Ehhez az elemhez bármikor adhatunk hozzá gyerek elemeket. A gyerek elem egy bekezdés lesz, amelyben az az idő szerepel majd, amikor lenyomtuk  **Részidő** feliratú gombot.
Létrehozunk egy függvénnyel új elemeket, majd ezt mint gyerek elemet hozzáadjuk a részidőhöz. Ezt valósítja meg a **reszido()** függvény. 
A **document.createElement()** paranccsal tudunk új elemet létrehozni, és az elemnév.appendChild() paranccsal egy elem gyerek elemeként hozzáadni.


```js
 function reszido() {
        var idodiv=document.getElementById("reszido");
        var reszido=document.createElement("p");
        var reszora=document.createElement("span");
        var reszperc=document.createElement("span");
        var reszms=document.createElement("span");      
	
        reszora.innerHTML=ora+":";
        reszperc.innerHTML=perc+":";
        reszms.innerHTML=masodperc;
        reszido.appendChild(reszora);
        reszido.appendChild(reszperc);
	reszido.appendChild(reszms);
	idodiv.appendChild(reszido);

}
```

### Részidők törlése

Ha törölni kívánjuk a tárolt részidőket, akkor a **reszido** \<DIV> gyerek elemeit kell eltávolítani. Lekérdezzük az elemet, meghatározzuk a benne lévő bekezdéseket \<P> , és azokat a **removeChild()** paranccsal töröljük. Vajon miért visszafelé halad a ciklus az elemeken?

például:

```js
 function reszido_torles()
        {
            var reszido=document.getElementById("reszido");
            var reszidok=reszido.getElementsByTagName("p");
            
            console.log("Elemek száma:"+reszidok.length);
            
            for (i=reszidok.length-1;i>=0;i--){
               
                reszido.removeChild(reszidok[i]);
                
            }
        }

```

Végül, indítsuk a stoppert:


```js
setInterval(stopper, 1000);
```
Kész is van.
