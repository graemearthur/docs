## Info on machine - Time/How long the machine has been up/Load
uptime

## Check the disk partitions - mounts
df -h

## Listing all of the directories in /s0
ls /s0
scr1  scr2  scratch  spool  tad

## Displaying messages from the machine - with time stamp

dmesg -T

## Displaying messages from the machine - with a time stamp and string

dmesg -T | grep -i error
 
## List the serial numbers (disks)

hdparm -i /dev/sda | grep -i serial


hdparm -i /dev/sd* | grep -i serial     - wildcard for both disk (a/b)

nvme list

## Using smart

smartctl -a /dev/sd[a/b/c/d]

## Using smart nvme
smartctl -a /dev/nvme?n0 - ? = the disk number

# GPU card checks

nvidia-smi                    - shows GPU info in table

nvidia-smi -L                - Lists all available devices


# Script for showing GPU location on MB and devices available
/flat4/pzapparo/gpulist.sh

## Ipmitool - commands

ipmitool sel list    - List all events

ipmitool sdr         - List status of all components
 
./ipmi_configure     - Run IPMI configuration - Web access

ipmitool sel clear   - Clear all events

# Puppet

puppet agent -t

## To run a I/O error check on the disks

dd if=/dev/sda of=/dev/zero status=progress


# Test eth0 
ethtool eth0
ethtool -t eth0
# Check Tango file location
ls /etc/tango

# Error investigation
root@red2902096:~# zgrep -i error /var/log/syslog*

# Check for memory issues
valgrind --tool=memcheck ls l

## Fai info

puppet cert clean red3403039.int.cgg.com

enablepxe red3403039