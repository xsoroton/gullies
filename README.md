# All Roads To

to Brisbane, Australia -27.468617, 153.026739
to Moscow, Russia,  55.7549391, 37.6115628
to Shanghai, 31.2231338, 120.9162975

project forked from https://github.com/krithin/gullies to generate map to specific needs (to make nice images)


### Need to run local OSM server
to run it in docker https://github.com/Project-OSRM/osrm-backend#using-docker
get data here: http://download.geofabrik.de/
```
docker run -t -i -p 5000:5000 -v $(pwd):/data osrm/osrm-backend osrm-routed --algorithm mld /data/australia-latest.osm.pbf
```

check original project readme if have a problems https://github.com/krithin/gullies/blob/master/README.md


### working on my machine :D
```
python3 getlocations.py australia-latest.osm.pbf 20000 > data/locations.csv
cat data/locations.csv | python3 getroutes.py http://localhost:5000 > data/routes.txt
cat data/routes.txt | python3 collatesegments.py australia-latest.osm.pbf > data/routescollated.txt
cat data/routescollated.txt | python3 simplifysegments.py 2 > data/routessimplified.txt
cat data/routessimplified.txt | python3 plotmatplotlib.py img/RoadsToBrisbane_20000_segment2_nice2.png
```

## Gallery
Brisbane, Australia -27.468617, 153.026739
![Brisbane 30000 locations](img/RoadsToBrisbane_30000_segment2_thin_lines.png)

Sydney, Australia -33.8469759, 150.3715249
![Brisbane 30000 locations](img/RoadsToSydney_30000_segment2_thin_lines.png)

Routes from 30000 locations to Brisbane, Australia -27.468617, 153.026739
![Brisbane 30000 locations](img/RoadsToBrisbane_30000_segment2.png)

Shanghai, China 31.2231338, 120.9162975
![Shanghai 20000 locations](img/RoadsToShanghai_20000_segment2_thin_lines.png)

Shanghai, China 31.2231338, 120.9162975
![Shanghai 20000 locations](img/RoadsToShanghai_20000_segment2.png)

Moscow, Russia 55.7549391, 37.6115628
![Moscow 15000 locations](img/RoadsToMoscow_15000_thin_line.png)
