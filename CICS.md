
##    cics the online server.
DFHSIP    = CICS loadmodule.
DFHRPL    = A dd card to find cics task modules.
DFHCSD    = A dd card that holds the CICS config.
            like steplib.
SIT       = (_System initialization table_) is connected to cics job sysin DD
costomer information control servies.

unit of work = like where to return in the unit of work time line of the
               transaction's life. (roll back,commit etc.)
- TPS     =    transaction per second
- TCA     =   for every task a TCA is created for that task's life.
              up to 2000 task's simultainslly
- TRANSACTION = could have only 4 char name
                for every task there is a TCA (_task control area_) and it
                contains pointers for the task in hand.
- TIOA     = TERMINAL I/O erea lives in the TCA
- After the TCA the PCA programe control area
- TDQUEUE  = (_transiat data queue_) can use to triger stuff on the record
                level. eg: every 5 record's print...
                her is Extra partition and Intra partition.
                the Extra writes or reads to a dd card.
                and Intra writes or reads from the cics memory
- Indirect redirect to extra
            
  Axilury/Main :
               Axi means that the tsqueue (_temporary storage queue_)
               is writen to a dataset. (like EXTRA)
               Main means that it is writing to the cics memory. (like INTRA)
               
-  Ati  atomatic transaction initiation t
- CEOT    = To look a you as a user.
(_in hebrew "look at me."_)
- cemt    = to look at the state of the CICS system.
```
/*  CAN SEE INFORMATION AND CHANGE SOME
/* to connect to CICS you need a terminal so to se the terminal's connect :
CEMT I TERMINAL
CEMT I FILE(FIL*)   ==> to find files that start with the char's "FIL"and to disable
CEMT I TRANS( AMNU ) ==>  to see if a transaction is defined.and to disable
CEMT I PROG( DFH$AMNU ) ==>  to see if a Program is defined. and to disable

CEDA
c as(tran_name) to(group)
```
- CEDF    = TO debugg transactions online. it checks where in the program
            the `EXEC CICS` is embedded and stops ther.
- CEDA    = allows to define in the RDO (_resource definition online_).
- SIT     = (_System initialization table_) is connected to cics job sysin DD
-
- SEMT & SEMA very strong transactions

-
- CESF    =
-
- CMAC    = a error code and abend lookup and reference
-
- CECI    = Is a command interpreter transaction than allow programers to test
            there EXEC CICS.
- UPILnks = is the stream catch of tn3270 protocol "Fepi" does the same but it
-           comes with cics.
- Application server = is one multi tasking machine.
- CICSplex = for cics to talk to another cics it needs only the name of the
             cics.
- CTG      = cics transaction gateway. (_for instance to connect to a java app_)

-            cics is divided to sevral domian's see cics.domain.managment.png
            every domain has it's uniq 2 char id in every message.
- RDO     = Resource definition online.


- TCB/SCB   = a processor (_table control block_) usually TCB are regular
              cpu's , and SCB's stands for (_System control block_) for athor
              operation's
- usually when looking in the spool check out "control is being given"
- PLTPI
- DFHPLT     : (_PROGRAM LIST TABLE_) USE to auto start cics transactoin
               PLTPI start on cics statup, has two phases the first is bifore
               the "control is being given" message, the second is after.

 ## CICS SECURITY
               
SAF          : (_System Authorization Facility_)

call & link
xctl  does not come back to the parent program unlike call & link
          ## cicsPlex
          CESM = CICSplex
BMS       : (_Basic mapping support_)old school cics panels programing


MAS       : every CICS instance in a cicsPlex are calld "MAS"
CMAS      : Control mas this is the cics that the cics plex is installed.
NEWCOPY   : when updating a programe to load the new cicsMoudle to memory
            but only if the programe is not in use.
PHASEIN   :

DSA       : (_Dinamic storage erea_)CICS Address space

      - DSA  -------- Below the 16MB LINE
      - EDSA  -------- Above the 16MB LINE
      - GDSA  --------  Above the 2GB LINE


EIB       : (_exec interface block_)is a block of data about the task and it's return
            code
EIBCALEN comman area length
EIB
COMMAREA  : 32KB of data that you cat pass between cics
channels & containers this is the new way.

  ## Inter Communication System
  - MRO     : (_Multi Reign Operation_) Allows cics instance's to communicate
              with out the use of **TCP/IP or ACF/VTAM**


  - ISC     : (_Inter System Communication_) to communicate cics to non-cics
              apps and for cics in a different sysPlex.
              usually over **TCP/IP or ACF/VTAM**


IPIC      : tcp/ip
