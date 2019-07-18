# IBM Sterling OMS Installation guide Windows 10
- [Install Guide](#Install-guide)
- [Errors](#Errors)
- [Debugging](#Debugging)

# Install guide
## db2 connection
 
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

## Download OMS


Oms Enterprise Edition V10.0
Fixpack 

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
Navigate to C:\IBM\bin
 
    buildear.cmd -Dsupport.multi.war=true -Dappserver=websphere -Dwarfiles=smcfs,sbc,sic,sma -Dearfile=smcfs.ear -Ddevmode=true -Dnowebservice=true -Dnodocear=false create-ear

# install web sphere application server
Download
 
    IBM WebSphere Application Server Version 9.0.0.0
    IBM SDK, Java Technology Edition, Version 8 Version 8.0.5.35
 
## create a profile
Open Profile management tool and create a new user
Start the server through the start menu

## Configure JDB Deploy heap size parameter
Type "Edit the System Environment variables into the search console
Click Environment variables
Make a new System Variable
Variable name:
 
    EJBDEPLOY_JVM_HEAP    
    
Variable Value:
 
    -Xms2048m -Xmx18000m
apply and save
## install war

 
    https://localhost:9043/ibm/console

Applications  
Application Typees  
Websphere Enterpis applicatin  
Install  
Click smcfs.ear

Fast Path

Select all the jars and war files
finish
## Configure db2 connection  for installed oms application
localhost:9060/ibm/console/login.do
Servers-> WebSphere application servers -> server1 -> Java and  -> Process Definition -> Java Virtual Machine
Under Generic JVM arguments enter
 
    -Dvendor=shell -DvendorFile=/servers.properties -Dsci.naming.provider.url=corbaloc::localhost:2809


# Install sterling ICSS
IBM Sterling CallCenter Installer
## install fixpack
IBM sterling ISCCS FixPack Installer 

# Errors
## JDEploy out of heap memory error
ensure JVM  [EJBDEPLOY_JVM_HEAP](#Configure-JDB-Deploy-heap-size-parameter)  is set as a system variable
# Debugging

## DB2
check that you can acess the OMDB database using Oracle Sql Developer
