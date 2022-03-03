

                             📇 INDEX :

                         check out colin paice blog

SYSZEN      :
IKJEFT01    : The load module of "TSO"

IPL         : IPL (initial program load) is a mainframe term for the loading of
              the operating system into the computer's main memory .
              A mainframe operating system (such as OS/390) contains many
              megabytes of code that is customized by each installation,
              requiring some time to load the code into the memory.

IML         : IML (_Initial Machine Load_)

RACF        :

SYS1.

3270 data stream

                      ## MAINFRAME OPERATING SYSTEMS:💻
            - z/OS
            - z/TPF
            - z/VM (_Type one hypervisor_)
            - z/VSE (_for smaller companies can run with less personal_)
            - Linux on IBM Z
            - KVM on z (_open source_**Type one hypervisor**_)

LPAR        : Logical Partition

CP          : Central Processor

SAP         : System Assist Processor

IFL         : Integrated Facility for Linux

zIIP        : IBM z Systems Integrated Information Processor for Linux

CHPIDS      : Channel Path Identifiers

PCHID       : Physical Channel ID



RMF         : "Resource Management Facility" Performance Monitoring.

SDSf        : Job Output

JES         : Job Management

spool       : disk's that JES owns and uses.

XMIT        : like ftp but legacy still in wide use
```
--> TSO XMIT

```
and the reciving side need to enter
```
recive ....etc.? some more parametors
```
                ## mainframe emulators 💻
                - Hercules (_open source_)
                - z/pdt (_IBM emulator_)
                -

PR/SM           : Logical to physical mapping

SMP/E           : Software Maintenance "The system modification program"
                  keeps all package dependencies managed something like a
                  package manager on linux.

DF SMS          : "Data Facility Storage Management Service" Automated Disk Mgt
                  Basically manages Storage what data goes where and deals with
                  backups migrations copy's and all I/O management.

HMC             : connected to the SE (_support element_)

WLM             : Workload Managers
                  1. Builds nodes ----->
                  2. Assigns work to nodes ----->
                  3. Measures system <-----
                  4. Unpark/Parks low CP's ----->

Hyper Dispatch  : (_see also HyperSockets_) Helps WLM with response times
                  especially in large systems with lots of cors.
                  So when we virtualize a system like defining an LPAR
                  and there is work to be done the system looks in a pool of
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

Millicode        : A micro architecture a layer that is making it possible to
                  add new functionality and still retaining the full
                  backward compatibility

IRD             : intelligent Resource Director (_IRD_)
                  can manage LPAR clusters and LPAR cpu management
                  - Dynamic Channel Path Management (_DCPM_)
                    FICON channel bandwidth which is primarily used for
                    connections to storage devices

                  - Channel Subsystem Priority Queuing
                    Allows I/O requests in the Channel Subsystem (_CSS_) to
                    have priorities assigned to them

SMF             : "Systems Management Facility" Activity Reporting
                  almost like a database for tracking events.
                  good for diagnosing problems audeting transactions.

USS             : Unix Services

ICKDSF          :

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

S0c7    : translation problems
S0c4    : is worse

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
-
-


to create a new member in a empty LAIBRARY
in ispf


ETL     : the notion of moving data from a mainframe to pc and vise versa
          for development
          _Extract Transfer Load_
