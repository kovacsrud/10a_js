# Az aktuális időt megjelenítő egyszerű honlapot fogunk készíteni.

Ebben a honlapban már arra is igyekszünk adni, hogy valahogy nézzen is ki, így CSS stílusfájlt is készítünk.
A feladat, hogy egy sorban látszódjon az **év-hónap-nap** információ, alatta pedig az **óra:perc:másodperc**. Az óra nézzen ki rendes órának, tehát az értékek megfelelően változzanak, az oldal újratöltése nélkül.

Az infókat egy keretbe tesszük (\<DIV> tag), ezen belül egy-egy bekezdés lesz (\<P>), és a bekezdéseken belül \<SPAN> tagokkal biztosítjuk a karakterformázást. Minden elemhez id-t rendelünk, hogy a script-ből könnyen el lehessen érni őket.
  
Az első feladat, hogy létre kell hozni egy stíluslapot ***style.css***  néven. A tartalma a következő legyen:

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

h1{
    text-align: center;
    color: brown;
}
```
A következő legyen az ***ora.html*** fájl létrehozása:

```html
<HTML>

<HEAD>
    <TITLE>
        Dátumok,dátumok mindenütt.
    </TITLE>
    <link rel="stylesheet" href="style.css" type="text/css">
</HEAD>

<BODY>
    <H1>Óra JavaScript-ben</H1>
    <DIV id="fokeret">
        <P>
            <SPAN id="ev">2000</SPAN>
            <SPAN id="elvalaszto">-</SPAN>
            <SPAN id="honap">01</SPAN>
            <SPAN id="elvalaszto">-</SPAN>
            <SPAN id="nap">01</SPAN>
        </P>
        
            <P>
                <SPAN id="ora">01</SPAN>
                <SPAN id="elvalaszto">:</SPAN>
                <SPAN id="perc">10</SPAN>
                <SPAN id="elvalaszto">:</SPAN>
                <SPAN id="masodperc">22</SPAN>
            </P>
        
    </DIV>
</BODY
</HTML>  
```
Látszik, hogy a \<HEAD> részben lévő \<LINK> utasítás betölti a stíluslapot. Az oldalban egyenlőre azok az idő értékek jelennek meg, amik kézzel be lettek írva, ennek pusztán csak annyi jelentősége van, hogy látjuk a stíluslap által alkalmazott formázásokat.


