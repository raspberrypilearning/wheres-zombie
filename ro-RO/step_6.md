## Afișează poziția ta curentă

Să afișăm poziția curentă a jucătorului pe hartă.

+ În interiorul funcției `initHarta()`, după ce creezi harta, adaugă niște cod pentru a utiliza geolocalizarea HTML5 pentru a găsi poziția curentă a jucătorului:

```javascript
if (navigator.geolocation) {
    navigator.geolocation.watchPosition (seteaza_pozitia_mea);
}
else {
    alertă („Geolocalizarea nu funcționează în browserul tău”);
}
```

Acest cod verifică dacă locația jucătorului poate fi găsită folosind browserul web. Dacă nu poate fi găsită, va apărea o fereastră pop-up cu un mesaj. Dacă poate fi găsită, setăm codul pentru `watchPosition`. Acest cod va monitoriza constant poziția dispozitivului și va apela funcția `seteaza_pozitia_mea` ori de câte ori poziția dispozitivului se schimbă.

+ Pentru a putea afișa poziția jucătorului pe hartă, trebuie să scriem funcția `seteaza_pozitia_mea`. După paranteza de închidere a funcției `initHarta()`, creează o nouă funcție numită `seteaza_pozitia_mea`.

[[[generic-javascript-create-a-function]]]

+ Această funcție are nevoie de latitudinea și longitudinea curente prin comanda `watchPosition` pe care am setat-o. Adaugă un **argument** numit `position` în parantezele funcției, astfel încât aceste date să fie transmise automat la aceasta.

`function seteaza_pozitia_mea(pozitie){`

+ The latitude can be found within the function as `position.coords.latitude`, and the longitude as `position.coords.longitude`. Following the same process as you did in the previous step, create a LatLng object called `pos` inside the `set_my_position` function. The object should contain the latitude and longitude values.

```JavaScript
var pos = new google.maps.LatLng(###, ###);
```

+ Still inside the function, create a marker which is situated at the LatLng object's position. You can do this the same way you created markers in the previous step. However, you should choose a different icon for this marker. we chose to represent the player as a smiley face, but you can choose any emoji you like. Don't forget to copy and paste the emoji image file you want to use into the same folder as your `index.html` code.

![Player emoji](images/player.png)

+ Save your code and refresh the internet browser. If a message pops up asking whether the browser can use your location data, press **Allow**. You should see your player emoji appear wherever you currently are.

![Where you are on the map](images/location-map.png)

+ You might want to adjust the `zoom` value in your map at this stage if it is a little too far out to see the locations of the icons clearly. Using a larger value will zoom in on the map.