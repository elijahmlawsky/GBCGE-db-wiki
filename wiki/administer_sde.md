---
title: Administering Enterprise Geodatabases
permalink: "/:basename"
layout: git-wiki-default
---

### Adding new users and roles
We will use 3 “roles” for an enterprise gdb – gis (faculty/staff), editors, and viewers
1.	Log in to psql as a user with permissions to create other roles in the database cluster. This can be a login with superuser status or one that has been granted the CREATEROLE privilege.
2.	First, use the CREATE ROLE command to create two login groups: one for users who can edit datasets (editors) and one for users who can only view data (viewers).

```
CREATE ROLE editors
NOSUPERUSER NOCREATEDB NOCREATEROLE NOINHERIT;
CREATE ROLE viewers
NOSUPERUSER NOCREATEDB NOCREATEROLE NOINHERIT;
```

To create a new user, run the “Create Database User” tool as the sde account.