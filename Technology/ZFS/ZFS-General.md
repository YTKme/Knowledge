# ZFS

## Overview

ZFS (previously Zettabyte File System) combines a file system with a volume manager.

## General Command

### zpool status
* [Oracle Solaris ZFS Administration Guide Documentation](https://docs.oracle.com/cd/E19253-01/819-5461/gbbxi/index.html)
* [OpenZFS Documentation](https://openzfs.github.io/openzfs-docs/man/8/zpool-scrub.8.html)

```bash
# Display status of the pool with scrubbing operation information
zpool status -v <pool>
```

### zpool scrub
* [Oracle Solaris ZFS Administration Guide Documentation](https://docs.oracle.com/cd/E19253-01/819-5461/gbbxi/index.html)

```bash
# Initiate an explicit scrub of a pool
zpool scrub <pool>
```

```bash
# Stop a scrubbing operation that is in progress
zpool scrub -s <pool>
```

## Reference

### General
* [OpenZFS Documentation](https://openzfs.github.io/openzfs-docs/)
* [Oracle Solaris ZFS Administration Guide](https://docs.oracle.com/cd/E19253-01/819-5461/index.html)