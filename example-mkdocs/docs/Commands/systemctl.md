# useful Commands to file / Remember

## command to stop ETX connection node
systemctl stop otetxcn.service 

## command to stop ETX server
systemctl stop ot.service 

## Command to restart xorg with Multiple seats
/etc/init.d/xorg-multiterminal restart

## systemctl show all running 
systemctl --type=service --state=running

## systemctl file 
systemctl cat processname