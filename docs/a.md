# Exercise 1
You may be able to do a deal of reconnaissance in any operating system, just using built-in tools. I will only cover Windows tools in this note. All drives use Self-Monitoring Analysis and Reporting Technology (SMART) to report on their status. Windows Management Instrumentation (WMI) is “a set of specifications from Microsoft for consolidating the management of devices and applications” [1]. WMI command-line (WMIC) utility provides a command-line interface to WMI.

Open the command prompt as administrator.

See what is available, try the command

````
wmic diskdrive get /?
````

To get all the data you could ever want, type

````
wmic diskdrive
````

it is not very readable. I dump the output to a file so I can open it later using 

````
wmic diskdrive > disks.txt
````

and then I open disks.txt in Notepad. 

Extract the most important information and create a table for your results.

To get the SMART status of the disks, try the command 

````
wmic /namespace:\\root\wmi path MSStorageDriver_FailurePredictStatus
````

This works on my private W10 laptops, but I need administrator privilege to run.

You can carry out similar in Power Shell using 

````
Get-WmiObject -namespace:root\wmi –class MSStorageDriver_FailurePredictStatus
````

For volume maintenance, you can also use chkdsk. Try the command 

````
chkdsk /?
````

to see what options there are. CHKDSK has been around since the early days of MS-DOS.



