##Disks Physical & RAID

<details>
<summary>Dell</summary>
<p>

### omreport summary raid status 

```
clear; echo ""; echo "     Hostname: $(hostname)"; for i in `omreport storage vdisk | grep "^ID" | awk '{print $3 }'`; do printf '%58s\n' | tr ' ' -; omreport storage vdisk | grep -A10 "^ID" | grep -i "^ID\|layout\|^State\|^Status" | awk '{print $3 }' | grep -A3 -w "^$i" |tail -3| tr '\n' " "; echo ""; omreport storage vdisk | grep -A12 "^ID" | grep -i "^ID\|write through" | grep -v "^ID"; omreport storage pdisk controller=0 vdisk=$i| grep -i "raid\|Name\|State\|Predicted\|Progress" | grep -v "Space\|Applicable\|: No"; done; printf '%58s\n' | tr ' ' - 
```

### Dell - Display RAID status using omreport 

```
echo -e "\nPhysical Disk Status:"; omreport storage pdisk controller=0 2>&1| grep -E '^ID|^Status|^Name|^State|^Failure Predicted|^Serial No.|^Part Number|^Capacity|^[[:space:]]$' | sed 's/^ID/\nID/';echo -e "\nLogical Volume Status:"; omreport storage vdisk controller=0 | grep -E '^ID|^Status|^State|^Name|^Layout|^Size|^Device|^[[:space:]]$'| sed 's/^ID/\nID/' 
```
</details>

<details>
<summary>HP</summary>
<p>

### HP - Display RAID status using hpacucli 

This will display the RAID cache backup battery status as well as spindle and array status. 

```
hpacucli "ctrl all show config detail" | grep -E 'Firmware Version:|Cache Status:|Battery/Capacitor Status:|Logical Drive:|^ *Status:|Mirror Group|physicaldrive|Bay:|^ *$|Serial Number:'  | grep -vE '^[[:space:]]*$' 
```

### HP - Display RAID status using ssacli / hpssacli 

```
ssacli / hpssacli "ctrl all show config detail" | grep -E 'Firmware Version:|Cache Status:|Battery/Capacitor Status:|Logical Drive:|^ *Status:|Mirror Group|physicaldrive|Bay:|^ *$|Serial Number:'  | grep -vE '^[[:space:]]*$' 
```
<p>
HP - Check RAID cache, accelerator, and battery status using ssacli, hpacucli or hpssacli

using hpacucli:

```
hpacucli ctrl all show config detail | grep -iE 'cache|accel|Battery' 
```

using hpssacli:
```
ssacli / hpssacli ctrl all show config detail | grep -iE 'cache|accel|Battery'
```

</details>

   
[root@545792-dr-app1 ~]# omreport storage pdisk controller=0 | egrep "Name|Stat|Fail|^$"

# Array & Virtual Disk Info

#List of Virtual Disks in the System useful to check raid level of disks. 

omreport storage vdisk 


#Physical Disks
 
### check physical disk status 

omreport storage pdisk controller=0 pdisk=0:1:1 

Omreport RAID 

omreport storage pdisk controller=0|grep Progress 

omreport storage pdisk controller=0 


### List of Physical Disks belonging to array 00 
omreport storage pdisk controller=0 vdisk=0 

