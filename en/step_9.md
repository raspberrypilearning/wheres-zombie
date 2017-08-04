## Find the items

Now we need to make the game work! As the player moves around, we will check whether the player has found an item. To find an item they have to go in real life to a location that is considered close enough to it to pick it up.

+ Locate the line `var zombie_map;` and underneath it add a new variable called `tolerance`. This is how close the player will have to be to the location in metres to be considered to have found it. You can choose how close this is - the smaller the number of metres you choose, the closer the player will have to get to the exact location to find the item. We chose a tolerance of 10.

+ To be able to calculate the distance between two points on a map, we need to use some of Google's technical wizardry from their geometry library. Locate the code near the bottom of the page which tells the map your API key:

```html
<script async defer
src="https://maps.googleapis.com/maps/api/js?key=A1b2c3d4e5f6g7h8i9j10k11&callback=initMap">
</script>
```

Immediately after `initMap` and before the `"`, add `&libraries=geometry`, being careful that you do not add any spaces.

+ Now locate your `set_my_position()` function and position your cursor immediately below the line `old_position = marker;`.

+ Create a for loop which will loop through the `all_markers` array

[[[generic-javascript-for-loop]]]

+ Inside your loop, use this code to calculate the distance between the current position (`pos`) and each marker, one by one.

```javascript
var distance = google.maps.geometry.spherical.computeDistanceBetween(pos, all_markers[i].getPosition());
```
+ Add an `if` statement immediately below to check whether the distance between the player and the marker we are currently examining is less than the tolerance

```javascript
if( distance < tolerance ){
    alert("Found it!")
}
```
- what did they find
- remove the marker from the map
- add a score
