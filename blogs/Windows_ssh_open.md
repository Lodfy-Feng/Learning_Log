Here is my situation:
I have my laptop and my PC on my desk. And they are connected via a switch machine.

I want to scp some directories, but find sshd not open.So I question the AI and search on the Internet, then give the following process:
1.
```
who am i
```
Through this cmd in the powershell, we can get the PC-name and current user name.
2.
```
ipconfig
```
get the ip address of this pc.
3.
```
ping $(ipadress)
```
And we can test whether we can connect laptop to the PC via the ssh technology.
4.
If sshd doesn't open, then we need to execute the following commands to open the ssh:
```
Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
```
Then we execute this cmd:
```
Start Service sshd
```
we can even set sshd as an automatic starter as the PC starts:
```
Set-Service -Name sshd -StartupType 'Automatic'
```

4.Add the firewall
```
New-NetFirewallRule -DisplayName 'OpenSSH Server(sshd)' -Direction Inbound -Protocol TCP -LocalPort 22 -Action Allow
```
Then we can get the laptop ssh working.


But make sure you know the password.
Just in case, you can modify the pw using "net user administrator $(pw)" cmd in administractive powershell.
