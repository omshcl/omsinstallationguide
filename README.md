# IBM Sterling OMS Installation guide Windows 10

# db2 connection
CREATE DATABASE OMDB

CONNECT TO OMDB

CREATE BUFFERPOOL ICMLBUFFER32 PAGESIZE 32k
CREATE BUFFERPOOL ICMLBUFFER16 PAGESIZE 16k
CREATE BUFFERPOOL ICMLBUFFER8 PAGESIZE 8k
CREATE BUFFERPOOL ICMLBUFFER4 PAGESIZE 4k

CREATE SYSTEM TEMPORARY TABLESPACE ICMLSSYSTSPACE32 PAGESIZE 32k BUFFERPOOL ICMLBUFFER32
CREATE SYSTEM TEMPORARY TABLESPACE ICMLSSYSTSPACE16 PAGESIZE 16k BUFFERPOOL ICMLBUFFER16
CREATE SYSTEM TEMPORARY TABLESPACE ICMLSSYSTSPACE8  PAGESIZE  8k BUFFERPOOL ICMLBUFFER8
CREATE SYSTEM TEMPORARY TABLESPACE ICMLSSYSTSPACE4  PAGESIZE  4k BUFFERPOOL ICMLBUFFER4


## download db2jcc4 jar
https://jar-download.com/?search_box=db2jcc4


## Oms installation arguments

Database Vendor

    DB2
Database user name

    alice

Database password
 
    acoount password


Database Catalog name

    OMDB


Hostname

    localhost

port number

    50000

schema name

    ALICE

jar
 
    path to the downloaded jar

Additional ant arguments
 
    -XX:MaxPermSize=768m
    
    -J-Xms1408m -J-Xmx1752m
# build ear file

# install war

 
    https://localhost:9043/ibm/console

Applications  
Application Typees  
Websphere Enterpis applicatin  
Install  
Click smcfs.ear

Fast Path


Select all the jars and war files

## Configure JDB Deploy heap size parameter
Type "Edit the System Environment variables into the search console
Click Environment variables
Make a new System Variable
Variable name:
 
    EJBDEPLOY_JVM_HEAP    
    
Variable Value:
 
    -Xms2048m -Xmx18000m

apply and save
## Configure db2 connection  for installed oms application
localhost:9060/ibm/console/login.do
Servers-> WebSphere application servers -> server1 -> Java and  -> Process Definition -> Java Virtual Machine
Under Generic JVM arguments enter
 
    -Dvendor=shell -DvendorFile=/servers.properties -Dsci.naming.provider.url=corbaloc::localhost:2809
