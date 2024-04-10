---
layout: default
permalink: /documentation/database/
---
# General usage and file structure of Database
The database repository has the following structure:

```
./
├── data/                      # Database sample SQL files
│  ├── sample/
│  │   └── xx.data-init.sql    # Data SQL files to execute in order to create a sample database data with all required information
│  └── _creationg_script.sql   # Main script to create an empty database, used primary for the automated testing
├── <database>/                # Database specific engine SQL files, create one folder for each database engine supported
│  ├── _history.sql            # Script that need to be executed when downloading new changes.
│  ├── 01.tables.sq            # Script that will create only the tables with their definition (no PK, neither FK)
│  ├── 02.pks.sql              # Script that will alter all required tables to add the PK definitions
│  ├── 03.fks.sql              # Script that will alter all required tables to add the FKs definitions
│  ├── 04.indexs.sql           # Script that will alter tables / create index in order to improve the performance of the database
│  └── 05.views.sql            # Script that will create all the required views of the solution

```

The files required for the database creation are splited in order to avoid dependency errors in the sequence execution. By having the actions splited in multiples files, and executing those files in the correct order, we can garantee that script will have the required elements for the correct execution.

Main rules used to create the names of the database elements:

- Direct related tables use start with the name of the parent
- Columns that are SERIAL will always end with _auto
- FK to _auto columns will not contain the _auto postfix
- View's names will always start with vw_ in order to avoid confusion with tables
- FK's names will contain the name of the table follow by the name of the parent table
- Index's names will contain the name of the table and a sequence number
- Use 3 letters abreviation when possible to avoid long names (except for the last word)

If new files are required, the GitHub main action need to be updated in order to execute the new added files.