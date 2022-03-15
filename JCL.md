
jcl



`SPACE=(UOM,(P,S,D),RLSE,?CONTIGUS?)`

```jcl
//cond=(0,NE)
//* need to read left to right if false it does the step. if true it
//* skips the steps. and can do with more conditions
//cond=((o,NE),(...),(...))
//* it like an 'or' '||' statement

TYPERUN=SCAN/HOLD
```


BPXBATCH       : utiliti that can send commands to UNIX/USS in jcl

IDCAMS         : VERY important utiliti
                 to work with VSAM ds's.


DCB            : Data Control Block. e.g:
this means 100 records of 80 bytes each in every I/O
`LRECL=80,RECFM=FB,BLKSIZE=8000`


this means 3 records of 200 bytes each in every I/O + **4 more bytes** for
record data, hence `BLKSIZE=604`
`LRECL=200,RECFM=VB,BLKSIZE=604`

this means 1 record of 200 bytes in every I/O + **4 more bytes** for
record data, hence `BLKSIZE=204`
`LRECL=200,RECFM=V,BLKSIZE=204`


DCB= Data Control Block
DCB=(LRECL=80,RECFM=FB,.....
BLKSIZE=  size of I/O block size
LRECL = 80RECFM=
   V     variable
   F     Fixed
   U     Undefined ( Load modules)    LM
   FB   Fixed,Blocked
   VB   Variable,Blocked


   +A   (FBA)   =   + 1 byte at the beginning with an ASA code (printer Control chars)


```jcl
//S1   EXEC PGM=FFILE       F WORD
//KKK DD DISP=OLD,DSN=A.B.C                     LRECL=84,RECFM=VB,BLKSIZE=0

in this example the file in the jcl has a  `LRECL=84,RECFM=VB,BLKSIZE=0`
and in the program below that's using the file you can see that it opens the
file with different DCB's 👇
FFILE
----------
  FD  KKK       LRECL=45,RECFM=F
  OPEN KKK
     WRITE "DFSDFSDF",KKK
  CLOSE KKK

 need to beware of opening a file with different DCB options it will corrupt
 the file.
 ```
  AM = Access Method  - Class  (data,functionality)
BPAM , QSAM , BSAM     - PS
VSAM:           CI (records) , CA
    - ESDS    Entery Sequential
    - KSDS    Key Sequentail
    - RRDS    Relative   --  Direct
    - LDS     Linear     4k, 4k 4k 4k 4k 4k         ( Div)


SMS
this are definitions that the sysadmin makes to manage and order all the
aspects of the system behaver
    DC   data class
    SC   storage class
    MC   managment class
    SG
    ACS - Autamtic Class Selection
    an ACS rutine is a automated definitions to a

CSECT       : the smallest operational part of a loadmodule
ADRDRSU     :
