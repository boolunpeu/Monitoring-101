# Monitoring-101

**Monitoring tools enable you to:**
1.  Ensure the hardware is working (Hard drive, motherboard, cpu, ect.)
2. Uptime (mostly for online servers)
3. Sufficient resources are available (storage, memory, cpu,ect.)
4. Find wich bottlenecks are degrading perfomance (not enough storage, weak cpu, ect.)

Focus areas :
 1. Memory ( how much RAM is available)
 2. Enough disk space ? 
 3. How busy is the CPU 
 4. Input/Output 

## **Monitoring tools :** 

**Using nmap :** 

***what is Nmap ?** : Nmap (Network Mapper) is a widely-used open-source security scanning tool used to discover hosts and services on a computer network. It provides various scanning techniques to determine what hosts are available on the network, what services they are offering, and what operating systems they are running.*

**command used :**
- `nmap sS  `

![Capture](https://github.com/boolunpeu/Monitoring-101/assets/131985567/b192aa3b-2a85-48b8-b37a-1a6f39c3d3ce)

**Using Sysstat :** 

***what is Sysstat ?** : Sysstat is a collection of performance monitoring tools for Unix/Linux systems. It includes utilities like sar, iostat, mpstat, and pidstat, which provide detailed statistics on CPU, memory, disk I/O, and process activity. Sysstat helps system administrators monitor system performance and diagnose issues*.

**command used :**
- `sar -u 1 10 `

![sar](https://github.com/boolunpeu/Monitoring-101/assets/131985567/a727f6d7-8513-45d7-960f-7d1cc701dd3e)


**Using Vmstat :** 

***what is Vmstat ? :**(Virtual Memory Statistics) is a Unix/Linux command-line utility that provides real-time information about system memory, CPU usage, processes, and system I/O activity. It displays statistics on memory usage, paging, swapping, CPU utilization, and block I/O. `vmstat` is often used for monitoring system performance, diagnosing memory-related issues, and analyzing system behavior under different loads.

**command used :**
- `vmstat 1 `

![vmstat](https://github.com/boolunpeu/Monitoring-101/assets/131985567/b95f746b-7e99-420b-a6db-2110e84611ee)

---

**VMSTAT AND SYSSTAT DIFFERENCE ?** 
 vmstat is a simple, versatile tool focused on memory, I/O and CPU monitoring, while sysstat is a more comprehensive suite of system tools offering more advanced and detailed features for monitoring overall system performance.
 
---

**Using Nethogs :** 

***what is Nethogs ?** : Nethogs is a network monitoring tool for Linux that displays bandwidth usage per process. It provides real-time insights into which processes are using the network bandwidth, helping users identify bandwidth-hungry applications or processes.*

**command used :**
- `nethogs eth0 `

![nethogs](https://github.com/boolunpeu/Monitoring-101/assets/131985567/ad9bc8fd-657e-4c10-86f6-1798435b15d7)

(there is currently no activity on my bandwidth)


**Using Htop :** 

***what is Htop ?** :  htop is an interactive process viewer for Unix-like systems that provides a comprehensive and user-friendly interface for monitoring system resources. It displays information about CPU usage, memory utilization, swap space, and running processes in a hierarchical manner. With its customizable layout and color-coded display, htop offers advanced features such as scrolling, searching, and sorting processes, making it a powerful alternative to the traditional top command.*

**command used :**
- `htop `
  
![htop](https://github.com/boolunpeu/Monitoring-101/assets/131985567/c72bc32d-7c3d-4054-8fda-023c576d9818)

---

## Useful question :

- What are the main area of concern when monitoring a system? (EX: _CPU load_, _disk usage_, ...)

	`CPU`
	`Memory Usage`
	`Disk Usage`
	`Network Activity`
	`Security event`
	`App perfom`
	`System log`

- How can you check what are the most memory intensive [running processes](https://www.computerhope.com/jargon/p/process.htm) ?

	`htop or top`

- What are log files? Where can you fin them on a typical Linux system ?

	`/var/log`

- How can you check who where the last connected users, what they did, when they left ?

	`last` | to see who was the last user connected

	 `history` | to see what they did

	 `grep 'session closed' /var/log/auth.log` | to see when they left

- What are the different metrics of health and performance of a system ?

	`CPU`
	`Memory`
	`I/O (in/out)`
	`Swapd`
	`System`

- How can you check the uptime of a machine ?

	 `htop`

- How can you assess the network traffic ?

	 `nethogs eth0`


## EXTERNAL USEFULL RESSOURCES : 

https://tryhackme.com/r/room/linuxfilesystemanalysis

https://www.youtube.com/watch?v=AhW1ZvChFjs

https://www.youtube.com/watch?v=RrkDUbt3V6o&sttick=0
