---
title: README
date: 2023-09-14
---

# `ipcalc.py`


## Info

View network information for a provided IPv4 address and subnet mask. 



## Overview

This program was written to act similar to the perl version of [`ipcalc`](https://jodies.de/ipcalc). 

The main purpose for writting this was a need to include such a program in docker images with a much smaller footprint.

Some of differences between this program and Perl ipcalc are:

- Change the dependancy from Perl over to Python3
- Present output where items are separated by whitespace (useful for `awk`)
- Removed extra information such as binary data and colors
- Added command line options to filter the output by fields
- Added an interactive mode if a subnet is not provided on the command line

Run `ipcalc.py` by supplying the IPv4 address and subnet mask as the argument. 

By default, if no arguments are supplied, the script will enter an interactive mode and prompt the user to enter a subnet.

For a list of commands run `ipcalc.py` with the `-h` or `--help` options.


## Examples

```bash
$ ipcalc.py 172.16.31.45/28
Network:      172.16.31.32/28
Netmask:      255.255.255.240
Netmask_Bits: 28
Network_Addr: 172.16.31.32
Host_Min:     172.16.31.33
Host_Max:     172.16.31.46
Broadcast:    172.16.31.47
Total_Hosts:  14
```

```bash
$ ipcalc.py
Enter subnet or `q` to quit: 10.20.30.9/30
Network:      10.20.30.8/30
Netmask:      255.255.255.252
Netmask_Bits: 30
Network_Addr: 10.20.30.8
Host_Min:     10.20.30.9
Host_Max:     10.20.30.10
Broadcast:    10.20.30.11
Total_Hosts:  2
Enter subnet or `q` to quit:
```

```bash
$ ipcalc.py --help
usage: ipcalc.py [-h] [-v] [-f key] [subnet ...]

Tools for obtaining IP information like broadcast, network, etc.

positional arguments:
  subnet                IP subnet. Separate with a slash "/" or space.
                        (examples: 192.168.10.0/24 or 192.168.10.0
                        255.255.255.0)

options:
  -h, --help            show this help message and exit
  -v, --version         show the version number and exit
  -f key, --filter key  Enter one or more `key(s)` to filter the output.
                        Omitting this option shows all keys. Keys are:
                        ('network', 'netmask', 'netmaskbits', 'networkaddr',
                        'broadcast', 'hostmin', 'hostmax', 'numhosts')

Have a great day!
```


## Requirements

The following are requirements to run this script:

- python3
