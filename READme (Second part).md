# Report on Monitoring a Linux System

**Introduction:** Monitoring a Linux system is crucial for maintaining its health, stability, and performance. It involves observing various metrics and parameters to ensure that the system is operating efficiently and effectively. In this report, we will explore the main areas of concern when monitoring a system, methods for identifying memory-intensive processes, the significance of log files, techniques for tracking user activity, metrics for assessing system health and performance, methods for checking uptime, and ways to assess network traffic.

**Main Areas of Concern:** When monitoring a system, several key areas require attention:

1. CPU Load: Monitoring CPU utilization helps ensure that the processor isn't overburdened.
2. Memory Usage: Monitoring RAM usage is essential to prevent memory leaks and system slowdowns.
3. Disk Usage: Monitoring disk space ensures that there is sufficient storage available and helps prevent disk space-related issues.
4. Network Activity: Monitoring network traffic helps identify bottlenecks and potential security threats.
5. Process Activity: Monitoring running processes helps detect any anomalies or resource-intensive tasks.

---

**Identifying Memory-Intensive Processes:** To identify the most memory-intensive running processes, tools such as `top` or `htop` can be used. These tools provide real-time information about CPU and memory usage, allowing users to identify processes consuming the most memory.

I prefer htop since it use color and its more "friendly appareance" compared to top.
# **This is htop**

![[htop 1.png]]

	command used : 
	sudo apt update 
	sudo apt install htop
	 htop 

htop dont take argument but you can use shortcut in it to help you access the date you

1. **F1 or ?**: Opens the help screen, displaying a list of available keyboard shortcuts and their descriptions. (its like the 'man' of htop)
2. **F2**: Enters the setup menu, where you can configure various options such as display settings and columns shown. (to customize your environnement)
3. **F3**: Opens the search function, allowing you to search for processes by name. (to precise research by process name)
4. **F4**: Filters processes based on user-defined criteria. (kinda like F3 but for other metrics)
5. **F5**: Refreshes the `htop` display, updating process information.
6. **F6**: Allows you to select different sorting options for processes, such as CPU usage, memory usage, or process name.
7. **F7 and F8**: Decrease and increase the nice value (priority) of a selected process, respectively.
8. **F9**: Opens the kill process menu, where you can send signals to selected processes (e.g., terminate, kill, or send custom signals).
9. **F10 or q**: Exits `htop` and returns to the command prompt.


Now let's focus on the metric actually shown in htop to understand what are we looking and what to monitor 

![[bar.png]]

1. **PID (Process ID)**: This is the unique identifier assigned to each running process by the operating system. It is used to distinguish one process from another.
    
2. **USER**: This column displays the username or user ID associated with the process. It indicates the owner of the process.
    
3. **PRI (Priority):** The priority of the process, which determines its importance in the CPU scheduling algorithm. Lower values indicate higher priority. (RT = realtime , wich is the highest priority) . (On Unix/Linux, priorities are assigned on a scale generally ranging from -20 to 19).
    
4. **NI (Nice Value)**: The nice value of the process, which is used to influence its priority. Processes with a higher nice value are "nicer" to other processes, meaning they are lower in priority and may receive less CPU time.
    
5. **VIRT (Virtual Memory Size)**: The total virtual memory used by the process. This includes all code, data, and shared libraries, as well as memory that has been swapped out.
    
6. **RES (Resident Set Size)**: The amount of physical memory (RAM) used by the process. This represents the portion of memory that is currently in RAM and actively being used by the process.
    
7. **SHR (Shared Memory)**: The amount of shared memory used by the process. Shared memory is memory that can be accessed by multiple processes, often used for inter-process communication.

--- 

**Log Files:** Log files record important system events, errors, and activities. They are essential for troubleshooting issues, monitoring system health, and ensuring security. Log files are typically found in the `/var/log` directory on a Linux system.

there is many log in the directory  `/var/log` that is interesting to monitor depending on the problem you are troubleshooting.

For example, common log files found in `/var/log` include:

- `syslog`: Contains general system messages.
- `auth.log` or `secure`: Records authentication-related events, such as user logins and authentication failures.
- `messages`: Logs messages from various system processes and daemons.
- `kern.log`: Logs kernel-related messages.
- `apache2/access.log` and `apache2/error.log`: Logs related to the Apache web server, including access and error logs.
- `mysql/error.log`: Logs related to the MySQL database server.

So, if you're troubleshooting network-related issues, you might want to monitor logs such as `syslog` or `messages` for network-related errors or warnings. If you're troubleshooting web server issues, you might focus on logs such as Apache's `access.log` and `error.log`. If you're troubleshooting authentication problems, you might pay attention to `auth.log`

---

**Sysstat:** Sysstat primarily gathers performance data on various system resources such as CPU, memory, disk I/O, and network activity. It stores this data in log files, allowing users to analyze historical trends and identify potential performance bottlenecks or irregularities.

	sudo apt-get update 
	sudo apt-get install sysstat

1. Display CPU utilization statistics for the current day:

    `sar -u`

2. Display memory usage statistics:

    `sar -r`
   
3. Display disk I/O statistics:

    `sar -d`
   
4. Display network traffic statistics:

    `sar -n DEV`
  
5. Display process activity:

    `sar -q`

The data collected by `sar` is saved in daily files named `saXX`, where "XX" represents the day of the month. For example, `sa01` would be the file for the first day of the month, `sa02` for the second day, and so on. These files are binary files and can be read using `sar` itself or other tools like `sar -f` to specify a specific file.

	 example : sar -f /var/log/sa/sa09

---

**Nethogs**  : Nethogs is a command-line tool used for monitoring network traffic bandwidth usage in real-time on a Linux system. It provides a detailed breakdown of bandwidth usage by individual processes and helps administrators identify which processes are consuming network resources.

	sudo apt-get install nethogs
	sudo nethogs [options]

**Options:**

- `-d`: Delay in seconds between refreshes (default is 1 second).
- `-t`: Truncate long process names.
- `-v`: Verbose mode, which displays the full path of the process.
- `-h`: Display the help message with all available options.

To start Nethogs with the default settings, simply run:

	sudo nethogs

This will display a real-time list of processes and their respective bandwidth usage, sorted by the amount of data transferred.

---

Now lets do a report on my client machine : 

**System Monitoring Report**

_Date: [9-04-2024]_  
*Name of the device*: [library-client]_  
_Reported by: [Rios Falcon Pablo]_

---

**1. System Overview:**

- **Hostname:** [library-client]
- **Operating System:** [Ubuntu 22.04.4 LTS]
- **Kernel Version:** [linux 6.5.0-26 generic]
- **Architecture:** [x86_64]
- **Uptime:** [14:51:51 up 7 min, 1 user]
- **System Load:** [Load average for the last 1 min = 0.05 , 5 min = 0.18, and 15 min = 0.10]

cmd used : 

- `hostnamectl` (to see most of the system info)
- `uptime` (to see the uptime of the device)

**2. Resource Utilization:**

- **CPU Usage:** [1 - 5% ]
- **Memory Usage:** [790Mb/3.23Gb]
- **Disk Usage:** [56%]

cmd used : 

- `htop` (to see CPU and Mem usage)
- `df -h` (to see disk usage)

**3. Process Activity:**

- **Total Processes:** [108]
- **Running Processes:** [1 (htop)]
- **Top CPU Consuming Processes:**
    1. htop: [2%]
- **Top Memory Consuming Processes:**
    1. gnome-shell : [9.4 %]

cmd used : 

- `htop` 

**4. User Activity:**

- **Currently Logged-In Users:** [library :1]
- **Recent Logins:** [library | root]
- **Active Sessions:** [ library :1 tty1]

cmd used : 

- `w (to list currently logged in user)

**5. System Health and Alerts:**

- **System Health Status:** [None]
- **Disk Space Alerts:** [None]
- **CPU/Memory Alerts:** [None]

cmd used : 

- `htop`

**6. System Configuration:**

- **Kernel Parameters:** [too long to print but can be accessed with `sysctl -a`]
- **Filesystem Configuration:** [UUID=d391ea3e-9aa5-4def-9025-cf3b75ea6aad       /          ext4         errors=remount-ro 0         1]
- **Network Configuration:** [eth0 | ip : 172.24.38.136 | netmask : 255.255.240.0 | broadcast : 172.24.47.255 ]

cmd used : 

- `ifconfig`  
- `nano /etc/fstab  
- `sysctl -a`   