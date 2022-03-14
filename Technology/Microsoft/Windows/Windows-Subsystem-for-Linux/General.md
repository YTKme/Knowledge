# Windows Subsystem for Linux

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
* [Differences between doublequotes, singlequotes and backticks on commandline?](https://askubuntu.com/questions/20034/differences-between-doublequotes-singlequotes-and-backticks-on-comm)
* [What does (backquote/backtick) mean in commands?](https://unix.stackexchange.com/questions/27428/what-does-backquote-backtick-mean-in-commands)