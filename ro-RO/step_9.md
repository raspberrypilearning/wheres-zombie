## Găsește obiectele

Acum trebuie să facem jocul să funcționeze! Pe măsură ce jucătorul se mișcă, vom verifica dacă acesta a găsit un obiect. Pentru a găsi un obiect, trebuie să meargă într-o locație din viața reală care este considerată suficient de aproape de locația virtuală a obiectului.

+ Localizează linia `var harta_zombi;`, iar sub aceasta adaugă o nouă variabilă numită `toleranta`. Această variabilă va determina cât de aproape va trebui să fie jucătorul de locația marcajului pentru obiectul respectiv (în metri) pentru a-l găsi. Poți alege cât de aproape este acest obiect - cu cât numărul de metri este mai mic, cu atât mai aproape de locația exactă jucătorul va trebui să ajungă pentru a găsi obiectul. Am ales o toleranță de 10.

Pentru a putea calcula distanța dintre două puncte de pe o hartă, trebuie să folosim o parte din vrăjitoriile tehnice ale Google din biblioteca lor de geometrie. Găsește codul în partea de jos a paginii care ii îndică hărții cheia ta API:

```html
<script async defer
src="https://maps.googleapis.com/maps/api/js?key=A1b2c3d4e5f6g7h8i9j10k11&callback=initMap">
</script>
```

+ În linia de cod de mai sus, imediat după `initHarta`, dar înainte de încheierea `"`, adaugă `&libraries=geometry`. Ai grijă să nu adăugi spații.

+ Acum localizează funcția `seteaza_pozitia_mea()` și poziționează cursorul imediat sub linia `pozitie_veche = marcaj;`.

+ Creează o buclă care va trece prin tabloul `toate_marcajele`.

[[[generic-javascript-for-loop-array]]]

+ În interiorul buclei, utilizează următorul cod pentru a calcula distanța dintre poziția curentă (`poz`) și marcajul pe care îl examinăm în momentul de față:

```javascript
var distanta = google.maps.geometry.spherical.computeDistanceBetween(poz, toate_marcajele[i].getPosition());
```

Imaginea de mai jos arată un exemplu de calcul. Cât de departe este jucătorul față de marcajul spitalului?

![Ce calculăm](images/what-we-are-calculating.png)

+ Adaugă o instrucțiune `if` imediat sub pentru a verifica dacă distanța dintre jucător și marcajul curent pe care îl examinăm este mai mică decât toleranța. Ar trebui să arate așa:

```javascript
if( distanta < toleranta ){
    alert("L-ai gasit!")
}
```

Momentan, nu suntem siguri ce a găsit jucătorul.

+ Elimină linia care spune „L-ai gasit!”, iar în locul ei obține numele pictogramei de care jucătorul este aproape.

```javascript
var ce_este = toate_marcajele[i].getIcon();
```

+ Elimină partea `.png` din numele pictogramei. De exemplu, dacă numele pictogramei este `hospital.png `, vrem doar să spunem „hospital”.

```javascript
ce_este = ce_este.replace(".png", "");

```

+ Creează o alertă pentru a spune jucătorului ce a găsit. În acest caz, alerta va spune `Ai gasit hospital`:

```javascript
alert("Ai gasit " + ce_este );
```

+ Elimină `toate_marcajele[i]` de pe hartă, astfel încât jocul să nu îi spună jucătorului că a găsit același lucru în continuu.

\--- hints \--- \--- hint \--- Amintește-ți că am scos un marcaj din harta înainte, când am oprit atacul emoji-urilor zâmbărețe. \--- /hint \---

\--- hint \--- Pentru a elimina un marcaj de pe hartă, setează harta marcajului pe `null`, ceea ce înseamnă că nu există o hartă în acest caz. \--- /hint \---

\--- hint \--- Va trebui să folosești metoda `.setMap()` asupra marcajului. \--- /hint \---

\--- /hints \---

+ În final, să adăugăm un scor. Încă o dată, localizează linia `var harta_zombi;` și adăugă o altă linie de cod sub ea pentru a crea o variabilă numită `scor`.

Dacă jucătorul a găsit un zombi, în jocul meu nu primesc puncte. Poate că dacă te simți îndrăzneț, ai putea scădea jucătorului tău punctele! Dacă au găsit un spital sau un magazin de arme, primesc 10 puncte.

+ Iată niște linii în pseudo-cod pentru codul pe care vrem să îl adăugăm. Tradu-l în cod real și adăugă-l în programul tău.

```html
DACĂ ceea ce au găsit nu este zombi
    scor + 10 puncte
    ALERTĂ Scorul tau este + scor
```

Adaugă codul tău aici:

![Adaugă un scor](images/add-score.png)

\--- hints \---

\--- hint \--- Am elaborat deja ce au găsit și le-am stocat în variabila `ce_este`. Folosește acest lucru pentru a crea o condiție care spune că conținutul acestei variabile nu este egal (`!=`) cu un zombi. \--- /hint \----

\--- hint \--- Poți adăuga puncte la o variabilă în felul următor:

```javascript
scor += 10
```

Aceasta înseamnă „`scor`-ului precedent i se adaugă 10". \--- /hint \----

\--- hint \--- Soluție:

```javascript
if( ce_este != "zombie"){
    scor += 10;
    alert("Scorul tau este " + scor);
}
```

\--- /hint \----

\--- /hints \---

+ Acum este timpul să îți testezi jocul! Te rugăm să citești sfaturile de siguranță în pasul următor înainte de a face orice testare.