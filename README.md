ansible-ghettoVCB
====================

An ansible play for ghettoVCB

This configuration assumes that you have a pre-configured datastore where you won't delete your ghettoVCB scripts upon upgrading or re-installing your ESX environment such as on your NFS or iSCSI storage array(s), and this also assumes that you have Ansible running on a Linux machine. In CentOS you can do ```yum install ansible -y``` after installing the EPEL packages.

modify these 3 variables: **ghettoVCB**, **invFile**, **logFile** with the full path to them on the shared storage device. It usually looks something like this:

```
ghettoVCB: '/vmfs/volumes/array1/vcb/ghettoVCB.sh'
invFile: '/vmfs/volumes/array1/vcb/baklist'
logFile: '/vmfs/volumes/array1/vcb/logs/vcblog_`date+\%Y\%m\%d\%h\%M\%S`.log 2>&1'
```
save the YAML file then modify the hosts file with the ESX(i) server you want to run the ghettoVCB scripts on.

run the command
```
ansible-playbook -i vmhosts ansible-ghettoVCB.yml -k
```

It should start to run the playbook.
