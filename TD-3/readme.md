#TD3
##Spatial SQL Functions
###How many parcels are located within 1 km of a fire point?
# TD-3: Spatial SQL Functions

## Objective
To determine how many parcels in Florida are located within a 1 km radius of a fire point, using PostGIS and QGIS.

---

## Step 1: Import the Shapefile into PostGIS
1. Download the shapefile of the Florida parcels. (To search for the st_xxxx features, please refer to the official PostGIS
documentation https://postgis.net/docs/reference.html)
2. Open **PostGIS Shapefile Import/Export Manager**:
- Press the **Windows** key, search for "Shapefile" and open the tool.
- Select the shapefile of the Florida parcels.
- Import it into a PostgreSQL table.

---

## Step 2: Verify Imported Data
1. Open **pgAdmin**.
2. Run the following queries to verify the data:
```sql
SELECT COUNT(*) FROM parcels;
SELECT * FROM parcels LIMIT 5;
## Step 3: Select Fire Point

### Identify the centroid of the parcel `gid = 462273`:
```sql
SELECT ST_Centroid(geom) AS fire_point
FROM parcels
WHERE gid = 462273;
# Steps to Identify the Risk Area and Analyze the Data

## Step 4: Identify the Risk Area (1 km around the Fire Point)

### Create a QGIS layer for the risk area
1. **Duplicate the `parcels` layer in QGIS** and rename it **fire-risk**.
2. Right click on the **fire-risk** layer and select **Filter**.
3. Add the following expression to the filter box:
```sql
ST_DWithin(
geom,
(SELECT ST_Centroid(geom)
FROM "public"."parcels"
WHERE gid = 462273),
1000
)
## Add a Second Fire
Modify the filter to include two fire points (`gid = 460957` and `gid = 462273`):

```sql
ST_DWithin(
geom,
(SELECT ST_Union(ST_Centroid(geom))
FROM "public"."parcels"
WHERE gid IN (460957, 462273)),
1000
)
# Step 5: Spatial SQL Queries

### Question 1: How many parcels are in within a 1 km radius around the two parcels (`gid = 460957` and `gid = 462273`)?

```sql
SELECT COUNT(*)
FROM parcels
WHERE ST_DWithin(
geom,
(SELECT ST_Union(ST_Centroid(geom))
FROM parcels
WHERE gid IN (460957, 462273)),
1000
);
### Question 2: What is the total area of ​​the parcels near the fire?

```sql
SELECT SUM(ST_Area(geom::geography))
FROM parcels
WHERE ST_DWithin(
geom,
(SELECT ST_Union(ST_Centroid(geom))
FROM parcels
WHERE gid IN (460957, 462273)),
1000
);
# Step 6: Final Result

### Display in QGIS
- The risk zones (1 km around the fire points) are displayed on the map.
- Apply custom symbology (e.g. bright color or border) to differentiate the risk zones.

### SQL Query Results
1. **Number of parcels in the risk zone:**
For example: `42`.

2. **Total area of ​​parcels:**
For example: `123456.78 m²`.
