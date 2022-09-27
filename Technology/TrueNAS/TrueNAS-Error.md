# TrueNAS Error

## Currently Unreadable Sector

```plaintext
Device: /dev/<device> [SAT], 1 Currently unreadable (pending) sectors
```

### Solution

Run a SMART long self-test

```plaintext
smartctl -t long /dev/<device>
```

## Reference

* [Fixing FreeNAS Error: Currently unreadable (pending) sectors](http://bytesandbolts.com/fixing-freenas-error-currently-unreadable-pending-sectors/){:target="_blank"}