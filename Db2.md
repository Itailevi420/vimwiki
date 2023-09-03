
#             db2
reference
- installing db2 TODO:ibm url?
- cata
- sysibm.


## [sql](sql)

When we CREATE a TABLESPACE the catalog gets a new line, and adds the directory
a new Entry for that new TABLESPACE.

DSNDB01      : DB2 directory

DSNDB06      : DB2 catalog

BSDS/VSDS = BootStrapDataSet is the most important file in a database
            cannot update vsds while db2 is up.
LDS       = (_Linear dataset_)a Vsam dataset that DB2 uses to store file's

## db2 JCL job and subsystem start.
DSNDB* in sdsf to see db2 job's usauly
1. DSNDMSTR
2. DSNDIRLM     Locking Manager.
3. DSNDDBM1       db2 Buffer pool residence


### Table Space
* storage area for one or more tables.
* Maps to one or more Vsam data sets.
* The data set is divided into pages.
* Can be:
    - Simple
    - Segmented
    - Partitioned
    - Universal:
        * Partition by Growth (_MAXPARTS_)
        * Partition by Range  (_NUMPARTS_)


DSNDB01     : SYSUTIL table, TODO
DSNDB01
DSNDB06
DSNDB07


## important cluster-ratio
-    a good ratio >95%

 _the index is always sorted but in time the database can change and_
 db2 tries to fix it as much as it can. the **clusterratio** tells us how much
 _the database columns differ from the index_
 _every index has it's own **clusterratio** and only 1 of them can have a_
 _clusterratio of >95%_

- RUNSTATS =
- index page split = is very expensive CPU and I/O wise

PCTFREE = DEFINES
FREEPAGE = DEFINES


## MANAGING DATA WITH DB2 UTILITIES

- **DSNZPARAM**
- set sysparm

## DB2 UTILITIES
- data backup & recovery utilities
    - COPY
    - COPYTOCOPY
    - MERGECOPY
    - QUIESCE
    - RECOVER
    - REBUILD

### load
load resume
load replace : deletes tables very dangers
- share level = how well you play with others
    - SHRLEVEL = NONE ; don't play with nobody
    - SHRLEVEL REFERENCE  LIKE RO
    - SHRLEVEL CHANGED enables RW

    0. init
    1. unload
    2. sort
    3. reload
    4. rebuild
    5. log
    6. switch --> outage
    7. utilterm

ERD      : Entities rlationship

HOW DOES DATA IN REALITY TRANSLATES TO A DATABASE

- Reality
- Data
- Metadata

##          NORMALIZATION OF DATA



- columns considerations


SYSADM   =  DB2 administrator
install sysadmin =  a species user that have permissions to install DB2 systems


RACF profiles for db2 security MDSNTB MDSNDB etc.


DB2 concorence

every applacation needs permissoin to accesse a DB
- claim
- lock

Installation:
NUMLKTS:
NUMLKUS:

DBA:
usuely you want to define "locksize = page"

SLOCK:
ULOCK:


RVA : is the address in the log
monitering lock
            LOCKINFO


MIAPU   : a program that define's


    ## Parallel Sysplex

### Coupling Facility structure's

* Lock structure      :
* List structure  (_SCA_)
* Cache structure (_GBP's_) Group Buffer Pool

when installing db2 the output pramator member usuely to the next letter
xxxxxb but if you use SAP then you cant use xxxxxb so xxxxxc......


IRLM        : Internal Resource Lock Manager
              if using default values the start Procedure is called **IRLMPROC**

 db2 **DSNTINST** installation clist
