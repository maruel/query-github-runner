# Query GitHub Runner

This repository defines a workflow that queries a lot of information from the
running environment. This help understanding the differences in behavior on the
runner versus a local environment.

While https://github.com/actions/runner-images provides information about the
base image, it doesn't contain the sources of
`c:\actions\runner-provision-Windows\provisioner.exe`

See recent actions at
https://github.com/maruel/query-github-runner/actions/workflows/query_windows.yml
to see the output of the workflow.

Here's a few interesting bits:

## Take screenshot

![screenshot.png](screenshot.png)

## Get-PhysicalDisk

```
Number FriendlyName SerialNumber MediaType   CanPool OperationalStatus HealthStatus Usage         Size
------ ------------ ------------ ---------   ------- ----------------- ------------ -----         ----
0      Virtual HD                Unspecified False   OK                Healthy      Auto-Select 256 GB
1      Virtual HD                Unspecified False   OK                Healthy      Auto-Select 150 GB
```

## Get-Disk

```
Number Friendly Name Serial Number                    HealthStatus         OperationalStatus      Total Size Partition
                                                                                                             Style
------ ------------- -------------                    ------------         -----------------      ---------- ----------
0      Virtual HD                                     Healthy              Online                     256 GB MBR
1      Virtual HD                                     Healthy              Online                     150 GB MBR
```

## Get-CimInstance -ClassName Win32_Processor

```
DeviceID Name                                            Caption                            MaxClockSpeed SocketDesigna
                                                                                                          tion
-------- ----                                            -------                            ------------- -------------
CPU0     AMD EPYC 7763 64-Core Processor                 AMD64 Family 25 Model 1 Stepping 1 2445          None
```


## Get-CimInstance -ClassName Win32_PhysicalMemory

```
Caption              : Physical Memory
Description          : Physical Memory
Name                 : Physical Memory
CreationClassName    : Win32_PhysicalMemory
Manufacturer         : Microsoft
PartNumber           : None
SerialNumber         : None
Tag                  : Physical Memory 0
FormFactor           : 0
BankLabel            : None
Capacity             : 1073741824
InterleavePosition   : 0
MemoryType           : 1
DeviceLocator        : M0
InterleaveDataDepth  : 0
SMBIOSMemoryType     : 1
TypeDetail           : 4

Caption              : Physical Memory
Description          : Physical Memory
Name                 : Physical Memory
CreationClassName    : Win32_PhysicalMemory
Manufacturer         : Microsoft
PartNumber           : None
SerialNumber         : None
Tag                  : Physical Memory 1
FormFactor           : 0
BankLabel            : None
Capacity             : 16106127360
InterleavePosition   : 0
MemoryType           : 1
DeviceLocator        : M1
InterleaveDataDepth  : 0
SMBIOSMemoryType     : 1
TypeDetail           : 4
```

## Get-CimInstance Win32_StartupCommand

```
Command                                                    User   Caption
-------                                                    ----   -------
C:\PROGRA~1\MICROS~4\SERVIC~1\Tools\SERVIC~2\SERVIC~1.EXE  Public Service Fabric Local Cluster Manager
%windir%\system32\SecurityHealthSystray.exe                Public SecurityHealth
%windir%\AzureArcSetup\Systray\AzureArcSysTray.exe         Public AzureArcSetup
```
