# quickpostgresdb

Instructions for loading data into an AWS postgreSQL database and how to access that data.  

Non-confidential data only.

Steps:  
1. Launch server
2. Access server
3. Import data

## Launch server

### Amazon AWS - RDS

Settings default unless specified.

Engine:  
postgres

Production:  
Dev/Test

Specify DB Details:  
DB Instance Class: db.t2.micro - 1 vCPU, 1 GiB RAM  
Multi-AZ Deployment: No  
Allocated Storage: 5 GB  
DB Instance Identifier: instanceid01  
Master Username: masteru  
Master Password: masterpass  

Advanged Settings:  
Database Name: dbname01

### Prices

US East (N Virginia)  
db.t2.micro  
single-AZ deployment  
$0.018 per hour  
$3.024 per week  
$12.96 per month  

Plus  
$0.09 per GB data transfer out via internet




## Connecting to the database



### From AWS console

Make note of server locatoin:  
instanceid01.cxxxxxxxxxxi.us-west-2.rds.amazonaws.com:5432 


### pgAdmin

https://www.pgadmin.org/

Add a new connection

Name: awsrds01  
Host: instanceid01.cxxxxxxxxxxi.us-west-2.rds.amazonaws.com  
Port: 5432  
Service: dbname01  
Username: masteru  
Password: masterpass  


See a list of current tables:  
Databases > dbname01 > Schemas > public > Tables 



## Loading data


Create your table

```sql
CREATE TABLE table01_staging (

 col1_int VARCHAR(50)
,col2_varchar VARCHAR(50)
,col3_date VARCHAR(50)

);
```


### Option 1 - pgAdmin GUI

Data Location: Local computer e.g. your laptop  
Data Size: Small  

In pgAdmin's Object browser, navigate to table:  
Databases > dbname01 > Schemas > public > Tables > table01_staging  

Right click > Import  
Follow GUI instructions


### Option 2 - python script

Data Location: Local computer e.g. your laptop  
Data Size: Larger  

... TBC

### Option 3 - 

Data Location: AWS (EC2 or S3 etc)  
Data Size: Larger  

... TBC




