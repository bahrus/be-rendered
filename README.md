# be-rendered [TODO]

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
    <script nomodule be-calculating='["latitude", "longitude"]'>
        ({latitude, longitude}) => html`<a href="http://www.gps-coordinates.org/my-location.php?lat=${_latitude}&lng=${_longitude}" target="_blank">
            (${_latitude},${_longitude})
        </a>` 
    </script>
</form>
```

Uses lit-html.  Renders before the script element.