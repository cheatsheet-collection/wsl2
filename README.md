# WSL2 Cheatsheet
A collection of common commands to fix common WSL2 problems


## Networking
### Add portforward WSL2 to Network
1. Get the ip address of your wsl machine. You can do that using the following command in the wsl terminal if you have ipconfig installed `ifconfig eth0 | egrep 'inet ([0-9]+\.[0-9]+\.[0-9]+\.[0-9]+)'`.
1. On the Windows side you can now run PowerShell as Administrator and run `netsh interface portproxy add v4tov4 listenport=<PORT> listenaddress=0.0.0.0 connectport=<PORT> connectaddress=<WSL_IP>`.

### Remove portforward WSL2 to Network
1. On the Windows side you can now run PowerShell as Administrator and run `netsh interface portproxy delete v4tov4 listenport=<PORT> listenaddress=0.0.0.0`.


### Reset portforward WSL2 to Network
If you don't forward all your ports everytime your WSL2 ip address changes it can be that localhost does not work anymore. You can reset your network using the following PowerShell commands:
```
wsl --shutdown
netsh winsock reset
netsh int ip reset all
netsh winhttp reset proxy
ipconfig /flushdns
```
