# DevOps Task 7 – Monitor System Resources with Netdata

## 🎯 Objective
Install **Netdata** using Docker and visualize real-time system and application performance metrics.

## ⚙️ Setup Environment
- **OS/Host**: Ubuntu 22.04 VM  
- **Tools Used**: Docker, Netdata (Dockerized)  
- **Access**: `http://<VM_IP>:19999`  

## 🚀 Steps Followed
1. Pulled and ran Netdata container:
   ```bash
   docker run -d --name netdata \
     -p 19999:19999 \
     -v netdata_lib:/var/lib/netdata \
     -v netdata_cache:/var/cache/netdata \
     -v /etc/passwd:/host/etc/passwd:ro \
     -v /etc/group:/host/etc/group:ro \
     -v /proc:/host/proc:ro \
     -v /sys:/host/sys:ro \
     -v /etc/os-release:/host/etc/os-release:ro \
     -v /var/run/docker.sock:/var/run/docker.sock:ro \
     --cap-add SYS_PTRACE \
     --security-opt apparmor=unconfined \
     --restart unless-stopped \
     netdata/netdata
Verified container status using:


docker ps
Opened the Netdata dashboard at http://<VM_IP>:19999.

Explored CPU, Memory, Disk I/O, Network, Processes, and Docker metrics.

Captured screenshots for proof of implementation.

# 📸 Project Screenshots

![CPU](CPU.png)  
![Containers & VMS](containers%20&%20VMS.png)  
![Dashboard](dashboard.png)  
![Disk](disk.png)  
![Docker](docker.png)  
![Memory](memory.png)  
![Network](network.png)  
![Storage](storage.png)  


📊 Key Learnings
Netdata provides real-time, lightweight monitoring with minimal setup.

It automatically detects system and Docker metrics without manual configuration.

Useful KPIs in DevOps:

CPU utilization & load average

Memory usage & swap activity

Disk I/O performance

Network latency, errors, bandwidth

Container health & resource usage

❓ Interview Prep (Q&A)
1. What does Netdata monitor?
👉 CPU, RAM, disk I/O, network, processes, and container metrics in real time.

2. How do you view real-time metrics?
👉 By accessing the Netdata web UI at http://<host>:19999.

3. How is Netdata different from Prometheus?
👉 Netdata = real-time, auto-generated dashboards, lightweight.
👉 Prometheus = time-series DB, needs exporters + Grafana for visualization.

4. What is a collector?
👉 A Netdata plugin that gathers specific metrics (CPU, Docker, MySQL, etc.).

5. Important performance KPIs to watch?
👉 CPU %, memory usage, load average, disk I/O, network errors, container health.

6. How to deploy Netdata on a VM?
👉 Either using Docker (docker run) or native install script on Linux.

7. How does Netdata alerting work?
👉 Comes with built-in alarms (warning/critical) and supports notifications (Slack, Email, etc.).

8. What is a dashboard in this context?
👉 A graphical UI in Netdata showing real-time charts of metrics.

✅ Conclusion
Successfully deployed Netdata, monitored key system and Docker metrics, and documented the findings with screenshots.
This demonstrates the ability to set up lightweight real-time monitoring for servers and applications in a DevOps environment.


---
