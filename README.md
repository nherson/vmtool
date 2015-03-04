# VMTool

### Overview
VMTool is a really simple script that allows a Systems Administrator to quickly interact with VMWare VSphere from a shell session. It was developed at Residential Computing at UC Berkeley to make powering on/off and snapshotting VMs easier.

### Usage
The script supports the following operations:
```
poweron HOST1 HOST2 ...
poweroff HOST1 HOST2 ...
snapshot [--poweroff] HOST1 HOST2 ...
status HOST1 HOST2 ...
popsnapshot HOST1 HOST2 ...
listsnapshots HOST1 HOST2 ...
```

In addition, each command also accepts a `-g` flag.  If `-g` is specified, it interprets the arguments as _groups_ instead of _hosts_.  In this case, it looks for matching `[hostgroups]` entries in a file located at `~/.vmtool.conf`. An example of this config file might look like this:

```
[vsphere]
host=vsphere.example.com
username=nherson

[hostgroups]
testing=test-host1,test-host2,test-host3
production=host1,host2,host3
```

Given the above sample configuration, the following two commands are operationally equivalent:
```
vmtool snapshot host1 host2 host3
vmtool snapshot -g production
```

### Dependencies
- pysphere
