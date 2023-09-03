

                             📇 INDEX :

                         check out colin paice blog

IOCDS       : the disk parametor file. in Hercules its the tk4-.cnf
ADRDSSU     : Important application that helps to manage datasets
SYSZEN      :
IKJEFT01    : The load module of "TSO"
DFHSIP      : CICS loadmodule.
HASJES20    : Jes2 loadmodule.
ISTES01     : VTAM loadmodule.
SYSRES      : the IPL disk to start MVS. in Hercules its calld MVSRES in IOCDS
HSA         : The name of the REAL MEMORY buffer that is used for the disks
              and other devices that is configured in IOCDS.

```
TSO COMMANDS:

to allocate a logical file <foo> to jes internal reader thus submitting a job.
ALLOC FI(FOO) SYSOUT WRITER(INTRDR)

TSO HOMETEST  ---> shows the ip address of the LPAR your in
```
VTAM        : the networking manager of z/OS has 8 char addresses to each
              connection like in the tcp/ip world but with ip addresses.

IPL         : IPL (initial program load) is a mainframe term for the loading of
              the operating system into the computer's main memory .
              A mainframe operating system (such as OS/390) contains many
              megabytes of code that is customized by each installation,
              requiring some time to load the code into the memory.
              taks params from the SYSRES, in Hercules called MVSRES
IODF        : Software I/O config like the IOCDS but for the OS so he know's
              what devices are configured

              ```
   IPL-Parameter -----> 07B000M1    ⤵
    LOADPARM
              IODF unit    |  LOADxx  | IMSI | Alt' nucliues |
                1-4        |  5-6     |  7   |     8         |
              ```

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
            - KVM on z (_open source_ **Type one hypervisor**)

LPAR        : Logical Partition under PR/SM (_prisma_)

CP          : Central Processor

SAP         : System Assist Processor (dedicated to I/O)

IFL         : Integrated Facility for Linux

ICF         : Integrated Coupling Facility

zIIP        : IBM z Systems Integrated Information Processor for Linux

CHPIDS      : Channel Path Identifiers. channels that go out CSS to I/O devices

HCD         : difines the OS configuration and proccesor configuration as well.
              defines what CHPIDS are managed by the system **not all** CHPIDS
              can be managed

PHCHID      : Physical Channel ID. channels that go in the CSS form system

## the first address space is called MASTER "SCHEDULER"
### ther is 5 different types of address spaces
1. system address space
2. subsystem address space
3. started task program's  __every started task need's to be in
   SYS1.PROCLIB(task_name).
4.
5.

### address space blocks:
LPA/LinkList : syslib where the system looks for loadmodules
               a bunch of modules that helps the system with I/O.
LLA



RMF         : "Resource Management Facility" Performance Monitoring.

SDSf        : Job Output
```
SDSf HELD Output:
COMMAD --> TSO SDSF H
PARM   --> shows the parametors Data sets
```

JES         : (_Job Entry Subsystem_)Job Management
              accept and queue jobs submitted for execution.
`s jes2,parm='warm,noreq'` ---> start jes2 with operator command `noreq` means
that jes will start and wont ask stuff from the operator



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

DFSMS           : "Data Facility Storage Management Service" Automated Disk Mgt
                  Basically manages Storage what data goes where and deals with
                  backups migrations copy's and all I/O management.
                  `IDGXX` is an sms prefix
DFSMShsm        : makes it easy to get the datasets that are archived .


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

WLM             : Workload Managers the IRD extends wlm to handle sysplex loads
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
VVDS            : vsam volume dataset    like vtoc for vsam files
                  so if you have vsam datasets on dasd you need to have VVDS
                  beside the vtoc so you can find the datasets

                  vvr,nvr SYS1.VVDS.Vxxxx
ICKDSF            TO initialize a new dasd makes the vtoc.

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

APPC            : Application Peer to Peer connection (_USES SNA_)

TCP/IP          : Networking


ZOSMF       : a front end app written in Java for the mainfraim to do the job
              of SMP/E. (package manager)

OSA         : Network card in the mianfraim

HZS         : Health checker prefix code

HZSPROC     : Health checker default jobname


//TM0TCP PGM=EZBTCPIP
profile
systcpd

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






EYE CATCHER is a readable piece in your load module that you plant on purpose

## ALL the reg info is IN THE PSW INFORMATION
the last place the app was. is stored in the PSW in the last 4 bytes

DAT            : DAT is a component that translate between logical and physical
                 memory.

reg 1 some data on the loadmodule

error codes
rc are stored in reg 15
rc = 0
rc = 4
rc = 8
system abbend code (_abb normal end_)

ABEND codes
S0C806-04      : module not found
S0c7           : translation problems and DCB problems
S222           : user problems and sessions?
S0c4           :
        Abend is a protection exception when a virtual address cannot be mapped
                 with a physical address. When S0C4 Abend occurs. An Invalid
                 address referenced due to subscript error. In a group Move the
                 length of the receiving field was defined incorrectly.
S013-14        : usually DCB problems

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


-
-

ISRDDN          : is an ispf utiliti that show you all the DD cards that is
                  allocated to your USER

## TSO COMMANDS
- lpa     :link list they are always in cache (real memory)
 ac
- link list (lla) laibrary look asaid
- tso del 'dsn'
- tso ALLOC DA(ALLOC.FILE2) DSORG(PS) SPACE(2,0) TRACKS LRECL(80) BLKSIZE(800)
 RECFM(F,B) NEW


ETL     : the notion of moving data from a mainframe to pc and vise versa
          for development
          _Extract Transfer Load_

## file types
### [DATASETS](DATASETS) : DFSMS

## [JCL](JCL)

## [REXX](REXX)

## [CICS](CICS)

## [OPERATOR COMMANDS](OPERATOR-COMMANDS)

## [VTAM NETWORKING](VTAM-NETWORKING)

### SMP/E the z/OS package manager
smp/e zones:


GLOBAL        : This dataset holds info abuot the state of the installation
                process.
CSI           : GLOBAL zone, Dzone, Tzone

Dzone         : a Vsam ds that records all the changes in DLIB pds.

DLIB          : Distrubution Laibrary, a PDS that holds the source code objects
                of the new updates. when you ACCEPT the updates from PTS it
                over rides the existing source code in DLIB.
                **DLIB's elements**:


SYSGEN        : Generates new target laibrary from the DLIB's elements.


TARGETzone    : a Vsam (_KSDS_) ds that records all the changes in TARGETlib pds

TARGETlib     : a PDS ds that you APPLY the new updates from PTS.

MCS           : Modification Control Statments

PTS           : Temporary Storage, a PDS dataset that holds all the update
                requests & code fixes or patches.

GLOBALzone    : Holds the SMPPTS & pointers to the targetLib & its zone, distroZone's

SMPPTS        : holds all the sysmods. (_system modification's_)

CSI           : a name for all the zones as a whole, can implement
                CSI with more then one file. type: vsam _KSDS_

SYSMOD        : paches or fixes that is uploaded to the PTS
smp/e sysmod's element packaging:

    1. APAR        : small fixes & Zapping modules. (_modules fixes usulley_)
    2. PTF         : Preventing service
    3. FUNCTION    : a service or a application.
    4. USERMOD     : if you want to package your app that you builde.


IEWL          : Binder & linkige editor. it's an alias for `IEWBLINK`
                every


SMP/E COMMANDS:

- SET `SET BOUNDARY(GLOBAL) .`

SVC           :Storage Area Network (SAN) volume controller (SVC) usage
               is a module that has autherization to do stuff in the OS





