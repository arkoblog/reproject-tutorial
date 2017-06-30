# How to use reproject library to change projections of a geojson file

### Install reproject
`sudo npm i -g reproject`

### Create a file called crs-defs.json with the following content.
```javascript
{
    "EPSG:3857": "+proj=merc +a=6378137 +b=6378137 +lat_ts=0.0 +lon_0=0.0 +x_0=0.0 +y_0=0.0 +k=1.0 +units=m +nadgrids=@null +wktext +no_defs +over",
    "EPSG:3006": "+proj=utm +zone=33 +ellps=GRS80 +towgs84=0,0,0,0,0,0,0 +units=m +no_defs",
    "EPSG:4326": "+proj=longlat +ellps=WGS84 +datum=WGS84 +no_defs"
}
```

### Use the following command  in your terminal to change projections of the geojson file.
`echo "$(cat Nepal_National_Park.geojson)" | reproject  --crs-defs=crs-defs.json --from=EPSG:3857 --to=EPSG:4326 > output.geojson` 


I have not included the geojson file in this repo for security reasons.

Cheers,
Arogya