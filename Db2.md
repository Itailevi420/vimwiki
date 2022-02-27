
#             db2
reference
- installing db2 TODO:ibm url?
- cata
- sysibm.


## [sql](https://github.com/Itailevi420/vimwiki/blob/master/sql.md)


VSDS = is the most important file in a database
        cannot update vsds while db2 is up.


## important cluster-ratio
-    a good ratio >95%

 _the index is always sorted but in time the database can change and_
 _db2 tries to fix it as much as it can. the **clusterratio** tells us how much_
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

