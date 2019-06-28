---
title: Getting Started with Enterprise Geodatabases
permalink: "/:basename"
layout: git-wiki-default
---

## Getting started with enterprise geodatabases at NBMG
We now have a server that will be hosting all collaborative databases. This will look and feel fairly similar to file geodatabases with a few key differences.

### Restrictions on enterprise Geodatabases
* You cannot change geodatabase name after creation
* Geodatabase name must be unique among all enterprise database instances on a server
* PostgreSQL in particular does not recognize case for the following
  - Names of: databases, schemas, users, tables, indexes, columns

You cannot do the following with _versioned_ data (see [Register and unregister data as versioned](http://desktop.arcgis.com/en/arcmap/latest/manage-data/geodatabases/a-quick-tour-of-registering-and-unregistering-data-as-versioned.htm) for more information)
* Create a topology. (need to create it beforehand)
* Create a geometric network.
* Add or remove a feature class from a geometric network.
*	Create a network dataset.
* Add or remove a feature class from a network dataset or make other schema changes.
* Rasters cannot be versioned.

Note that all of these types of data may still exist in an enterprise geodatabase - these are just *versioning* restrictions.

See Esri's [An Overview of Versioning](http://desktop.arcgis.com/en/arcmap/10.3/manage-data/geodatabases/an-overview-of-versioning.htm) for more information.

## Setup

### Creating a new enterprise geodatabase
The database administrator must create the enterprise geodatabase. In order to request a new geodatabase, email eodean@unr.edu with the following information -
1. Geodatabase name
2. List of users who need access and their permission levels (read, write, edit, delete)
    - IP addresses will be needed for each user for the first time that they log in to the new database server. If you already have a login to an enterprise geodatabase and you are requesting a new gdb, your IP is not needed again.
3. Estimated size of data in database
4. Estimated lifetime of project before archival

### Adding an enterprise geodatabase to your ArcGIS environment
Note: You need to be running at least 10.6 of any ArcGIS product to connect to the database.

From the catalog pane in ArcMap or ArcCatalog:
1. Click “Add Database Connection”
2. Under “Database Platform,” choose “PostgreSQL”
3. In the “Instance” box, type “strata.unr.edu”
4. Under “Authentication Type,” choose “Database Authentication”
5. Enter your username and password given to you by the database administrator. Your username will be the same as your netID, and the dbadmin will assign you a password and send it to you securely. This will be the same password that you will use to log in to all geodatabases that you have permission to access.
6. Wait a moment until the “Database” field is populated. Choose the appropriate geodatabase to connect to.

Alternatively, the database administrator may securely send you a connection file and instructions to use it.

### Permissions
You may have different permissions in each enterprise geodatabase. Generally, all faculty and staff will be given complete read/write permissions. There are three "roles" in the database management system from which all users inherit their permissions.

- gis - full permissions EXCEPT create and delete databases
- editor - may edit data but may not add or delete data
- viewer - may view data only

When adding datasets and granting permissions to others to read/write to it (see [adding data](#adding-data) section), you may add based on role rather than individual users.

## Versioning workflows

[A great example of a versioning workflow](http://desktop.arcgis.com/en/arcmap/latest/manage-data/geodatabases/version-creation-and-permissions-example.htm)

<h3 id="adding-data">Adding data</h3>
You can copy data from a file geodatabase to an enterprise geodatabase using copy and paste. You can also create datasets from scratch in the same way that you create them in file geodatabases.

After adding a dataset to an enterprise geodatabase, **you must grant other users access to view and edit the data**. Right click on the dataset, then click Manage, then Privileges.

Make sure you add ALL privileges to the "gis" role, unless you only want certain users to access the data. All faculty and staff users inherit privileges from the gis role. The two other roles, viewer and editor may be used to restrict access.

### Register a dataset as versioned
Each feature class and dataset in the enterprise gdb needs to be explicitly registered as versioned. Right click on the dataset, point to “Manage,” and click “Register as Versioned.” Only the person who added/created the dataset can register it as versioned. If you are adding data to an enterprise geodatabase and want others to be able to collaborate, go through this step immediately after creating the data. Otherwise, read/write locks will be placed on the data while editing, as they are with normal file geodatabase workflows.

There are two different versioning options –
“Move data to base” if you don’t need to:
* Edit feature classes that participate in a topology, network dataset, or geometric network.
* Archive data with the archiving functionality built into the geodatabase.
*	Make use of geodatabase replication.

“Do not move data to base” if you want to:
*	Undo and redo edits.
*	Perform long transaction edits.
*	Use named versions for designs and projects.
*	Use geodatabase archiving.
*	Use replication.
*	Place a unique constraint on the base table of a feature class

Generally, we will want to select "Do not move data to base." [Read more about these topics here](http://desktop.arcgis.com/en/arcmap/10.3/manage-data/geodatabases/a-quick-tour-of-registering-and-unregistering-data-as-versioned.htm)

### Create a version
1. Open the Version Manager dialog box using one of the following methods:
    - In the Catalog tree, right-click a connection to the geodatabase, point to Administration, click Administer Geodatabase, then click the Versions tab (this prefills much of the information for you).
    - In ArcMap, click the Version Manager button on the Versioning toolbar.
1. To create a new version, right-click the version from which you want to derive the new version and click New.
1. Type a name for the new version. Note that the length of the version name is limited to 62 characters. Type a description of the version. You can use the version description to provide additional information regarding the version's purpose. The size limit on the description is 62 characters.
1. Choose the desired access level for the version: Private, Public, or Protected.
  - Private: Only the owner or the geodatabase administrator may view the version and modify versioned data or the version itself.
  - Protected: Any user may view the version, but only the owner or the geodatabase administrator may edit datasets in the version or the version itself.
  - Public: Any user may view the version. Any user who has been granted read/write (update, insert, and delete) permissions on datasets can modify datasets in the version.
1. Click OK to create the new version.
See [creating a version](http://desktop.arcgis.com/en/arcmap/latest/manage-data/geodatabases/creating-versions-and-setting-permissions.htm) for more information.

### Editing
[Make sure you are using the correct version while editing](http://desktop.arcgis.com/en/arcmap/10.3/manage-data/geodatabases/changing-versions-in-arcmap.htm). Only one person should edit a version at a time. In general, each user will have at least one version of a geodatabase.

### Merging your edits back into the master version
After you've completed an edit or an addition, you will want to merge your changes back into the Base version. In order to do this, you will need to first "reconcile" (pull changes from Base into your version), and then "post" (contribute your changes to the upstream version).

#### Reconcile and Post
It's a good idea to reconcile your version with the upstream versions often to avoid conflicts.

1. Right click on your connection to the database and select "Administer Geodatabase."
2. Right click on the version that you want to reconcile (this is the version you've been editing) - then click "Reconcile Versions." This will open the Reconcile Versions toolbox and it will be prepopulated with most settings that you need.
3. Under "Target Version," make sure you have selected the "Base" version, not "DEFAULT."
4. Under "Edit Versions" make sure to de-select all other versions under "Edit Versions" and only have your version selected.
5. Choose which type of "Conflict Definition" you need (see tool help for descriptions)
6. Choose which type of "Conflict Resolution" you need (see tool help for descriptions)
7. If you are ready to post your changes to the upstream Base version, Click "Post Versions after Reconcile." If you choose this option, you should also click "Abort if Conflicts Detected." You can go through this workflow twice as well - once to reconcile, once to post. If you are done editing your downstream version, click "Delete Versions After Post."

[More information on reconcile and post can be found here.](http://desktop.arcgis.com/en/arcmap/10.6/manage-data/geodatabases/a-quick-tour-of-reconciling-a-version.htm)

### Offline workflows
In order to work on a database offline, you will need to use Esri's "distributed workflow" to replicate the enterprise geodatabase to a local file geodatabase. See [understanding distributed data](http://desktop.arcgis.com/en/arcmap/latest/manage-data/geodatabases/understanding-distributed-data.htm) for more information.

A replica differs from a version in that the entirety of the database is copied and saved locally, whereas a version only saves information that is different from the master version.

#### Before going to the field/going offline
1. Have the database administrator create an enterprise geodatabase for your project.
2. Connect to the enterprise geodatabase.
3. Create a file geodatabase on your computer that you will use to store your local version.
4. Navigate to the "Create Replica" tool (ArcToolbox > Distributed Geodatabase > Create Replica)
5. In the "Replica Datasets" box, chose the feature sets to replicate locally. You can make a skeleton feature set if you don't have any data yet.
6. Under Replica Type, choose "CHECK_OUT" for offline editing in a file geodatabase. With this workflow, you check the data out once, work locally, and once you check your data back in you can no longer synchronize additional edits. See [replication types] (http://desktop.arcgis.com/en/arcmap/latest/manage-data/geodatabases/replication-types.htm) for more information.
  - Note: If you need to be checking in and out data and syncing multiple times during the course of your work, see the section on [offline enterprise multi-sync workflow below](#offline-multi-sync)
7. Make your offline edits in the replica file geodatabase.

#### Once you're back in service ####
At this point, you have completed your offline editing and you are ready to check your changes back into the enterprise geodatabase server.

1. Right click on your local replica (your file geodatabase) in which you have been making the changes. Select Distributed Geodatabase > Synchronize changes.
2. All of the required settings should be prefilled. Geodatabase 1 should be your local geodatabase, the replica to synchronize should be the version that you are synchronizing to, and the replica type should be from Geodatabase 1 to Geodatabase 2.
3. Press next, and choose how to resolve conflicts if they arise.
4. Check that your changes have been pushed to the correct version in the enterprise gdb. Then, if you don't need to make any more edits and want to merge your changes with the Base version, go through the procedure of reconciling versions (detailed above).

<h4 id="offline-multi-sync">Offline Enterprise Multi-Sync Databases</h4>
To take advantage of multi-sync functionality (check in edits multiple times while in the field), you have to create a local enterprise geodatabase to sync to. This requires having SQL Server Express installed on your local computer.

Stay tuned for more in this section....

### Workflow example
1.	Cartography requests a new enterprise geodatabase
  - Emily creates the database and database Users
2.  Cartography adds the skeleton structure to the database, sets the database as versioned
3.	Carto loads the data into the database and is responsible for maintaining it.
4.	Carto registers the datasets as versioned.
5.	Carto sets the Default version to “protected,” and then creates a working version called Base to use for edits. Base is set to “public.” All users can view the Default database, but cannot edit it.
6.	Editors will create their own versions from the Base version. Each user/editor should have their own working version.
7.	Each editor will merge their versions back to Base after edits are complete.
    - There are two operations in enterprise gdbs related to versioning: Reconciling and Posting. Reconciling involves pulling upstream changes down. For example, if you are editing eodean_base which you’ve versioned from Base and Base has a change posted to it from another version, you must Reconcile your version with Base to keep up to date. Then, when you are ready to merge eodean_base into Base, you Post your changes.
    - Conflicts are more likely to arise if multiple people are editing features that are in close proximity.
10.	Once everything has been reconciled and the versions have been deleted, the database admin compresses the gdb. This doesn’t delete all of the versioning lineage, just cleans up unused files.
