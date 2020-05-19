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
