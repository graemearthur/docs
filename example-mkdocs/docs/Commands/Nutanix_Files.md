# Nutanix Files Notes

# show all smb connections
afs smb.conn verbose=true

# list all snapshots for a Nutanix File share_name
afs snapshot.list share_name=infra-nexus

# list all file shares (example with grep)
nutanix@NTNX-EOAACVM001NX-CVM:10.116.208.51:~$ ncli fs list-all-fs-shares | grep -i infra-nexus
    Name                      : swinfra-nexus
    Share Path                : /swinfra-nexus




# Example of force deleting a Nutanix share from fsvm
# get uuid and share uuid from ncli fs list-all-fs-shares
nutanix@NTNX-EOAACVM001NX-CVM:10.116.208.51:~$ ncli fs delete-share uuid=276beab3-e283-43a5-9df0-017cd32e1531 share-uuid=dd258bad-6891-4763-a87b-845f81995ce7 force=true

    Task Status               : 0
    Task Uuid                 : 734926ba-5b9e-48a3-7b62-2f7c65f54be0

    <afs> nfs.show_clients
Number of Clients connected: 8
List of client IP addresses:
10.115.64.112
10.115.129.29
10.115.129.31
10.116.192.56
10.116.192.226
10.116.200.3
10.116.200.4
10.116.200.26