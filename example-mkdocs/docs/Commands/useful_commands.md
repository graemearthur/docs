display when your user
```
setenv DISPLAY redapp105:39
```

set display when root
```
export DISPLAY=redapp101:15
```
# set proxy as root
export https_proxy=http://gateway.zscaler.net:80
export http_proxy=http://gateway.zscaler.net:80

# set proxy as user
setenv https_proxy http://gateway.zscaler.net:80
setenv http_proxy http://gateway.zscaler.net:80

Check space used
```
:~# du -hx /s0 | sort -h
```

# find high load dead processes
ps -eo s,user,cmd,pid | grep ^[RD] |wc -l

# when ifdown doesn't work
ifconfig eth0 down



ps -eo pid,lstart,cmd
The above command will output all processes, with formatters to get PID, command run, and date+time started.

From <https://stackoverflow.com/questions/5731234/how-to-get-the-start-time-of-a-long-running-linux-process> 

```
| wc-l
```
Count number of lines

From <https://stackoverflow.com/questions/6314679/in-bash-how-do-i-count-the-number-of-lines-in-a-variable>

oneliner to ssh-copy-id in windows - replace hostname
```
type $env:USERPROFILE\.ssh\id_rsa.pub | ssh 192.168.30.31 "cat >> .ssh/authorized_keys"
```
