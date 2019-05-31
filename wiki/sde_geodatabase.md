---
title: Getting Started with Enterprise Geodatabases
permalink: "/:basename"
layout: git-wiki-default
---

## Getting started with enterprise geodatabases at NBMG
We now have a server that will be hosting all collaborative databases. This will look and feel fairly similar to file geodatabases with a few key differences.

### Adding a geodatabase to your ArcGIS environment
Note: You need to be running at least 10.6 of any ArcGIS product to connect to the database.

From the catalog pane in ArcMap or ArcCatalog:
1. Click “Add Database Connection”
2. Under “Database Platform,” choose “PostgreSQL”
3. In the “Instance” box, type “strata.unr.edu”
4. Under “Authentication Type,” choose “Database Authentication”
5. Enter your username and password given to you by the DB administrator
6. Wait a moment until the “Database” field is populated. Choose the appropriate geodatabase to connect to.

### Permissions

You may have different permissions in each enterprise geodatabase. Generally, all faculty and staff will be given complete read/write permissions.

### Versioning workflows
A great example of a versioning workflow –
http://desktop.arcgis.com/en/arcmap/latest/manage-data/geodatabases/version-creation-and-permissions-example.htm

Keep in mind that you cannot do the following with versioned data:
* Create a topology.
* Create a geometric network.
* Add or remove a feature class from a geometric network.
*	Create a network dataset.
* Add or remove a feature class from a network dataset or make other schema changes.
Rasters cannot be versioned.

### Register a dataset as versioned
Each feature class and dataset in the enterprise gdb needs to be explicitly registered as versioned. Right click on the dataset, point to “Manage,” and click “Register as Versioned.” Only the person who added/created the dataset can register it as versioned. If you are adding data to an enterprise geodatabase and want others to be able to collaborate, go through this step immediately after creating the data.
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

### Add a version
http://desktop.arcgis.com/en/arcmap/latest/manage-data/geodatabases/creating-versions-and-setting-permissions.htm
1. Open the Version Manager dialog box using one of the following methods:
1. In the Catalog tree, right-click a connection to the geodatabase, point to Administration, click Administer Geodatabase, then click the Versions tab.
1. In ArcMap, click the Version Manager button on the Versioning toolbar.
1. To create a new version, right-click the version from which you want to derive the new version and click New.
1. The New Version dialog box appears.
1. Type a name for the new version.
1. The length of the version name is limited to 62 characters.
1. Type a description of the version.
1. You can use the version description to provide additional information regarding the version's purpose. The size limit on the description is 62 characters.
1. Choose the desired access level for the version: Private, Public, or Protected.
1. Private: Only the owner or the geodatabase administrator may view the version and modify versioned data or the version itself.
1. Protected: Any user may view the version, but only the owner or the geodatabase administrator may edit datasets in the version or the version itself.
1. Public: Any user may view the version. Any user who has been granted read/write (update, insert, and delete) permissions on datasets can modify datasets in the version.
1. Click OK to create the new version.

### Administration
Adding new users and roles
We will use 3 “roles” for an enterprise gdb – data viewers, editors, creators, and administrators.
1.	Log in to psql as a user with permissions to create other roles in the database cluster. This can be a login with superuser status or one that has been granted the CREATEROLE privilege.
2.	First, use the CREATE ROLE command to create two login groups: one for users who can edit datasets (editors) and one for users who can only view data (viewers).

```
CREATE ROLE editors
NOSUPERUSER NOCREATEDB NOCREATEROLE NOINHERIT;
CREATE ROLE viewers
NOSUPERUSER NOCREATEDB NOCREATEROLE NOINHERIT;
```

To create a new user, run the “Create Database User” tool as the sde account.

### Questions and discussion:
1.	Roles/permission types and who should have each role

ESRI recommends a database admin (Emily), a geodatabase administrator (Carto and Geo?), data owners (Cartography and Geologic mapping), data editors (students) and data viewers (everyone else?). With the current authentication, we will likely need to send Brett individual IP addresses in order to gain any sort of access to the server. I will also need to provision access files for each user.

What this would look like:
1.	Cartography creates the geodatabase and creates the “Default” version of the database.
2.	Emily adds users and sets permissions on the database.
3.	The data “owner” loads the data into the database and is responsible for maintaining it.
4.	The data owner registers the datasets as versioned.
5.	The geodatabase administrator sets the Default version to “protected,” and then creates a working version called Base to use for edits. Base is set to “public.” All users can view the Default database, but cannot edit it.
6.	Editors will create their own versions from the Base version. Only one person should be editing each version at a time.
7.	The geodatabase administrator will merge changes from other versions back to Base after edits are complete.
8.	Note: There are two operations in sde gdbs related to versioning: Reconciling and Posting. Reconciling involves pulling upstream changes down. For example, if you are editing Base_V1 which you’ve versioned from Base and Base has a change posted to it from another version, you must Reconcile your version with Base to keep up to date. Then, when you are ready to merge Base_V1 into Base, you Post your changes.
9.	Conflicts are more likely to arise if multiple people are editing features that are in close proximity.
10.	Once everything has been reconciled and the versions have been deleted, the database admin compresses the gdb. This doesn’t delete all of the versioning lineage, just cleans up unused files.




Versioning workflows
a.	Clean “Master” copy and working “QA” copy?

12.	Archiving workflows
a.	When to archive/merge versions
b.	When to archive an entire gdb

13.	How this will change project file structures

14.	Test project and collaborators on that project

15.	IT considerations
a.	Looking forward – how many of these do we see hosting at any given time? Size?

Will the database need to be used outside the University? Thinking about authentication here. Most should be able to remote in to a desktop, or use the campus’s generic remote desktop. Is there a case where someone will need to use it on their laptop and will not be able to remote in to a laptop for access? This is pretty much the same use case as nickel – only available on the campus network.