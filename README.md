# OFBootMenu

OFBootMenu is a boot selector for the Pegasos platform written in
Forth. A simple configuration file specifies the set of operating
system choices and the commands used to boot each one.

# Installation

* Copy 'bootmenu' and 'bootmenu.conf' to one of the partitions
  accesible by SmartFirmware. You may want to choose the "less
  volatile" partition.

* Edit bootmenu.conf and customize it to suit your needs. See the
  Syntax section for details.

* Test the configuration. In SmartFirmware, type:
```
  boot hd:<your-partition-number> bootmenu
```
* If you're not satisfied with the results, edit the configuration 
  and test again

* In SmartFirmware, type:
```
  setenv boot-device hd:<your-partition-number>
  setenv boot-file bootmenu
```
* Enjoy!


# Usage

Just use the cursors to select the desired option. Pressing <RETURN>
will execute the corresponding command.


# Syntax

The configuration file accepts the following commands:

`\ <string>`
   Comment line


`print <string>`
   Prints the string. You can use escape characters for the string if
   you use a decent editor. This allows you to assign colors to the
   lines in the menu.

`command <string>`
   Turns the preceding "print" line into a choice and associates a
   command to it.

`timeout <N> <string>`
   Sets the timeout to N seconds. Prints the remaining time counter
   followed by the string.

`bartimeout <N> <string>`
   Sets the timeout to N seconds. Prints the string followed by a bar
   representing the remaining seconds.
