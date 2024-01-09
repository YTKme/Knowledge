# vmware FUSION Network

## Table of Content

## Overview

## Static <abbr title="Internet Protocol">IP</abbr> (Internet Protocol) Address

### Get <abbr title="Medium Access Control">MAC</abbr> (Medium Access Control) Address

> Note: Replace `<Virtual-Machine-Name>` with the appropriate virtual
> machine name.

```bash
cat ~/Virtual\ Machines.localized/<Virtual-Machine-Name>.vmwarevm/<Virtual-Machine-Name>.vmx | grep ethernet0.generatedAddress
```

```bash
# Output
ethernet0.generatedAddress = "xx:xx:xx:xx:xx:xx"
```

### Add Static <abbr title="Internet Protocol">IP</abbr> Address

> Note: Replace `<x>` with the appropriate `vmnet` number.

```bash
sudo vi /Library/Preferences/VMware\ Fusion/vmnet<x>/dhcpd.conf
```

> Note: Add configuration after the
> `####### VMNET DHCP Configuration. End of "DO NOT MODIFY SECTION" #######`
> comment.

```
host <Virtual-Machine-Name> {
    hardware ethernet xx:xx:xx:xx:xx:xx;
    fixed-address  ###.###.###.###;
}
```

### Restart vmware Application and Service

```bash
sudo /Applications/VMware\ Fusion.app/Contents/Library/services/services.sh --stop
sudo /Applications/VMware\ Fusion.app/Contents/Library/services/services.sh --start
```

## Reference

### General
* [Configuring the Network Connection](https://docs.vmware.com/en/VMware-Fusion/13/com.vmware.fusion.using.doc/GUID-E498672E-19DD-40DF-92D3-FC0078947958.html)
* [Creating Custom Networks](https://docs.vmware.com/en/VMware-Fusion/13/com.vmware.fusion.using.doc/GUID-C5837B81-9509-4F1B-9572-0EC0CFA87563.html)

### Static <abbr title="Internet Protocol">IP</abbr> Address
* [How To Setup Your VMWare Fusion Images To Use Static IP Addresses on Mac OS X](https://gist.github.com/pjkelly/1068716/921c8b62ca07e29a7312e81e7b2efa88b69858ab)
* [How To Setup Your VMWare Fusion Images To Use Static IP Addresses on Mac OS X v2](https://gist.github.com/mgutz/1b8b5569190155dc31b9)
* [Set a Static IP Address in VMware Fusion 7](https://willwarren.com/2015/04/02/set-static-ip-address-in-vmware-fusion-7/)
