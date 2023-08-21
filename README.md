# MySQL Database Interface for VeighNa Framework

<p align="center">
  <img src ="https://vnpy.oss-cn-shanghai.aliyuncs.com/vnpy-logo.png"/>
</p>

<p align="center">
    <img src ="https://img.shields.io/badge/version-1.0.4-blueviolet.svg"/>
    <img src ="https://img.shields.io/badge/platform-windows|linux|macos-yellow.svg"/>
    <img src ="https://img.shields.io/badge/python-3.7|3.8|3.9|3.10-blue.svg" />
</p>

## Description

MySQL database interface based on peewee development.

## Use

### Global Configuration

When using MySQL in VeighNa, you need to fill in the following field information in the global configuration:

|name|meaning|required|example|
|---------|----|---|---|
|database.name|Name|Yes|mysql|
|database.host|Address|Yes|localhost
|database.port|Port|Yes|3306
|database.database|Instance|Yes|vnpy
|database.user|Username|Yes|root
|database.password|Password|Yes|123456

### Create instance (Schema)

VeighNa does not actively create instances of MySQL databases, so please make sure that the instance of the database filled in the database.database field has been created before using it.

If the instance has not been created, you can use [new_schema] in the MySQL Workbench client.


### String case-sensitivity support

Due to the limitation of peewee's table building function, by default, the [symbol] field of the contract code is not case-sensitive when it is saved. If it affects the usage, you can fix it by manually modifying the MySQL data table as follows:

```sql
# Connect to the database with the MySQL command line tool

# Select the data instance
use vnpy;

# Modify the BINARY attribute of the SYMBOL field of the four tables
ALTER TABLE `dbbaroverview` MODIFY COLUMN `symbol` VARCHAR(45) BINARY;

ALTER TABLE `dbtickoverview` MODIFY COLUMN `symbol` VARCHAR(45) BINARY;

ALTER TABLE `dbbardata` MODIFY COLUMN `symbol` VARCHAR(45) BINARY;

ALTER TABLE `dbtickdata` MODIFY COLUMN `symbol` VARCHAR(45) BINARY;
```
