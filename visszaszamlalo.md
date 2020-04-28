# Visszaszámláló JavaScript-ben

Páran jelezték, hogy ez a visszaszámláló nehezen akart kialakulni, ezért készítünk egy alap megoldást, és aztán majd mindenkinek meg kell próbálnia kiegészíteni.

A megoldás a következő: bekérjük prompt-al az a másodperc értéket, ahonnan vissza akarunk számolni, majd indul a visszaszámlálás. Ha az érték eléri a nullát, akkor bónuszként még beállítjuk az oldal háttérszínét pirosra.

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
