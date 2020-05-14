# Hibakezelés a Javascript-ben

A Javascript-ben is kezelhetjük a program futása során felmerülő hibákat, melynek módja rendkívül hasonló más programnyelvek, pl.C# megoldásaihoz.

Készítsünk egy alap HTML dokumentumot

```HTML
<HTML>
    <HEAD>
        <TITLE>Hibakezelés
        </TITLE>
        
    </HEAD>
    <BODY>
        <H1>Hibakezelés, keresés</H1>
        
        <p id=ertek>58</p>
        
        <SCRIPT>
                    
           
            
        </SCRIPT>
    </BODY>
</HTML>
```
Látható, hogy van egy bekezdés(ertek id-vel), amelynek az értéke  jelenleg 58. Szeretnénk ehhez az értékhez hozzáadni mondjuk 10-et. Ez nyilván csak akkor fog sikerülni, ha az innen kiolvasott értékkel tudunk matematikai műveletet végezni. Ha nem tudunk, akkor pedig szeretnénk valami hibaüzenetet adni. 

A \<SCRIPT> tag-be a következő programkód kerül:

```js
 var ertek=document.getElementById("ertek").innerHTML;
   try{
      ertek=parseInt(ertek)+10;
      if(isNaN(ertek)) {
          throw "Nem szám!";
      }
       document.write("Az érték:"+ertek);
               
      } catch(err) {
            document.write(err);
      }        
           
```
Átvesszük az ertek id-vel ellátott elem értékét. Megpróbáljuk számként értelmezni (parseInt) és hozzáadni 10-et. Nyilván, ha az átvett érték nem alakítható számra, akkor az eredmény sem szám lesz. Ebben az esetben a változó értéke Nan (Not a Number) lesz. 
Ezt tudjuk egy elágazással figyelni, és dobunk egy kivételt, egy hibaüzenettel. Ha az érték szám, akkor természetesen nem keletkezik kivétel. 
