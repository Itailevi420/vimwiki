

### Commands (cmdlets, executables, scripts, aliases)

```PowerShell
get-command -Noun Network*
get-command -Verb get -Noun file*

Get-Help -Name Get-Help

Get-Process -Name 'firefox'
Get-Process -Name 'firefox' | Get-Member
Get-Process -Name 'name-of-process' | Get-Member | Select-Object Name, MemberType
Get-Command -ParameterType Process
```
we can see the Object type in the first row of `Get-Member` cmdlet OUTPUT
e.g:
_issue the Cmdlet `Get-Process` with the `-Name` flag_
```PowerShell
PS C:\Users\Itai> Get-Process -Name 'firefox' | Get-Member
```
OUTPUT:
```PowerShell

   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
NPM                        AliasProperty  NPM = NonpagedSystemMemorySize64
PM                         AliasProperty  PM = PagedMemorySize64
SI                         AliasProperty  SI = SessionId
VM                         AliasProperty  VM = VirtualMemorySize64
WS                         AliasProperty  WS = WorkingSet64
Parent                     CodeProperty   System.Object Parent{get=GetParentProcess;}
.........
.........
more.....
```

