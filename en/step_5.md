## Create the markers

+ Below the line `var zombie_map;` add another line to create a variable called `all_markers` and set it equal to `[]` which is a blank array. This will eventually store a reference to each of the markers we are about to create.

+ Position your cursor inside the `initMap()` function, just after the code for creating the zombie map.

![Add marker code here](images/add-marker-code.png)

+ Create a **for loop** that will run once for every marker in the `markers` array we created in the previous step.

[[[generic-javascript-for-loop-array]]]

Inside the **for loop** the line of marker data we are currently looking at is `markers[i]` - the loop will add one to the variable `i` each time it runs, so we will be looking at each line of data, one by one.

The first line of data looks like this:

```html
51.90769026213801 -2.068905830383301 zombie.png
```

We want to end up with this data as an array so we will need to split it up just like we did in the previous step.

+ Add all of the rest of the lines of code in this step inside your **for loop**. First, `trim()` any unwanted spaces from the beginning and end of the data

```JavaScript
var marker_data = markers[i].trim();
```

+ Now split the string up just like we did before, but this time we will split wherever there is a space

```JavaScript
marker_data = marker_data.split(" ");
```

We will end up with an array called `marker_data` which contains three values. In order, these are: the latitude, the longitude and the marker image file.

+ Create variables to name each of these values. The first is done for you.

```JavaScript
var latitude = marker_data[0];
var longitude = ?;
var emoji = ?;
```

+ To be able to add the marker at the correct position, you need to create a `LatLng` object.

```JavaScript
var marker_position = new google.maps.LatLng(?, ?);
```

Add this line of code immediately underneath the previous line, replacing `?` with the latitude and longitude variables.

+ Still inside the loop, write some code to create a marker at the `marker_position`, with the `icon:` set to the emoji variable.

[[[generic-api-google-maps-marker]]]

--- hints ---
--- hint ---
Instead of putting in a fixed latitude/longitude like in the example, use the `marker_position` variable to tell the marker where it should be placed.
--- /hint ---

--- hint ---
Check that the name of the map (in the example `mymap`) has the same name as the map you have created.
--- /hint ---

--- hint ---
You can add an icon by adding another line within the marker to specify `icon: "nameofpicture.png"`. Don't forget to put a comma at the end of the map line to say that there is another marker property you would like to set.
--- /hint ---

--- hint ---
If you specify a fixed filename like `"nameofpicture.png"` then the marker icon will always be the same. Which number item in the `marker_data` array contains the picture for each piece of data? Don't forget that we start counting in the array at 0, so the first item in the array (the latitude) is `marker_data[0]`.
--- /hint ---

--- /hints ---

+ Immediately after the end of the marker code, but still within the loop, add this line to save a reference to this marker in our list of `all_markers`. We will need this list in a later step.

```JavaScript
all_markers.push(marker);
```

+ Save your code and refresh the page. Test that all of your markers show up properly on the map. If they do not show up properly, perhaps you could look in the JavaScript **console** to see if there are any error messages for you to resolve?

[[[generic-javascript-opening-console]]]
