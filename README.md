# Roads To Brisbane, Australia

shortest way to BRISBANE -27.468617, 153.026739

project forked from https://github.com/krithin/gullies to generate map to my specific needs


### Need to run local OSM server
to run it in docker https://github.com/Project-OSRM/osrm-backend#using-docker
get data here: http://download.geofabrik.de/australia-oceania/australia.html
```
docker run -t -i -p 5000:5000 -v $(pwd):/data osrm/osrm-backend osrm-routed --algorithm mld /data/australia-latest.osrm
```

check original project readme if have a problems https://github.com/krithin/gullies/blob/master/README.md


### working on my machine :D
```
python3 getlocations.py australia-latest.osm.pbf 1000 > data/blocations.csv
cat data/blocations.csv | python3 getroutes.py http://localhost:5000 > data/broutes.txt
cat data/broutes.txt | python3 collatesegments.py australia-latest.osm.pbf > data/broutescollated.txt
cat data/broutescollated.txt | python3 simplifysegments.py 2 > data/broutessimplified.txt
cat data/broutessimplified.txt | python3 plotmatplotlib.py img/RoadsToBrisbane_1000_segment2.png
```

## Gallery
Australia, Brisbane
![Brisbane 1000 locations](img/RoadsToBrisbane_1000_segment2.png)

Australia, Brisbane
![Brisbane 10000 locations](img/RoadsToBrisbane_10000_segment2.png)

Australia, Brisbane
![Brisbane 20000 locations](img/RoadsToBrisbane_20000_segment2.png)

