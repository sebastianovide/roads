## Data

### Formatting

In order to be eligible for parsing, OS and OSM data sets need to be converted into JSON format. Once you have your original GML/OSM/XML files, these can be converted into JSON by running the following commands. When converting OSM Data Files, it may ask you to confirm which layer you would like to transform, in this case, append the word `lines` to the end of the command below. In order to have access to the `ogr2ogr` commands, make sure you have [gdal](http://www.gdal.org/) installed on your machine.

```
ogr2ogr -dim 2 -f GeoJSON -s_srs "+proj=tmerc +lat_0=49 +lon_0=-2 +k=0.999601 +x_0=400000 +y_0=-100000 +ellps=airy +units=m +no_defs +nadgrids=./OSTN15_NTv2_OSGBtoETRS.gsb" -a_srs EPSG:4326 "./name_of_output.json" "./name_of_input_file"
```

Once a file has been successfully converted, these files can then be parsed to extract all of the one-way roads so that they can be compared across data sets in order to determine identical roads.