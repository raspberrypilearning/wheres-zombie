## Creează marcajele

+ Sub linia `var zombie_map;`, adaugă o altă linie pentru a crea o variabilă numită `all_markers`. Seteaz-o egală cu `[]`, care reprezintă un tablou gol. Acest lucru va stoca, în final, o referință la fiecare dintre marcajele pe care suntem pe cale sa le creăm.

+ Poziționează cursorul în interiorul funcției `initMap()`, chiar sub codul pentru crearea hărții zombi.

![Adaugă codul marcajului aici](images/add-marker-code.png)

+ Creează o buclă for care va rula o dată pentru fiecare marcaj din tabloul `marcaje` pe care l-am creat în pasul anterior.

[[[generic-javascript-for-loop-array]]]

În interiorul buclei for, linia de date a marcajului la care ne uităm în momentul de față este `markers[i]` - bucla va adăuga `1` la variabila `i` de fiecare dată când rulează, așa că ne vom uita la fiecare linie de date, una câte una.

Prima linie de date arată astfel:

```html
51.90769026213801 -2.068905830383301 zombie.png
```

Vrem să obținem aceste date într-un tablou, așa că va trebui să le împărțim la fel ca în pasul anterior.

+ Adaugă toate celelalte linii de cod în acest pas în bucla for. Mai întâi, cu ajutorul funcției `trim()` elimină orice spații nedorite de la începutul și sfârșitul datelor, făcând în felul următor:

```JavaScript
var marker_data = markers[i].trim();
```

+ Acum, împarte șirul la fel ca și înainte, dar de data aceasta împarte oriunde există un spațiu:

```JavaScript
marker_data = marker_data.split(" ");
```

Dacă faci așa, vei obține un tablou numit `marker_data`, care conține trei valori. În ordine, acestea sunt: latitudinea, longitudinea și fișierul de imagine al marcajului.

+ Creează variabile pentru a denumi fiecare dintre aceste valori. Am numit prima variabila pentru tine:

```JavaScript
var latitude = marker_data[0];
var longitude = ?;
var emoji = ?;
```

+ Pentru a putea adăuga marcajul la poziția corectă, trebuie să creezi un obiect `LatLng`.

```JavaScript
var marker_position = new google.maps.LatLng(###, ###);
```

Adaugă această linie de cod imediat sub linia anterioară, înlocuind `###` cu variabilele de latitudine și longitudine.

+ Tot în interiorul buclei, scrie un cod pentru a crea un marcaj la poziția `marker_position`, cu pictograma `icon:` setată cu variabila emoji.

[[[generic-api-google-maps-marker]]]

\--- hints \--- \--- hint \---

Instead of putting in a fixed latitude/longitude like in the example, use the `marker_position` variable to tell the marker where it should be placed.

\--- /hint \---

\--- hint \---

Check that the name of the map (in the example `mymap`) is the same as the name of the map you have created.

\--- /hint \---

\--- hint \---

You can add an icon by adding another line within the marker to specify `icon: "nameofpicture.png"`. Don't forget to put a comma at the end of the `map` line to indicate that there is another marker property you would like to set.

\--- /hint \---

\--- hint \---

If you specify a fixed file name like `nameofpicture.png`, then the marker icon will always be the same. We created a variable earlier which contains the picture name: put the variable `emoji` as the specified icon to use the right emoji from the data.

```JavaScript
var marker = new google.maps.Marker({
  position: marker_position,
  map: zombie_map,
  icon: emoji
});
```

\--- /hint \---

\--- /hints \---

+ Imediat după sfârșitul codului `marker`, dar tot în interiorul buclei, adaugă următoarea linie pentru a salva o referință la acest marcaj în lista noastră de marcaje `all_markers`. Vom avea nevoie de această listă, mai târziu, într-un pas ulterior.

```JavaScript
all_markers.push(marker);
```

+ Salvează-ți codul și reîncarcă pagina. Testează dacă toate marcajele tale apar pe hartă. Dacă acestea nu sunt afișate corect, poate ar trebui să te uiți în **consola** JavaScript pentru a vedea dacă există mesaje de eroare pe care trebuie să le rezolvi?

[[[generic-javascript-opening-console]]]