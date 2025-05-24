# pgAdmin Install

## Table of Content

## Python

### Install

A Python package is available for those wishing to run pgAdmin as a web
application in a Python environment. Note that the packages do not
include the Desktop Runtime.

pgAdmin is available on [PyPi](https://pypi.org/project/pgadmin4/). To
install it, create a virtual environment as required, and then use `pip`
to install.

```shell
pip install pgadmin4
```

> Note that pgAdmin will run in server mode, using system-wide paths so
> you may need to create them first:

```shell
sudo mkdir /var/lib/pgadmin
sudo mkdir /var/log/pgadmin
sudo chown $USER /var/lib/pgadmin
sudo chown $USER /var/log/pgadmin
```

Alternatively...

To customize the system-wide path(s)
* Create the `lib` and `log` directory in a separate path(s)
* Update `config.py` with the new `lib` and `log` path(s)

**Create Directory**

```shell
sudo mkdir --parents /path/to
sudo chown --recursive $USER /path/to
```

```shell
mkdir --parents /path/to/pgadmin/var/lib
mkdir --parents /path/to/pgadmin/var/log
```

**Update Configuration**

```shell
sed -i '' 's|DATA_DIR = os\.path\.join('\''/var/lib/'\'', APP_PATH)|DATA_DIR = os\.path\.join('\''/path/to/pgadmin/var/lib'\'', APP_PATH)|' /path/to/python/lib/python/site-packages/pgadmin4/config.py
sed -i '' 's|LOG_FILE = os\.path\.join('\''/var/log'\'', APP_PATH, APP_SHORT_NAME + '\''\.log'\'')|LOG_FILE = os\.path\.join('\''/path/to/pgadmin/var/log'\'', APP_PATH, APP_SHORT_NAME + '\''\.log'\'')|' /path/to/python/lib/python/site-packages/pgadmin4/config.py
```

## Reference

* [pgAdmin Download](https://www.pgadmin.org/download/)
* [pgAdmin (PyPI)](https://pypi.org/project/pgadmin4/)
* [pgAdmin The `config.py` File](https://www.pgadmin.org/docs/pgadmin4/latest/config_py.html)
