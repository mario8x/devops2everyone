

## Restore from Microsoft SQL Server Management Studio

* Steps

right click on the Databases container within object explorer.
from context menu select Restore database.
Specify To Database as either a new or existing database.
Specify Source for restore as from device.
Select Backup media as File.
Click the Add button and browse to the location of the BAK file.

## How to make remote connectcion

* Configure `security group` to allow inbound TCP 1433

* Server configure: sample-instance.cg034hpkmmjt.us-east-1.rds.amazonaws.com,1433

*

## Restore db from local source to aws destination
* download db migration tool: https://sqlazuremw.codeplex.com/

* run the tool above

* select migrate sql

* select db and local source

* select db and destination aws

* run migration application.