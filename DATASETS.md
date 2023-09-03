
## VSAM FILES:
  AM = Access Method  - Class  (data,functionality)
BPAM , QSAM , BSAM     - PS
VSAM:           CI (records) , CA  it allows to work on part of a file on a
                record level so the file is not locked for writing and reading.
    - ESDS    Entery Sequential
    - KSDS    Key Sequentail
    - RRDS    Relative   --  Direct
    - LDS     Linear     4k, 4k 4k 4k 4k 4k         ( Div)

to create a new member in a empty LAIBRARY
in ispf


## VSAM data sets are briefly described as follows:

Key Sequence Data Set (KSDS)
This type is the most common use for VSAM. Each record has one or more key
fields and a record can be retrieved (or inserted) by key value.
This provides random access to data. Records are of variable length.
IMS™ uses KDSDs.

Entry Sequence Data Set (ESDS)
This form of VSAM keeps records in sequential order. Records can be accessed
sequentially. It is used by IMS, DB2®, and z/OS® UNIX®.

Relative Record Data Set (RRDS)
This VSAM format allows retrieval of records by number; record 1, record 2, and
so forth. This provides random access and assumes the application program has a
way to derive the desired record numbers.

Linear Data Set (LDS)
This type is, in effect, a byte-stream data set and is the only form of a
byte-stream data set in traditional z/OS files (as opposed to z/OS UNIX files).
DB2 and a number of z/OS system functions use this format heavily, but it is
rarely used by application programs.



DFDSS       : DFSMSdss data set services (_Data mover & copier_)

DFSMShsm    : Hierarchical storage manager usually manages migrated archived
              DS's uses hierarchical

DFSMSrmm    : Removable media manager. Tape volume and dataset management.

DFSMStvs    : transactional VSAM services.

IGDnnnX  is usually the prefix of DFSMS.

LOADxx      : is the load parameters . can see it via SDSF command --> system
              and the second way is via parmLib OPERATOR command --> iplinfo

ACS Routine   : for every DC, MC, SC, SG there is a routine like :
                if dsn = something then do this or that.
                for every class you define a ACS Routine.

ASCDS      : Active configuration of SMS.

SSCDS      : the place to add new configuration before Activation.

storageClass == SC  must be for every sms managed DS.

DC ACS --> SC ACS  SC=NULL --> non managed.
                 |
                  SC = XXX --> managed.  --> MC ACS --> SG ACS.

vvds      : a catalog for VSAM ds.

`/d xcf,blaaaa`
```
d sms
load (source) this scds/acds ds with out restarting sms
SETSMS SCDS DSN =
SETSMS ACDS DSN =
SET SMS=XX
display
d sms,sg(sgroup_name),listvol
ds sms,d83,10 <--- number of devices to show
      |👇 |
      |address of the device|
```
Storage class   :  f/


