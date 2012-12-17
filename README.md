# Boundary Conversions

A set of tools and data for converting boundary shapefiles to SVG, GeoJSON, etc to be used client side.

## Method

1. Find shapefile
2. Use [MapShaper](http://mapshaper.com/test/MapShaper.swf) to simplify.  This is used because it perserves intersection points, otherwise scripting would make more sense.
3. Use ogr2ogr to create GeoJSON file:  ```ogr2ogr -f GeoJSON -t_srs EPSG:4326 mn-county-2010/geojson-dp-60/mn-county-2010.json mn-county-2010/shp-dp-60/county2010.shp```

### JSONP

If used in browsers, you may need to get this data via JSONP.  Here are a couple commands to make JSONP.

   echo "mn_county_2010(" > mn-county-2010/geojson-dp-60/mn-county-2010.jsonp && \
   cat mn-county-2010/geojson-dp-60/mn-county-2010.json >> mn-county-2010/geojson-dp-60/mn-county-2010.jsonp && \
   echo ");" >> mn-county-2010/geojson-dp-60/mn-county-2010.jsonp;