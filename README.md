# ticket_298623

Notes for ticket 298623, related to [UPPMAX documentation #126](https://github.com/UPPMAX/UPPMAX-documentation/issues/126).

Hypothesis: not all RStudio versions work,
user needs to load the one that is documented to work.

Questions:

- Does RStudio/2023.06.2-561 indeed work as documented?
  - Does loading this module also load R?
  - Does loading this module also load R_packages?
- Does the newer RStudio/2023.12.1-402 also works in the same way?
  - Does loading this module also load R?
  - Does loading this module also load R_packages?

Questions with answers:

- Does RStudio/2023.06.2-561 indeed work as documented? No
  - Does loading this module also load R? No
  - Does loading this module also load R_packages? No
- Does the newer RStudio/2023.12.1-402 also works in the same way? Yes
  - Does loading this module also load R? No
  - Does loading this module also load R_packages? No

## Procedures

### Subquestion 1a, the (incorrect?) UPPMAX doc approach for RStudio/2023.06.2-561:

- Start rackham-gui.uppmax.uu.se
- Start an `interactive` session with 2 nodes (user uses 5, but 2 should work too)

```bash
interactive -t 2:00:00 -n 2 -A staff
```

- Load the RStudio/2023.06.2-561 module, without R and without R_Packages

```
module load RStudio/2023.06.2-561
```

Gives:

```
[richel@r210 richel]$ module load RStudio/2023.06.2-561
RStudio/2023.06.2-561: Sandboxing is not enabled for RStudio at UPPMAX. See 'module help RStudio/2023.06.2-561' for more information

[richel@r210 richel]$ module list

Currently Loaded Modules:
  1) uppmax   2) PostgreSQL/10.3   3) RStudio/2023.06.2-561
```



- Obtain the R version

```
[richel@r210 richel]$ module load RStudio/2023.06.2-561
RStudio/2023.06.2-561: Sandboxing is not enabled for RStudio at UPPMAX. See 'module help RStudio/2023.06.2-561' for more information
[richel@r210 richel]$ R --version
R version 3.6.0 (2019-04-26) -- "Planting of a Tree"
Copyright (C) 2019 The R Foundation for Statistical Computing
Platform: x86_64-redhat-linux-gnu (64-bit)

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under the terms of the
GNU General Public License versions 2 or 3.
For more information about these matters see
https://www.gnu.org/licenses/.
```

- Check if packages are installed
- Start RStudio, record errors

```
[richel@r210 richel]$ rstudio
[10829:0905/082808.948237:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[10829:0905/082808.948688:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[10829:0905/082809.562579:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[10829:0905/082809.637181:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[10883:0905/082809.818860:ERROR:gpu_memory_buffer_support_x11.cc(49)] dri3 extension not supported.
[10829:0905/082810.073515:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[10829:0905/082813.962082:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[10829:0905/082814.009277:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[10829:0905/082814.065842:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[10829:0905/082814.101876:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[10829:0905/082814.173446:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[10829:0905/082814.245107:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[10829:0905/082814.257955:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[10829:0905/082814.363277:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[10829:0905/082814.502333:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[10829:0905/082814.688413:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[10829:0905/082841.608768:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[10829:0905/082841.718912:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[10829:0905/082844.121524:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[richel@r210 richel]$ 
```

![](1a.png)

 

### Subquestion 1b, the (incorrect?) UPPMAX doc approach for RStudio/2023.12.1-402


```
module load RStudio/2023.12.1-402
module list
```

```
[richel@r210 richel]$ module load RStudio/2023.12.1-402
RStudio/2023.12.1-402: Sandboxing is not enabled for RStudio at UPPMAX. See 'module help RStudio/2023.12.1-402' for more information
[richel@r210 richel]$ module list

Currently Loaded Modules:
  1) uppmax   2) PostgreSQL/10.3   3) RStudio/2023.12.1-402

```

```
[richel@r210 richel]$ R --version
R version 3.6.0 (2019-04-26) -- "Planting of a Tree"
Copyright (C) 2019 The R Foundation for Statistical Computing
Platform: x86_64-redhat-linux-gnu (64-bit)

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under the terms of the
GNU General Public License versions 2 or 3.
For more information about these matters see
https://www.gnu.org/licenses/.
```

```
[richel@r210 richel]$ rstudio
[11637:0905/083327.797032:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[11637:0905/083327.797233:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[11637:0905/083327.797295:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[11637:0905/083327.797360:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused

(rstudio:11637): dconf-CRITICAL **: 08:33:28.519: unable to create directory '/run/user/4019125/dconf': Permission denied.  dconf will not work properly.

(rstudio:11637): dconf-CRITICAL **: 08:33:28.545: unable to create directory '/run/user/4019125/dconf': Permission denied.  dconf will not work properly.
[11637:0905/083328.547302:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused

(rstudio:11637): dconf-CRITICAL **: 08:33:28.549: unable to create directory '/run/user/4019125/dconf': Permission denied.  dconf will not work properly.
[11637:0905/083328.599437:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[11637:0905/083328.741175:ERROR:object_proxy.cc(590)] Failed to call method: org.freedesktop.portal.Settings.Read: object_path= /org/freedesktop/portal/desktop: unknown error type: 
[11637:0905/083328.886902:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[11637:0905/083332.159845:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[11637:0905/083332.204327:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[11637:0905/083332.263417:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[11637:0905/083332.310827:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[11637:0905/083332.339524:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[11637:0905/083332.442935:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[11637:0905/083332.478774:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[11637:0905/083332.605164:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[11637:0905/083332.775689:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[11637:0905/083332.956050:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[11637:0905/083334.766375:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[11637:0905/083337.145918:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /tmp/dbus-5ixqlzjclI: Connection refused
[richel@r210 richel]$ 
```

![](1b.png)


## No modules

System R version is version 3.6.0 (from 2019-04-26):

```
[richel@rackham3 richel]$ module list

Currently Loaded Modules:
  1) uppmax

 

[richel@rackham3 richel]$ R --version
R version 3.6.0 (2019-04-26) -- "Planting of a Tree"
Copyright (C) 2019 The R Foundation for Statistical Computing
Platform: x86_64-redhat-linux-gnu (64-bit)

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under the terms of the
GNU General Public License versions 2 or 3.
For more information about these matters see
https://www.gnu.org/licenses/.
```
