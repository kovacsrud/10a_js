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
A szövegbeviteli mezők speciális esete, amikor jelszót kérünk be erre külön elem van sajátossága, hogy a beírt karakterek helyett csak  pontok jelennek meg.
A \<Select> elemmel lehet megvalósítani a legördükő menüt.  Az egyes űrlapelemeknél általában a **name** paraméternél megadott névvel tudjuk beazonosítani az adott elemet, a **value** paraméter képviseli az elemben megadott/kiválaszott stb. értéket.

Írassuk ki az űrlapba beírt/kiválasztott értékeket!  A form onsubmit eseményénél szerepel már egy **formadatok()** nevű függvény, készítsük el!
A \<SCRIPT> -be a következő kerüljön:
```js
 function formadatok()
{
   alert("A megadott név:"+document.regisztracio.nev.value);
   alert("A jelszó hossza:"+document.regisztracio.password.value.length);
   alert("A kiválaszott lakhely:"+document.regisztracio.lakhely.value);
}
```
Készen is van.

### Űrlapok ellenőrzése

Az űrlapok elemeinek ellenőrzésére számos lehetőség van. Figyelhetjük, hogy a felhasználó nem hagyta-e üresen valamelyik mezőt. Ebben az esetben a benne lévő érték hossza (length) 0 lesz.

Ellenőrizhetjük, hogy a jelszó elég hosszú-e, ha nem éri el a kívánt hosszúságot, hibaüzenetet adhatunk.
Így módosul a függvény az ellenőrzésekkel:

```js
 function formadatok()
{
 alert("A megadott név:"+document.regisztracio.nev.value);
 if(document.regisztracio.nev.value.length==0)      
 {
        alert("A név mező nem lehet üres!");
 }
        alert("A jelszó hossza:"+document.regisztracio.password.value.length);
            
 if  (document.regisztracio.password.value.length<5)
 {
        alert("Túl rövid jelszó!")
 }
            
        alert("A kiválaszott lakhely:"+document.regisztracio.lakhely.value);
}
```
