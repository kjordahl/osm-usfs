This repository is a staging area for National Forest Service data to
be uploaded into OpenStreetmaps. National data available from
http://data.fs.usda.gov/geodata/edw/datasets.php include:

- Administrative Forest Boundaries (`S_USA.AdministrativeForest.shp`)
- Wilderness Areas (`S_USA.Wilderness.shp`)
- Wilderness Areas: Legal Status (`S_USA.WildernessStatus.shp`)

Currently I am focusing on regions in the Inland Northwest (roughly
between the Cascades and the Continental Divide), particularly Idaho,
which has none of its over 20 million acres of National Forest land in
OSM.

The files in the `osm` directory have been converted to WGS-84 datum
and OSM format. Before uploading to OSM directly, more quality control
needs to be done. For example, polygons should be validated and split
to no more than 2000 vertices.  After that, they should be checked
against data already in OSM to resolve any conflicts (for example,
part of Colville National Forest is already in OSM).

For example, the administrative boundary for Bois National Forest was
converted with:

    $ ogr2ogr -fid 38 -f "ESRI Shapefile" -t_srs EPSG:4326 Boise.shp S_USA.AdministrativeForest.shp
and exported to OSM with the JOSM editor.

GeoJSON files are provided for convenience, they should be equivalent
to the `.osm` files but can be rendered directly on GitHub.
