

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
$p i3  ---> stops initiator 3
$s i3  ---> starts initiator 3
d omvs,a=all   -->  to show all unix process
F BPXOINIT,TERM=pid   -->  to terminate a unix process (F means modify)
F BPXOINIT,SHUTDOWN=FORKINIT  --> forkinit means that the unix system
                                  will stop taking process's  F means modify

v xcf,
to attach a console:
/devlist
/detach 010
/d u,,,010,1
/attach unit type group
/attach 010 3270 console
/v 010,console
```

multi line WTO   - when a command write's to the console usually each line ends
with 210 address space.
sys1.uans? to set in racf some config

Dinamic Address translation   =  the component that translats virtual storage
                                 to real storage
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
