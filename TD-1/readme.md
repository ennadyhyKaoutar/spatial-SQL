#TD1
##Installing PostGis and Creating a Spatial DB
# Installing PostGIS and Creating a Spatial Database

## 1. Download and Install PostgreSQL
1. Go to the [PostgreSQL download page](https://www.postgresql.org/download/) to download the latest version compatible with your operating system (Linux, MacOS, Windows, BSD, Solaris).
2. Follow the installation guide to install PostgreSQL on your machine.
3. During the installation, set a password for the postgres user. **Make a note of this password**, as you will need it to connect to PostgreSQL.

## 2. Download and Install PostGIS
1. During the installation of PostgreSQL, check **all the required components**, including **Stack Builder**.
2. At the end of the installation, **launch Stack Builder**. The latter will allow you to download PostGIS, a spatial database extension.
3. In Stack Builder:
- Select the PostgreSQL version corresponding to your installation.
- Choose the **PostGIS** extension (it will usually be checked automatically).
- You can check "Create a spatial database" if you wish, but this tutorial will guide you through the creation via pgAdmin 4.
4. Follow the steps of the wizard and specify the installation folder.
5. Once the installation is complete, click **Close** to finalize the installation.

## 3. Create a Database with pgAdmin 4
1. Launch **pgAdmin 4**, a PostgreSQL database management tool.
2. Log in with the password you defined during installation.
3. Expand the **Servers** section, right-click on PostgreSQL > **Create** > **Database**.
4. Give your database a name (e.g. spatial-db-1) and click **Save**.

## 4. Add the PostGIS Extension to the Database
1. In pgAdmin 4, expand the **Databases** section and select your database (spatial-db-1).
2. Right-click on your database and click **Query Tool**.
3. In the query editor, type the following command:

sql
CREATE EXTENSION postgis;
# Check Query Execution in pgAdmin

1. **Execute the query in pgAdmin**:
- Click the **Execute** button in the toolbar or press the **F5** key on your keyboard to execute the query you entered in the **Query Tool**.

# Verify PostGIS Installation

1. **Expand your database**:
- In pgAdmin, locate your database, for example `spatial-db-1`.

2. **Go to `Schemas`**:
- Click on **Schemas** > **Public** > **Tables**.

3. **Check for the presence of the `spatial_ref_sys` table**:
- The `spatial_ref_sys` table contains the information
