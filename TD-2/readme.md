#TD2
## Creating Tables with Spatial Columns
# TD-2: Creating Tables with Spatial Columns

## 1. Create a Spatial Table (Points)
### Step 1: Create the `points_of_interests` Table
1. Open **pgAdmin 4**.
2. Run the following command in the **Query Tool**:
```sql
CREATE TABLE points_of_interests (
id SERIAL PRIMARY KEY,
name VARCHAR(255),
geom GEOMETRY(Point, 4326)
);
# Step 2: Insert Data with QGIS

### PostgreSQL Connection
1. Launch QGIS.
2. To establish a PostgreSQL connection:
- Right-click on **PostgreSQL** in the **Explorer** panel.
- Click on **New Connection**.
- Fill in the connection information (host, database, user, password).
- Click on **Test Connection**, then validate.
3. Double-click on the **points_of_interests** table to add it as a layer in QGIS.
4. Activate the edit mode.
5. Add points directly on the map.
6. Save the changes.

---

# Step 3: Verification in pgAdmin

1. Open **pgAdmin**.
2. Run the following query to verify the data:
```sql
SELECT * FROM points_of_interests;
# 2. Create a Spatial Table (Polygons)

### Step 1: Create the `zones_protegees` Table

1. Open **pgAdmin 4**.
2. Run the following command in the **Query Tool**:
```sql
CREATE TABLE zones_protegees (
id SERIAL PRIMARY KEY,
name VARCHAR(255),
geom GEOMETRY(Polygon, 4326)
);
# Step 2: Insert Data with QGIS

1. **Repeat the PostgreSQL connection steps in QGIS** as mentioned before.
2. **Double-click on the `zones_protegees` table** to add it as a layer.
3. **Enable edit mode**.
4. **Add polygons** directly on the map.
5. **Save changes**.

---

# Step 3: Verification in pgAdmin

1. Open **pgAdmin**.
2. Run the following query to check the data:
```sql
SELECT * FROM zones_protegees;
# Create a Spatial Table (LineStrings)

## Step 1: Create the `routes` Table

1. Open **pgAdmin 4**.
2. Run the following command in the **Query Tool**:
```sql
CREATE TABLE routes (
id SERIAL PRIMARY KEY,
name VARCHAR(255),
geom GEOMETRY(LineString, 4326)
);
# Step 2: Insert Data with QGIS

1. **Repeat the PostgreSQL connection steps in QGIS** as mentioned before.

2. **Double-click on the `routes` table** to add it as a layer in QGIS.

3. **Enable edit mode** by clicking the pen icon or selecting the **Edit Mode** option from the layer context menu.

4. **Add LineStrings** directly on the map by drawing segments representing roads, paths, or other linear features. You can use the **Draw Line** tool to add geometries.

5. **Save changes** by clicking the floppy disk icon or selecting **Save Changes** from the **Edit** menu.

# Step 3: Verification in pgAdmin

1. **Open pgAdmin**.

2. Run the following query to verify the data inserted into the `routes` table:
```sql
SELECT * FROM routes;
