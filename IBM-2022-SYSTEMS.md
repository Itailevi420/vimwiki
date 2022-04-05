

                             📇 INDEX :

                         check out colin paice blog

SYSZEN      :
IKJEFT01    : The load module of "TSO"
DFHSIP      : CICS loadmodule.
```
TSO COMMANDS:
to allocate a logical file <foo> to jes internal reader thus submitting a job.
ALLOC FI(FOO) SYSOUT WRITER(INTRDR)
```
VTAM        : the networking manager of z/OS has 8 char addresses to each
              connection like in the tcp/ip world but with ip addresses.

IPL         : IPL (initial program load) is a mainframe term for the loading of
              the operating system into the computer's main memory .
              A mainframe operating system (such as OS/390) contains many
              megabytes of code that is customized by each installation,
              requiring some time to load the code into the memory.

IML         : IML (_Initial Machine Load_)

RACF        : z/OS security server

segregation = to do something on behalf a different user


SYS1.LINKLIST = usually the utility dataset in the system.

3270 data stream

TCB         : task control block. the OS task (running application) queue.
                      ## MAINFRAME OPERATING SYSTEMS:💻
            - z/OS
            - z/TPF
            - z/VM (_Type one hypervisor_)
            - z/VSE (_for smaller companies can run with less personal_)
            - Linux on IBM Z
            - KVM on z (_open source_**Type one hypervisor**_)

LPAR        : Logical Partition under PR/SM (_prisma_)

CP          : Central Processor

SAP         : System Assist Processor (dedicated to I/O)

IFL         : Integrated Facility for Linux

zIIP        : IBM z Systems Integrated Information Processor for Linux

CHPIDS      : Channel Path Identifiers. channels that go out CSS to I/O devices
HCD         : defines what CHPIDS are managed by the system **not all** CHPIDS
              can be managed

PHCHID      : Physical Channel ID. channels that go in the CSS form system

### ther is 5 different types of address spaces
1. system address space
2. subsystem address space
3. started task program's
4.
5.

### address space blocks:
LPA/LinkList : syslib wher the system looks for loadmodules
               a bunch of modules that helps the system with I/O.
LLA



RMF         : "Resource Management Facility" Performance Monitoring.

SDSf        : Job Output
```
SDSf HELD Output:
COMMAD --> TSO SDSF H
```

JES         : (_Job Entry Subsystem_)Job Management
              accept and queue jobs submitted for execution.
`s jes2,parm='warm,noreq'` ---> start jes2 with operator command `noreq` means
that jes will start and wont ask stuff from the operator

```
jes2 operator commands
to continue with default parms
$S
$D I [(1-2)] --> display status of initiators
$D Initinfo  --> display initialization info
$D J'jobname' --> display job info
$T I(4),class=m --> to change initiator class (t stand for SET)
$P --> stop jes from taking new jobs, but the jobs that are started will still
       finish
d omvs,a=all   -->  to show all unix process
F BPXOINIT,TERM=pid   -->  to terminate a unix process (F means modify)
F BPXOINIT,SHUTDOWN=FORKINIT  --> forkinit means that the unix system
                                  will stop taking process's  F means modify

v xcf,
```


spool       : disk's that JES owns and uses.

XMIT        : like ftp but legacy still in wide use
```
--> TSO XMIT

```
and the receiving side need to enter
```
recive ....etc.? some more parametors
```
## mainframe emulators 💻
- Hercules (_open source_)
- z/pdt (_IBM emulator_) (_1090 PREFIX_)
-

PR/SM           : Logical to physical mapping

SMP/E           : Software Maintenance "The system modification program"
                  keeps all package dependencies managed something like a
                  package manager on linux.

DF SMS          : "Data Facility Storage Management Service" Automated Disk Mgt
                  Basically manages Storage what data goes where and deals with
                  backups migrations copy's and all I/O management.
                  `IDGXX` is an sms prefix


SE              : The support element. every thing that you can do with the
                  HMC you can do with the SE.
                  usually there is 2 in a mainframe.
                  the SE contains :
                  1. LIC (_Licensed Internal Code_) used to control and monitor
                     the CPC
                  2. Loging and problem determination
                  3. hardware system definitions
                  4. IOCDS (_params dataset_)
                     that is used at POR time. (tells the mainframe how
                     to configure all the I/O and the LPAR's)
                  5. BOC (_battery operated clock_) to manage and sync time
                     between all the component's
                  6. Ethernet adapters.

HMC             : (_Hardware Management Console_)
                  usually used to start,stop,.. and manage LPAR's
                  it connects to the SE Support Element
                  1. Can connect to the SE remotely.
                  2. Add multiple mainframes to a single HMC (max 100)
                  3. Add a single mainframe to multiple HMC's (max 32)
                  4. connect to the HMC remotely

WLM             : Workload Managers
                  1. Builds nodes ----->
                  2. Assigns work to nodes ----->
                  3. Measures system <-----
                  4. Unpark/Parks low CP's ----->

Hyper Dispatch  : (_see also HyperSockets_) Helps WLM with response times
                  especially in large systems with lots of cors.
                  So when we virtualize a system like defining an LPAR
                  and there is work to be done, the system looks in a pool of
                  available processors in line of that specific line of work
                  (_zIIp, IFL, SAP etc._)
                  it fined a processor that can handle it and making sure that
                  the same process would go to the same processor so it can
                  use relevant data that is stored in the cache form the
                  previous operation for maximum efficiency.



zDAC            : z Discovery And auto Configuration can help with configuring
                  the HCD (_Hardware and configuration Definition_) helps
                  simplify I/O and some hardware (_mainly FICON_) configuration

VFM             : Virtual Flash Memory
                  helps intensive I/O programs like Db2 and such to minimize and
                  impact by storing the more frequently accessed data thus
                  improving performance

zAWARE          : z Advanced Workload Analysis Reporter. has its own LPAR
                  (_see pic $HOME/Pictures/Ibm-system-map.png ._)
                  it watches every thing going on and compare what it see's to
                  previous data

Millicode       : A micro architecture a layer that is making it possible to
                  add new functionality and still retaining the full
                  backward compatibility

Sysplex         : a way of making multiple systems work as a team. up to 32
                  there is a couple of sysplex's:

                  **monoPlex** : has only one LPAR.

                  **baseSysplex** : All the LPAR's are connected to each other
                     and know of one another.

                  **parallelSysplex** : All the LPAR's are connected to the

                     **Coupling Facility** (_A special LPAR_) typically you would
                     have a backup of this LPAR on another machine/mainframe.
                     the **Coupling Facility** takes care of all the complexity
                     and overhead of the systems working together.
### sysplex component's
                  - **STP** : (_Server Time Protocol_) synchronies time between the
                    systems.
                  - **GRS** : (_Global Resource Serialization_) this allow to
                    multiple systems to access the same resource concurrently
                    serializing when necessary to allow exclusive access.

## Data areas:
```
ASCB     : Address Space Co
PSA      : Prefix in offset 0
WTO/R    : write to the console
```

ENQ      : checks if the resource is available and if it is it locks it for
           updating, editing etc.

DEQ      : the oposite of ENQ it releases the lock to of them is used by GRS.



                  - **XCF** : (_cross Coupling Facility_) this manages communications
                    between applications in a sysplex allows you to issue a
                    command on behalf of another application in the system.
                    This what makes the sysplex communicate as a whole.
                  - **CouplingLinks** : this connect LPAR to processors, **without**
                    these accessing memory on deferent physical systems would
                    have to run through one of those LPAR's.
                    and these allow direct memory access connections between
                    the **sysplex memory and the memory of an attached system.**
                  - **CDS** : (_Coupled Data Set_) contains information related
                    to the parallel sysplex systems.
                    e.g 👇
                    say you are part of a team that needs to do some work on
                    one database, codebase,,,
                    so to make things easy you need to keep a list/ledger
                    so you wont runover someone else's work and vise versa.

CEC             : a physical cage or drawer that holds the processors in the
                  system


IRD             : intelligent Resource Director (_IRD_)
                  can manage LPAR clusters and LPAR cpu management
                  - Dynamic Channel Path Management (_DCPM_)
                    FICON channel bandwidth which is primarily used for
                    connections to storage devices

CSS               - Channel Subsystem Priority Queuing
                    Allows I/O requests in the Channel Subsystem (_CSS_) to
                    have priorities assigned to them
CHPID           :
PCHID
SMF             : "Systems Management Facility" Activity Reporting
                  almost like a database for tracking events.
                  good for diagnosing problems audeting transactions.

USS             : Unix Services
### I/O, Disk & tape config
ICKDSF          : config data sets that defines Labels for disks,tapes,etc.
                  e.g:
                  `VOL=SER=12345`
DSCB            : Data set Control Block
                  in the old days some times to unlock a tape you would ZAP
                  the tape with a ZAP utiliti to go over the bits and to flip
                  the necessary one to unlock the tape.
VTOC            : hase 6 DSCB's usually the fifth DSCB has volume space info.
VVDS            : like vtoc for vsam files

FUZI
MEM?

Screen Scraping :

## NETWORKING
Hyper sockets   : virtual connections that allow you to connect to a z/VM z/OS
                  or Linux systems after you define a virtual connection
                  (_a Hyper socket_ 😉)
                  so you can mix and match to the os it looks just like a
                  networking device for instance :👇
                  ```
                  lets say you define a group of HyperSockets as fallows:
                  HyperSockets "A"
                        has 2 connections
                        - z/OS(1)
                        - z/OS(2)
                  HyperSockets "B"
                        has 3 connections 1 of them is the same machine as "A"
                        HyperSockets
                        - Linux(1)
                        - Linux(2)
                        - z/OS(2)
                  HyperSockets "C"
                        has 6 connections 1 to a z/VM, 3 to the internal os's
                        that is running in the z/VM and another 2 connections
                        - Linux(3)
                        - z/OS(3)
                        - z/VM
                        - Linux#1 (that is in this particular z/VM)
                        - Linux#2(that is in this particular z/VM)
                        - z/OS#1(that is in this particular z/VM)
                  ```
                  _All these systems can now communicate like if their were_
                  _plugged to a super high speed network switch accept it's all_
                  _virtual_

SNA             : LEGACY networking

TCP/IP          : Networking


### Transaction Managers:
        - WebSphere
        - CICS
        - IMS (_Legacy_)


the logon procedure of the user connects hem with all hes files


                        prefixes:
ICH             : Racf
DSN             : Db2
$HASP           : JES
IEDG ?          : SMS





shtelat tavim kryim

EYE CATCHER is a readable piece in your load module that you plant on purpose

## ALL the reg info is IN THE PSW INFORMATION
the last place the app was. is stored in the PSW in the last 4 bytes

reg 1 some data on the loadmodule

error codes
rc are stored in reg 15
rc = 0
rc = 4
rc = 8
system abbend code (_abb normal end_)

ABBEND codes
S0C806-04      : module not found
S0c7           : translation problems and DCB problems
S222           : user problems and sessions?
S0c4           : is worse
S013-14        : usulley DCB problems

BC      : branch conditional

e.g: --> BC 15,106(0,10)

IPCS    : is a loadmodule that helps with finding bugs in dumps

# TODO:🔛
# LEARN ASSEMBLER NOWWWWW!!!!!!

360/ assembly/360 instructions/BC


- --> jcl lab
- --> uss lab
- --> z/OS lab
- RTFM = read the fucking manual

in tapes we dont usulley put PDS, only sequential data sets.
LUN     : is a modern ssd in the mainframe that store datasets that emulates
          DASD, tapes, etc.


console numbers
```
                         check out colin paice blog
<product><xxxx><c>
$HASP1234E

I = Information
E = Error
S = Server Error

this command stops JES and you end up with a console
$PJES2

to see the init and class setup
$D I
```

errors          : d37 = space error usually use compress


ISRDDN          : is an ispf utiliti that show you all the DD cards that is
                  allocated to your USER

## TSO COMMANDS
- lpa     :link list they are always in cache (real memory)
 ac
- link list (lla) laibrary look asaid
- tso del 'dsn'
- tso ALLOC DA(ALLOC.FILE2) DSORG(PS) SPACE(2,0) TRACKS LRECL(80) BLKSIZE(800)
 RECFM(F,B) NEW
-
-
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


ETL     : the notion of moving data from a mainframe to pc and vise versa
          for development
          _Extract Transfer Load_


      ## [JCL](JCL)

      ## [REXX](REXX)

      ## [CICS](CICS)

## OPERATOR COMMANDS
```
/DISPLAY ASM (page DS utilization)
/DISPLAY r,a (reply,all)
/d r,r,cn=(all)   ---> for outstanding reply's
to reply use
/R WTOnumber,response ---> e.g: R 01,response

                               R 1,response
                               R 1,response

/d a     ---> display jobs
/d a,a     ---> display all jobs long list (_IEE115I_)
/d a,l     ---> display jobs short list. jobs under jes
/d u  ---> display UCB's (unit control block)
/d u,,,unitAddressNum   to display ---> /d u,,,1001,1
/d u,iplvol  ---> display the IPL disk
/d iplinfo   ---> like what parmlib it uses etc.
/d u,vol=rsm009
/d m  ---> (matrix=...) display UCB's (unit control block) UCW's CSS.
/d m=dev(unitAddressNum)   ---> display status and number of online paths for all devices
/d m=chp()    ---> channel path info
/d m=cpu      ---> info abuot cors(smt  multi threaded operation)
/d m=config(member-suffix) --->
/d m=core

jes2 operator commands
to continue with default parms
$S
$D I [(1-2)] --> display status of initiators
$D Initinfo  --> display initialization info
$D J'jobname' --> display job info
$T I(4),class=m --> to change initiator class (t stand for SET)
$P --> stop jes from taking new jobs, but the jobs that are started will still
       finish
d omvs,a=all   -->  to show all unix process
F BPXOINIT,TERM=pid   -->  to terminate a unix process (F means modify)
F BPXOINIT,SHUTDOWN=FORKINIT  --> forkinit means that the unix system
                                  will stop taking process's  F means modify

v xcf,
```

multi line WTO   - when a command write's to the console usually each line ends
with 210 address space.
sys1.uans? to set in racf some config

Dinamic Address translation   =  the component that translats virtual storage
                                 to real storage
