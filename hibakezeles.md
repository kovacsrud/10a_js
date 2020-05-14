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
