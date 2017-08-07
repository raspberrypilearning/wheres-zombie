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

+ At the moment we are not sure what it is they have found. Instead of just saying "Found it", lets tell the player what it is they have found by getting the name of the icon used and removing the `.png` part from the end. For example, if they found `hospital.png` the alert will say `Found the hospital`

```javascript
var what_is_it = all_markers[i].getIcon();
what_is_it = what_is_it.replace(".png", "");

alert("Found the " + what_is_it );
```

+ We also want to remove the found marker from the map so that the game does not keep telling them they found the same thing. The marker we are looking at is called `all_markers[i]` in this case. See if you can remember how to remove a marker from the map and add the code just underneath your alert.

--- hints ---
--- hint ---
We removed a marker from the map before when we stopped the attack of the smileys.
--- /hint ---

--- hint ---
To remove a marker from the map, set the map of the marker to `null` which means no map in this case.
--- /hint ---

--- hint ---
You will need to use the `.setMap()` method on the marker.
--- /hint ---

--- /hints ---

+ Finally, let's add a score. Once again, locate the line `var zombie_map;` and add another line of code to create a variable called `score`.

+ If the player found a zombie, in my game they don't get any points. Perhaps if you are feeling particularly mean you could make your player get minus points in your game! If they found a hospital or a weapon store they get 10 points.

![Add a score](images/add-score.png)

Here is some pseudo code for the code we want to add. Translate this pseudo code into real code and add it to your program.

```html
IF what they found isn't a zombie
    score + 10 points
    ALERT Your score is + score
```

--- hints ---

--- hint ---
We already worked out what they found and stored it in the variable `what_is_it`. Use this to create a condition which says that thec contents of this variable is not equal to (`!=`) zombie.
--- /hint ----

--- hint ---
You can add on points to a variable like this:

```javascript
score += 10
```
This means "Score is whatever it was before, but plus 10".
--- /hint ----

--- hint ---
Solution:
```javascript
if( what_is_it != "zombie"){
    score += 10;
    alert("Your score is " + score);
}
```
--- /hint ----

--- /hints ---
