# Form ellenőrzés

Ez a weboldal egy egyszerű, regisztrációkban szokványos formot fog megvalósítani, amelynek a mezőit Javascript-el fogjuk leellenőrizni.

Az oldalhoz .css fájl is tartozik (regisztracio.css), amely beállít egy háttérképet [Innen letölthető](background.jpeg), illetve néhány elem stílusát. A weboldal fog tartalmazni táblázatot is, a táblázat háttérszíne részben átlátszó lesz (opacity:0.8).

```css
body {
    background-image: url(background.jpeg);
    color: aliceblue;
    background-size: 150%;
    background-repeat: no-repeat;
    background-position: center;
    font-family: sans-serif;
}

h1 {
    text-align: center;
    font-weight: bolder;
}

h2 {
    text-align: center;
    font-weight: bolder;
}

p {
   padding:80px;
}

table {
    margin: auto;
    padding: 10px;
    background-color: aliceblue;
    color: cornflowerblue;
    font-weight: bold;
    opacity: 0.8;
}

td {
    padding: 20px;
}
```
### Az alap weboldal a következő lesz:

```html
<html>

<head>
    <title>
        Form ellenőrzés
    </title>
    <meta lang="hu" charset="utf-8">
    <link rel=stylesheet type="text/css" href="regisztracio.css">

</head>

<body>
    <h1>Regisztráció</h1>
    <h2>Köszönjük érdeklődését!</h2>
    <p>Kérjük, hogy regisztráljon, így mindig rendelkezésére álljanak a legfrissebb információk, illetve, hogy személyre szabott ajánlatokat állíthassunk össze az Ön részére!</p>
    
    

    <script>
        
    </script>

</body>

</html>
```
A **Kérjük regisztráljon** szöveg alá jön a form:

```html
 <form name="regform" action="dummy" onSubmit="return ellenoriz()">
        <table>
            <tr>
                <td>Név:</td>
                <td><input type="text" name="nev"></td>
            </tr>
            <tr>
                <td>Életkor:</td>
                <td><input type="text" name="kor"></td>
            </tr>
            <tr>
                <td>Telefonszám:</td>
                <td><input type="text" name="telefon"></td>
            </tr>
            <tr>
                <td>E-mail cím:</td><td><input type="text" name="email"></td>
            </tr>
            <tr>
                <td>E-mail cím ismét:</td><td><input type="text" name="email_ismet"></td>
            </tr>
            <tr><td  colspan="2" align=center><input type="submit" name="go"></td></tr>
        </table>

    </form>
```
Látható, hogy az **action** mezőben nem szerepel semmilyen hivatkozás ami valamilyen feldolgozó programra mutatna. Ez azért van így, mert nem szeretnénk hibás adatokat küldeni, azért a feldolgozó programra való hivatkozást (ami most egy e-mail címre való elküldést fog jelenteni) csak akkor állítjuk be, ha a form minden mezője megfelelő adatokkal van kitöltve. Az **onSubmit** eseményhez van megadva az **ellenoriz()** függvény, **return ellenoriz()** formában. Ennek az eredménye egy logikai érték lesz.
