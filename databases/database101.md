
# Databases

## rds - OLTP

* relational database : tables, rows, fields

* database types :
- oracle
- microsoft sql
- postgresql
- mysql
- aurora
- marioDB


## dynamodb

* managed no sql database

- collection = table
- document = row
- key value pairs = field

* json/nosql

## Elastic Cache

* In-memory cache
Is a web serivce that makes it easy to deploy, operate, and scale an in-memory cache in the cloud. The service improves
the performance of web applications by allowing you to retrieve information from fast, managed, in-memory caches,
instead of relying entirely on slower disk-based databases

* 2 Open sources:

- Memcached
- Redis

## Redshift - OLAP 

* Fast, Simple, Cost-Effective Data warehousing

## DMS

* Managed database migration service
- managed data type transformation
- compression
- parallel transfer ( for faster data transfer)
>> Ensure that data changes to the source database that occur during the migration process are automatically
replicated to the target

* AWS schema conversion tool automatically converts the source database schema and a majority of the custome code:
views, stored procedures, and functions, to a format compatible with the target database

## Data Warehousing

* Used for business intelligence. Tools like Cognos, Jaspersoft, SQL Server Reporting Services, Oracle Hyperion, SAP NetWeaver

* Used to pull in very large and complex data sets. Usually used by management to do queries on data ( such as current performance vs targets etc)

## OLTP vs OLAP :

* Online Transaction Processing (OLTP) differs from Online Analytics Processing (OLAP) in terms of the types of queries run

* OLTP examples:

Order number 2120121
pulls up a row of data such as Name, Date, Address to Deliver to, Delivery Status etc.

* OLAP transaction examples:

Net Profit for EMEA and Pacific for the Digital Radio Product.
Pulls in large numbers of records

Sum of Raidos Sold in EMEA
Sum of Radios Sold in Pacific
Unit Cost of Radio in each region
Sales price of each radio
Sales price - unit cost

Data Warehousing databases use different type of architecture both from a database perspective and infrastructure layer
