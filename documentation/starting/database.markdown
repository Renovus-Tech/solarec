---
layout: default
permalink: /documentation/starting/database
---
# Getting started with Solarec Database

Currently the only database engine supported is **PostgreSQL 15**, how ever the project can be implemented in other engines.

In order to support another engine, the following steps need be to done:

- Create a folder for the database engine
- Create the following files in the format and with the data types supporte by the engine
  - 01.tables.sql: only include the tables definition (do not include PK neither FK neither indexes)
  - 02.pks.sql: include the required SQLs to alter the tables and define the primary key
  - 03.fks.sql: include the required SQLs to alter the tables and define the corresponding foreign keys
  - 04.indexs.sql: include the required SQLs to define the required indexes
  - 05.views.sql: include the SQLs for the views used by the system

Take in consideration that in order to create the database, a user will execute the files in the corresponding order.

## Sample data
In order to use the solution with sample data, the following files can be used to populate the database:
- 10.data-init.sql: contains the basic data required to have a Solarec installation up and running, but without clients
- 11.data.canary.sql: contains the SQLs that need to be executed to create a client call **Canary**, ones the data is in the database, you are good to login.

The files are stored at: **data / sample**.