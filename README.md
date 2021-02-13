# IntersectionDetector

IntersectionDetector is a Python library used to Detect Geospatial Intersections between a single LineString Shape vs. a List of Polygons

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
