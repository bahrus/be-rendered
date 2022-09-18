# be-rendered [TODO]

element behavior / decorator / custom attribute equivalent of [litter-g](https://github.com/bahrus-litter-g)

```html
<form>
    <label>
        Latitude
        <input name=latitude>
    </label>
    <label>
        Longitude
        <input name=longitude>
    </label>
    <script nomodule be-rendered='["latitude", "longitude"]'>
        ({latitude, longitude}) => html`<a href="http://www.gps-coordinates.org/my-location.php?lat=${latitude.value}&lng=${longitude.value}" target="_blank">
            (${latitude},${longitude})
        </a>` 
    </script>
</form>
```

Uses lit-html.  Renders before the script element.

The notation above is shorthand for:

```html
<form>
    <label>
        Latitude
        <input name=latitude>
    </label>
    <label>
        Longitude
        <input name=longitude>
    </label>
    <script nomodule be-exportable be-rendered='{
        "args":{
            "latitude": {
                "observeName": "latitude",
                "on": "input",
                "vft": "."
            },
            "longitude": {
                "observeName": "longitude",
                "on": "input",
                "vft": "."
            }
        }
    }'>
        ({latitude, longitude}) => html`<a href="http://www.gps-coordinates.org/my-location.php?lat=${latitude}&lng=${longitude}" target="_blank">
            (${latitude},${longitude})
        </a>` 
    </script>
</form>
```

It leverages the robust syntax of [be-observant](https://github.com/bahrus/be-observant).