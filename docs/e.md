## Exercise 4
Run Resource Monitor from the search bar. Look around and understand what is there. Go to the Memory tab. 

Watching the color-coded Physical Memory bar graph on the Memory tab of Resource Monitor is by far the best way to see exactly what Windows is up to at any given time. 

## Hardware Reserved (grey) 
This is physical memory that is set aside by the BIOS and other hardware drivers (especially graphics adapters). This memory cannot be used for processes or system functions. 

## In Use (green) 
The memory shown here is in active use by the Windows kernel, by running processes, or by device drivers. This is the number that matters above all others. If you consistently find this green bar filling the entire length of the graph, you are trying to push your physical RAM beyond its capacity. 

## Modified (orange) 
This represents pages of memory that can be used by other programs but would have to be written to the page file before they can be reused. 

## Standby (blue) 
Windows tries as hard as it can to keep this cache of memory as full as possible. In XP and earlier, the Standby list was a first-in, first-out cache. Beginning with Windows Vista and continuing with Windows 7 and 10, the memory manager is much smarter about the Standby list, prioritizing every page on a scale of 0 to 7 and reusing low-priority pages ahead of high-priority ones. If you start a new process that needs memory, the lowest-priority pages on this list are discarded and made available to the new process. 

## Free (light blue) 
Windows tries its very best to avoid leaving any memory at all free. If you find yourself with a big enough chunk of memory here, you can bet that Windows will do its best to fill it by copying data from the disk and adding the new pages to the Standby list. 

From Windows 7 onwards (and unlike XP and earlier Windows versions), the OS goes by the philosophy that empty RAM is wasted RAM and tries to keep it as full as possible, without impacting performance.