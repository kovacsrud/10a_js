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
  


