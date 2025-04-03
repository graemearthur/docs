## DHCP updates

cat /etc/dhcp/dhcpd.conf | grep -i reddgc001
service dhcpd restart

# Fai where classes is located
vi /srv/fai/config/stretch/class/50-host-classes

## Creating FAI files
fai-chboot -C /stretch/fai -IBv -s 4.9.0-6-amd64.stretch  -u nfs://redfai000/stretch/config -k "rootovl HOSTNAME=red99vm002" red99vm002

fai-chboot -C /bullseye/fai -IBv -s 5.10.0-8-amd64.bullseye  -u nfs://redfai000/bullseye/config -k "rootovl HOSTNAME=red99vm002" red99vm002

## PXE commands

### get hex from hostname
gethostip reddgc001
# Don't forget to enable after file exists
enablepxe 0AA440F4

# Location of /PXE
cd /srv/tftp/fai/pxelinux.cfg/

# Commands for Nutanix VMs only

## commmand to set boot via pxe
acli vm.update_boot_device red99vm002 mac_addr=50:6b:8d:a4:c4:84

## command to reset nutanix boot device to default
acli vm.update_boot_device vmname
