# Service and Process Management
Services, also known as <mark style="background: #FF5582A6;">daemons</mark>, are fundamental components of a Linux system that run silently in the background "without direct user interaction". They perform crucial tasks that keep the system operational and provide additional functionalities. Generally, services can be categorized into two types:

#### System Services
These are internal services required during system startup. They perform essential hardware-related tasks and initialize system components necessary for the operating system to function properly.
#### User-Installed Services
These services are added by users and typically include server applications and other background processes that provide specific features or capabilities.

Daemons are often identified by the letter `d` at the end of their program names, such as `sshd` (SSH daemon) or `systemd`. Just as a car relies on both its core components and optional features to provide a complete experience, a Linux system utilizes both system and user-installed services to function efficiently and meet user needs.

In general, there are just a few goals that we have when we deal with a service or a process:
1. Start/Restart a service/process
2. Stop a service/process
3. See what is/was happening with a service/process
4. Enable/Disable a service/process on boot
5. Find a service/process

Most modern Linux distributions have adopted `systemd` as their initialization system (init system). It is the first process that starts during the boot process and is assigned the Process ID (`PID`). All processes in a Linux system are assigned a `PID` and can be viewed under the `/proc/` directory, which contains information about each process. Processes may also have a Parent Process ID (`PPID`), indicating that they were started by another process (the parent), making them child processes.

---
## Systemctl
After installing `OpenSSH` on our VM, we can start the service with the following command.
```bash
fsiccatto@htb[/htb]$ systemctl start ssh
```

After we have started the service, we can now check if it runs without errors.
```bash
fsiccatto@htb[/htb]$ systemctl status ssh
```

To add OpenSSH to the SysV script to tell the system to run this service after startup, we can link it with the following command: 
```bash
fsiccatto@htb[/htb]$ systemctl enable ssh
```
(cada vez que queramos que se inicie con el sistema)

We can also use `systemctl` to list all services.
```bash
fsiccatto@htb[/htb]$ systemctl list-units --type=service

UNIT                                                       LOAD   ACTIVE SUB     DESCRIPTION              
accounts-daemon.service                                    loaded active running Accounts Service         
acpid.service                                              loaded active running ACPI event daemon        
apache2.service                                            loaded active running The Apache HTTP Server   
apparmor.service                                           loaded active exited  AppArmor initialization  
apport.service                                             loaded active exited  LSB: automatic crash repor
avahi-daemon.service                                       loaded active running Avahi mDNS/DNS-SD Stack  
bolt.service                                               loaded active running Thunderbolt system service
```

It is quite possible that the services do not start due to an error. To see the problem, we can use the tool `journalctl` to view the logs.
```bash
fsiccatto@htb[/htb]$ journalctl -u ssh.service --no-pager
```

---
### Kill a Process
A process can be in the following states:
- Running
- Waiting (waiting for an event or system resource)
- Stopped
- Zombie (stopped but still has an entry in the process table).

Processes can be controlled using `kill`, `pkill`, `pgrep`, and `killall`. To interact with a process, we must send a signal to it. We can view all signals with the following command:
```bash
fsiccatto@htb[/htb]$ kill -l

 1) SIGHUP       2) SIGINT       3) SIGQUIT      4) SIGILL       5) SIGTRAP
 2) SIGABRT      7) SIGBUS       8) SIGFPE       9) SIGKILL     10) SIGUSR1
13) IGSEGV     12) SIGUSR2     13) SIGPIPE     14) SIGALRM     15) SIGTERM
14) IGSTKFLT   17) SIGCHLD     18) SIGCONT     19) SIGSTOP     20) SIGTSTP
25) IGTTIN     22) SIGTTOU     23) SIGURG      24) SIGXCPU     25) SIGXFSZ
26) IGVTALRM   27) SIGPROF     28) SIGWINCH    29) SIGIO       30) SIGPWR
37) IGSYS      34) SIGRTMIN    35) SIGRTMIN+1  36) SIGRTMIN+2  37) SIGRTMIN+3
38) IGRTMIN+4  39) SIGRTMIN+5  40) SIGRTMIN+6  41) SIGRTMIN+7  42) SIGRTMIN+8
49) IGRTMIN+9  44) SIGRTMIN+10 45) SIGRTMIN+11 46) SIGRTMIN+12 47) SIGRTMIN+13
410) IGRTMIN+14 49) SIGRTMIN+15 50) SIGRTMAX-14 51) SIGRTMAX-13 52) SIGRTMAX-12
511) IGRTMAX-11 54) SIGRTMAX-10 55) SIGRTMAX-9  56) SIGRTMAX-8  57) SIGRTMAX-7
512) IGRTMAX-6  59) SIGRTMAX-5  60) SIGRTMAX-4  61) SIGRTMAX-3  62) SIGRTMAX-2
613) IGRTMAX-1  64) SIGRTMAX
```
The most commonly used signals are:

| **Signal** | **Description**                                                                                                          |
| ---------- | ------------------------------------------------------------------------------------------------------------------------ |
| `1`        | `SIGHUP` - This is sent to a process when the terminal that controls it is closed.                                       |
| `2`        | `SIGINT` - Sent when a user presses `[Ctrl] + C` in the controlling terminal to interrupt a process.                     |
| `3`        | `SIGQUIT` - Sent when a user presses `[Ctrl] + D` to quit.                                                               |
| `9`        | `SIGKILL` - Immediately kill a process with no clean-up operations.                                                      |
| `15`       | `SIGTERM` - Program termination.                                                                                         |
| `19`       | `SIGSTOP` - Stop the program. It cannot be handled anymore.                                                              |
| `20`       | `SIGTSTP` - Sent when a user presses `[Ctrl] + Z` to request for a service to suspend. The user can handle it afterward. |
For example, if a program were to freeze, we could force to kill it with the following command:
```bash
fsiccatto@htb[/htb]$ kill 9 <PID> 
```

---
### Background a Process
Sometimes it will be necessary to put the scan or process we just started in the background to continue using the current session to interact with the system or start other processes. As we have already seen, we can do this with the shortcut `[Ctrl + Z]`. As mentioned above, we send the `SIGTSTP` signal to the kernel, which suspends the process.
```bash
fsiccatto@htb[/htb]$ ping -c 10 www.hackthebox.eu

fsiccatto@htb[/htb]$ vim tmpfile
[Ctrl + Z]
[2]+  Stopped                 vim tmpfile
```

Now all background processes can be displayed with the following command.
```bash
fsiccatto@htb[/htb]$ jobs

[1]+  Stopped                 ping -c 10 www.hackthebox.eu
[2]+  Stopped                 vim tmpfile
```

The `[Ctrl] + Z` shortcut suspends the processes, and they will not be executed further. To keep it running in the background, we have to enter the command `bg` to put the process in the background.
```bash
fsiccatto@htb[/htb]$ bg

fsiccatto@htb[/htb]$ 
--- www.hackthebox.eu ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 113482ms

[ENTER]
[1]+  Exit 1                  ping -c 10 www.hackthebox.eu
```

Another option is to automatically set the process with an AND sign (`&`) at the end of the command.
```bash
fsiccatto@htb[/htb]$ ping -c 10 www.hackthebox.eu &

[1] 10825
PING www.hackthebox.eu (172.67.1.1) 56(84) bytes of data.
```

Once the process finishes, we will see the results.
```bash
fsiccatto@htb[/htb]$ 

--- www.hackthebox.eu ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9210ms

[ENTER]
[1]+  Exit 1                  ping -c 10 www.hackthebox.eu
```

---
### Foregground a Process
After that, we can use the `jobs` command to list all background processes. Backgrounded processes do not require user interaction, and we can use the same shell session without waiting until the process finishes first. Once the scan or process finishes its work, we will get notified by the terminal that the process is finished.
```bash
fsiccatto@htb[/htb]$ jobs

[1]+  Running                 ping -c 10 www.hackthebox.eu &
```

If we want to get the background process into the foreground and interact with it again, we can use the `fg <ID>` command.
```bash
fsiccatto@htb[/htb]$ fg 1
ping -c 10 www.hackthebox.eu

--- www.hackthebox.eu ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9206ms
```

---
### Execute Multiple Commands
There are three possibilities to run several commands, one after the other. These are separated by:

- Semicolon (`;`)
- Double `ampersand` characters (`&&`)
- Pipes (`|`)

The difference between them lies in the previous processes' treatment and depends on whether the previous process was completed successfully or with errors. The semicolon (`;`) is a command separator and executes the commands by ignoring previous commands' results and errors.

The semicolon (`;`) is a command separator and executes the commands by ignoring previous commands' results and errors.
```bash
fsiccatto@htb[/htb]$ echo '1'; echo '2'; echo '3'

1
2
3
```

 If we execute the same command but replace it in second place, the command `ls` with a file that does not exist, we get an error, and the third command will be executed nevertheless.
```bash
fsiccatto@htb[/htb]$ echo '1'; ls MISSING_FILE; echo '3'

1
ls: cannot access 'MISSING_FILE': No such file or directory
3
```
 
However, it looks different if we use the double AND characters (`&&`) to run the commands one after the other. If there is an error in one of the commands, the following ones will not be executed anymore, and the whole process will be stopped.
```bash
fsiccatto@htb[/htb]$ echo '1' && ls MISSING_FILE && echo '3'

1
ls: cannot access 'MISSING_FILE': No such file or directory
```

Pipes (`|`) depend not only on the correct and error-free operation of the previous processes but also on the previous processes' results.