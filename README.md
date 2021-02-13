# IntersectionDetector

IntersectionDetector is a Python library used to Detect Geospatial Intersections between a single LineString Shape vs. a List of Polygons

## Requirements

pip install -r -requirements.txt

geopandas==0.8.2
pygeos==0.7.1
gdal==2.4.2
fiona==1.8.18
shapely==1.7.1
pytest==3.6.4
Cython==0.29.21
pyproj

## Installation


pip install -e .


## Usage

```python
from shapely.geometry import Polygon, LineString
import pytest

from IntersectDetector.IntersectDetector import IntersectDetector as IDetect 
from IntersectDetector.ShapeStringUtils import ShapeStringUtils as SSUtils

idetect = IDetect()
idetect.load_polygons_file('data/polygons.txt') 


#First LineString Coordinates provided
coords_inputstring = '-90.16685485839844,35.17156320800291,-90.142822265625,35.266925688950074,-90.18539428710938,35.31008240129421,-90.27122497558594,35.303918565311704'
cords_xy = [(float(a),float(b)) for a,b in zip(*[iter(coords_inputstring.split(','))]*2)]


#Concise output: List of Polygons
intersect_list = idetect.detect_intersections(cords_xy, returnGPD=False)


#Verbose output: Dataframe of Polygons
intersect_details = idetect.detect_intersections(cords_xy, returnGPD=True)


```


## License
Beta
