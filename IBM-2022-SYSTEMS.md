

                             📇 INDEX :

                         check out colin paice blog

IKJEFT01    : The load module of "TSO"

IPL         : IPL (initial program load) is a mainframe term for the loading of
              the operating system into the computer's main memory .
              A mainframe operating system (such as OS/390) contains many
              megabytes of code that is customized by each installation,
              requiring some time to load the code into the memory.

SAS/IML     : SAS/IML is an interactive matrix language that is both powerful
              and flexible. The fundamental data object on which all commands
              operate is a row by column matrix. Therefore, single elementwise
              operators such as + and / can operate on many data values to
              produce many results

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

SMP/E           : Software Maintenance "The system modification program"
                  keeps all package dependencies managed something like a
                  package manager on linux.

DF SMS          : "Data Facility Storage Management Service" Automated Disk Mgt
                  Basically manages Storage what data goes where and deals with
                  backups migrations copy's and all I/O management.

WLM/IRD         : Workload Managers

SNA             : LEGACY networking
TCP/IP          : Networking

SMF             : "Systems Management Facility" Activity Reporting
                  almost like a database for tracking events.
                  good for diagnosing problems audeting transactions.

USS             : Unix Services

ICKDSF          :

Screen Scraping         :

Transaction Managers:
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
