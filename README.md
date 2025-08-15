# spatial-utils
Collection of utilities for working with spatial and geometric data

### Loading Standardized Polars and GeoPandas DataFrames
```python
from spatial_utils.io import get_preprocessor

# Load standardized IST data
pp = get_preprocessor('/path/to/your/raw/xenium/data')
tx = pp.transcripts
bd = pp.boundaries
```

### Converting to GeoPandas/CuSpatial DataFrames
```python
from spatial_utils.geometry import (
    points_to_geoseries,
    polygons_to_geoseries,
)

gdf = points_to_geoseries(
    np.array([[0,0], [1,1]]),  # see docstring for other valid inputs
    backend='geopandas',       # also accepts 'cuspatial'
)

gdf = polygons_to_geoseries(
    [                  # see docstring for other valid inputs
        shapely.Polygon([[0,0], [0,1], [1,1], [1,0], [0,0]]),
        shapely.Polygon([[1,1], [1,2], [2,2], [2,1], [1,1]]),
    ],
    backend='geopandas',       # also accepts 'cuspatial'
)
```