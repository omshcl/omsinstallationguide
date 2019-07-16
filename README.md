# IBM Sterling OMS Installation guide Windows 10

## download db2jcc4 jar
https://jar-download.com/?search_box=db2jcc4

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

# installation arguments

-XX:MaxPermSize=768m
-J-Xms1408m -J-Xmx1752mS

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
