## Găsește obiectele

Acum trebuie să facem jocul să funcționeze! Pe măsură ce jucătorul se mișcă, vom verifica dacă acesta a găsit un obiect. Pentru a găsi un obiect, trebuie să meargă într-o locație din viața reală care este considerată suficient de aproape de locația virtuală a obiectului.

+ Localizează linia `var harta_zombi;`, iar sub aceasta adaugă o nouă variabilă numită `tolerance`. Această variabilă va determina cât de aproape va trebui să fie jucătorul de locația marcajului pentru obiectul respectiv (în metri) pentru a-l găsi. Poți alege cât de aproape este acest obiect - cu cât numărul de metri este mai mic, cu atât mai aproape de locația exactă jucătorul va trebui să ajungă pentru a găsi obiectul. Am ales o toleranță de 10.

Pentru a putea calcula distanța dintre două puncte de pe o hartă, trebuie să folosim o parte din vrăjitoriile tehnice ale Google din biblioteca lor de geometrie. Găsește codul în partea de jos a paginii care ii îndică hărții cheia ta API:

```html
<script async defer
src="https://maps.googleapis.com/maps/api/js?key=A1b2c3d4e5f6g7h8i9j10k11&callback=initMap">
</script>
```

+ În linia de cod de mai sus, imediat după `initHarta`, dar înainte de încheierea `"`, adaugă `&libraries=geometry`. Ai grijă să nu adăugi spații.

+ Acum localizează funcția `set_my_position()` și poziționează cursorul imediat sub linia `old_position = marker;`.

+ Creează o buclă care va trece prin tabloul `toate_marcajele`.

[[[generic-javascript-for-loop-array]]]

+ În interiorul buclei, utilizează următorul cod pentru a calcula distanța dintre poziția curentă (`pos`) și marcajul pe care îl examinăm în momentul de față:

```javascript
var distance = google.maps.geometry.spherical.computeDistanceBetween(pos, all_markers[i].getPosition());
```

Imaginea de mai jos arată un exemplu de calcul. Cât de departe este jucătorul față de marcajul spitalului?

![Ce calculăm](images/what-we-are-calculating.png)

+ Adaugă o instrucțiune `if` imediat sub pentru a verifica dacă distanța dintre jucător și marcajul curent pe care îl examinăm este mai mică decât toleranța. Ar trebui să arate așa:

```javascript
if( distance < tolerance ){
    alert("L-ai gasit!")
}
```

Momentan, nu suntem siguri ce a găsit jucătorul.

+ Elimină linia care spune „L-ai gasit!”, iar în locul ei obține numele pictogramei de care jucătorul este aproape.

```javascript
var what_is_it = all_markers[i].getIcon();
```

+ Elimină partea `.png` din numele pictogramei. De exemplu, dacă numele pictogramei este `hospital.png `, vrem doar să spunem „hospital”.

```javascript
what_is_it = what_is_it.replace(".png", "");

```

+ Creează o alertă pentru a spune jucătorului ce a găsit. În acest caz, alerta va spune `Found the hospital`:

```javascript
alert("Found the " + what_is_it );
```

+ Elimină `all_markers[i]` de pe hartă, astfel încât jocul să nu îi spună jucătorului că a găsit același lucru în continuu.

\--- hints \--- \--- hint \---

Remember that we removed a marker from the map before, when we stopped the attack of the smileys.

\--- /hint \---

\--- hint \---

To remove a marker from the map, set the map of the marker to `null`, which means no map in this case.

\--- /hint \---

\--- hint \---

You will need to use the `.setMap()` method on the marker.

\--- /hint \---

\--- /hints \---

+ În final, să adăugăm un scor. Încă o dată, localizează linia `var zombie_map;` și adăugă o altă linie de cod sub ea pentru a crea o variabilă numită `score`.

If the player found a zombie, in my game they don't get any points. Perhaps if you are feeling particularly mean you could give your player minus points in your game! If they found a hospital or a weapon store they get 10 points.

+ Iată niște linii în pseudo-cod pentru codul pe care vrem să îl adăugăm. Tradu-l în cod real și adăugă-l în programul tău.

```html
DACĂ ceea ce au găsit nu este zombi
    scor + 10 puncte
    ALERTĂ Scorul tau este + scor
```

Add your code here:

![Add a score](images/add-score.png)

\--- hints \---

\--- hint \---

We already worked out what they found and stored it in the variable `what_is_it`. Use this to create a condition which says that the contents of this variable is not equal to (`!=`) zombie.

\--- /hint \----

\--- hint \---

You can add on points to a variable like this:

```javascript
score += 10
```

This means "`score` is whatever it was before plus 10".

\--- /hint \----

\--- hint \---

Solution:

```javascript
if( what_is_it != "zombie"){
    score += 10;
    alert("Scorul tau este " + score);
}
```

\--- /hint \----

\--- /hints \---

+ Acum este timpul să îți testezi jocul! Te rugăm să citești sfaturile de siguranță în pasul următor înainte de a face orice testare.