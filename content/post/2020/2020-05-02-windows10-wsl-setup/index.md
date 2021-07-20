---
title: "Windows 10 Laptop setup with WSL 2.0."
date: 2021-01-30T15:29:00-08:00
draft: false
toc: false
comments: true
twitterImage:
categories:
- SRE
- Windows
- Linux
---

Couple of days back i lost my Macbook to water and here i am shifting to windows in middle of a national wide lockdown. (Future me should remember this COVID19 lockdown of 2020)   
I personally prefer Linux based machines but in middle of lockdown this is the best i can arrange to continue my office work.
Lets give windows and wsl 2.0 a try instead of switching between a dual boot system that we used to have in our college days.

1. I am still searching for a google windows setup guide for a development environment apart from Microsoft World.
[Very Good Blog i found to customize WSL]
(https://www.smashingmagazine.com/2019/09/moving-javascript-development-bash-windows/#top)
[Awesome WSL]
(https://github.com/sirredbeard/Awesome-WSL#terminals)

2. Terminal for windows.
I am still waiting for Terminal 2.0 lets get the latest one from microsoft store.
[Terminal for Windows](https://github.com/microsoft/terminal)

3. Terminal customization.
I am big fan of shortcuts on terminal and utilities that make use of terminal piece of cake. List of URLs to read to customize the Windows Terminal as an alternative to iTerm2. 

- https://aka.ms/terminal-color-schemes
- https://aka.ms/terminal-keybindings
- https://aka.ms/terminal-selection
- https://aka.ms/terminal-panes


4. SSH access from both WSL and windows at one place.
- Add SSH keys in Username space in Windows and symlink it.
https://docs.microsoft.com/en-us/windows/wsl/troubleshooting#correct-ssh-related-permission-errors

- Add SSH Config as per requirement: https://www.cyberciti.biz/faq/create-ssh-config-file-on-linux-unix/
StrictHostKeyChecking no

OpenSSH-Client is installed by default in windows. ssh-agent service is disabled and so you can not use this service.
I would recommended setting the service to automatic mode.
Steps:
* Windows + R and search services.
* Search for: OpenSSH Authentication Agent.
* Edit it to startup type as automatic. 

While Windows people are making it more convenient to use all windows services accessible from WSL OpenSSH ssh-agent is still not one of them. Here is the fix to use it via WSL 2.
https://github.com/rupor-github/wsl-ssh-agent#wsl-2-compatibility

5. Ubuntu 20.04 customizations on WSL 2.0
Some addition tools for ubuntu WSL 2.0:
```
sudo apt-get install fzf
```
```
sudo apt install net-tools (ifconfig)
sudo apt install traceroute tcptraceroute
```
6. Kubernetes related configurations on ubuntu 20.04 WSL 2.0
curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.15.0/bin/linux/amd64/kubectl

https://kubernetes.io/docs/tasks/extend-kubectl/kubectl-plugins/
https://krew.sigs.k8s.io/docs/user-guide/quickstart/

https://github.com/jonmosco/kube-ps1

```
kubectl krew install ctx
kubectl krew install ns
```

7. Docker for windows with access from WSL 2.0 and Windows Home support.
- https://docs.docker.com/docker-for-windows/

- https://www.docker.com/blog/docker-desktop-for-windows-home-is-here/

- [You will need windows insider program for this to work](https://insider.windows.com/en-gb/welcome-insider/)

8. Bridge between WSL2.0 and Windows.
- File Storage
https://www.tenforums.com/tutorials/127857-access-wsl-linux-files-windows-10-a.html

- Network Sockets
https://github.com/jstarks/npiperelay
https://github.com/rupor-github/wsl-ssh-agent#wsl-2-compatibility

9. Issues with WSL 2 time.
https://github.com/microsoft/WSL/issues/4245
I noticed WSL 2 time was 5 min ahead on Windows time and aws cli tool was breaking for the same.
Quick Fix: 
```
sudo hwclock -s
```
Sometimes if WSL is not responding a restart of WSL is needed.
Restart all WSL using ADMIN powershell:
```
Get-Service LxssManager | Restart-Service
```