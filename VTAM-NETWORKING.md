

IRMA        : NETWORKING card via SNA

CSM         : the working space of VTAM and created by VTAM.

PU's        : physical unit (_sna component's_) in TCP/ip land its raffle like
              MAC ADDR, IP, etc.

LU's        : Logical unit, application program terminals, console's, printers
              controllers (_router_)

TCP/IP      : has it's own address space and cannot work with out VTAM thus
              VTAM starts it. it has 2 config files one for USS and MVS.

TCAS        : VTAM address space An APPL definition statement defines an
              application program to VTAM. Because TCAS and each TSO user are
              VTAM application programs, you must code APPL definition
              statements for them and put the definition statements in
              SYS1.VTAMLST.

VIPA        : virtual privet address

VTAMLST     :
VTAMLIB     :

PARMLIB(PROGAB) is the member that we define APF authorized Laibrary's.
IKJTSO00    : in SYS1.PARMLIB all APF authorized Laibrary's COMMANDS &
              LOADMADULE's that you want to CALL from TSO.
TSOKEY00 in SYS1.PARMLIB ----> usermax = .... , reconlim = ...
and more important variables
```
TSO PARMLIB    -----> info command.
SENSE 087D0001 -----> no application id in that name
SYS1.PARMLIB
SYS1.VTALST
/d net,id=A06TS001
```
