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
