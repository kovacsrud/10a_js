# Űrlapok készítése, hozzáférés az értékekhez

Az űrlapok azon részei egy HTML oldalnak, melynek a segítségével adatokat küldhetünk egy feldolgozó programnak, amely aztán valamilyen módon feldolgozza azokat (pl. beírja egy adatbázisba).

Az űrlapok különféle űrlapelemekből állhatnak, leggyakrabban az alábbi elemek találhatóak egy űrlapban:
 -szövegbeviteli mező
 -rádiógombok
 -jelölő négyzetek
 -legördülő menü
 
 A rádiógombokat több lehetséges érték közül egyetlen választására használják. A jelölő négyzetekkel igen/nem jellegű adatokat lehet küldeni.
 A legördülő menük olyan értékeket tartalmaznak, melyekből egyet vagy többet (beállítás kérdése) választhat a felhasználó.
 Az adatok küldését egy gomb lenyomása jelenti.
 
Nézzünk egy nagyon egyszerű html oldalt:
```HTML
<HTML>

<HEAD>
    <TITLE>
        Űrlapok mindenütt
    </TITLE> 
    
</HEAD>

<BODY>
    <H1>Űrlap</H1>
    <form name="regisztracio" action="dummy" onsubmit=formadatok()>
    <P><Span>Név:</Span><input type="text" name="nev" value="Név"></P>
    <P><Span>Jelszó:</Span><input type="password" name="password"></P>
    <P><Span>Lakhely:</Span><select name="lakhely">
            <option value="Békéscsaba">Békéscsaba</option>
            <option value="Gyula">Gyula</option>
            <option value="Orosháza">Orosháza</option>
        </select></P>
    <P><input type="submit" Value="Küldés"></P>
</form>   
    
    <SCRIPT>
       
    </SCRIPT>
</BODY>

</HTML>
```
