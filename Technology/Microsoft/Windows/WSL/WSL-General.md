# WSL (Windows Subsystem for Linux)

## General

```powershell
# Restart WSL Service
Get-Service vmcompute | Restart-Service
```

## Secure SHell (SSH)

```bash
# Install `openssh-server`
sudo apt install openssh-server
```

```bash
# Start `ssh`
sudo service ssh start
```

```bash
# Run `ssh-agent`
# The `ssh-agent -s` command should be in `` (backtick)
eval `ssh-agent -s`
```

## Reference
* [Windows Subsystem for Linux Documentation](https://docs.microsoft.com/en-us/windows/wsl/)
* [Ubuntu 18.04 on WSL2: Logon failure: the user has not been granted the requested logon type at this computer.](https://stackoverflow.com/questions/62681041/ubuntu-18-04-on-wsl2-logon-failure-the-user-has-not-been-granted-the-requeste)
* [Differences between doublequotes, singlequotes and backticks on commandline?](https://askubuntu.com/questions/20034/differences-between-doublequotes-singlequotes-and-backticks-on-comm)
* [What does (backquote/backtick) mean in commands?](https://unix.stackexchange.com/questions/27428/what-does-backquote-backtick-mean-in-commands)