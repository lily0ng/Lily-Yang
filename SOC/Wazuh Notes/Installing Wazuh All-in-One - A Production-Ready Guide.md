---
title: "Installing Wazuh All-in-One: A Production-Ready Guide"
source: "https://news.fmisec.com/04-installing-wazuh-all-in-one-a-production-ready-guide"
author:
  - "[[FPT Metrodata Indonesia]]"
published: 2025-11-14
created: 2025-12-13
description: "I've installed various security tools hundreds of times across different environments, and here's the thing: the installation is actually the easy part. The real challenge is configuring it properly for your specific use case and avoiding the common ..."
tags:
  - "clippings"
---
## 04\. Installing Wazuh All-in-One: A Production-Ready Guide![FPT Metrodata Indonesia's photo](https://cdn.hashnode.com/res/hashnode/image/upload/v1733298407203/c1f869b8-ec48-4bbc-a0fc-a87ef1e69e66.jpeg?w=200&h=200&fit=crop&crop=faces&w=500&h=500&fit=crop&crop=entropy&auto=compress,format&format=webp&auto=compress,format&format=webp)

FPT Metrodata Indonesia's photo

[FPT Metrodata Indonesia](https://hashnode.com/@fmisec)

·

11 min read

---

I've installed various security tools hundreds of times across different environments, and here's the thing: **the installation is actually the easy part**. The real challenge is configuring it properly for your specific use case and avoiding the common pitfalls that will bite you later.

In this guide, I'll walk you through not just how to install Wazuh All-in-One on Ubuntu 24.04 LTS, but also share the **hard-won lessons** from production deployments that will save you hours of troubleshooting (and probably some headaches).

**Why you should trust this guide:**

- Real production experience, not just lab testing
- I'll tell you about the mistakes I've made so you don't have to
- Performance considerations from day one (this matters more than you'd think)
- Troubleshooting tips for when things inevitably go wrong

---

### Step 1: VM Setup - Getting the Foundation Right

**Here's the thing:** Your VM specs will determine whether Wazuh runs smoothly or struggles. I've seen too many deployments fail because of inadequate resources, and honestly, it's frustrating to troubleshoot performance issues that could have been avoided.

**Here's what I recommend (based on real experience):**

**Minimum Specs (Lab/Testing):**

	- **vCPUs:** 4 cores (Wazuh is CPU-intensive, especially the analysis engine)
- **RAM:** 8GB (4GB for OS, 4GB for Wazuh components)
- **Disk:** 100GB SSD (60GB for OS, 40GB for logs and data)
- **Network:** Bridged adapter for external access

**Production Specs (Real Workloads):**

- **vCPUs:** 8+ cores (trust me on this)
- **RAM:** 16GB+ (8GB for indexer, 4GB for manager, 4GB for OS)
- **Disk:** 500GB+ SSD with separate data partition
- **Network:** Gigabit Ethernet (don't try to run this on 100Mbps)

**Why these specs matter (and why I'm being so specific):**

- **CPU:** The analysis engine (`wazuh-analysisd`) is single-threaded and CPU-bound (this is a common bottleneck)
- **RAM:** OpenSearch (indexer) needs significant memory for JVM heap (I've seen it crash with insufficient RAM)
- **Disk:** Log storage grows quickly; SSDs provide 10x better performance (this is not optional)
- **Network:** Agents send data continuously; poor network = data loss (and you won't know until it's too late)

**Pro tip:** Take a snapshot of your VM after the initial setup but before installing Wazuh. This saves hours if you need to start over (and trust me, you might need to start over).

### Step 2: Network Configuration - The Make or Break Moment

**Here's where many installations go wrong:** The firewall configuration. You have two options, and I'll explain both (and why I prefer one over the other):

**Option 1: Disable UFW (Quick & Dirty - Lab Only)**

```bash
# Disable UFW completely
sudo systemctl disable ufw
sudo systemctl stop ufw

# Verify it's stopped
sudo ufw status
```

**Option 2: Configure UFW Properly (Production Recommended)**

```bash
# Allow Wazuh ports
sudo ufw allow 1514/tcp    # Agent communication
sudo ufw allow 1515/tcp    # Agent communication (alternative)
sudo ufw allow 55000/tcp   # Wazuh API
sudo ufw allow 9200/tcp    # OpenSearch
sudo ufw allow 443/tcp     # Wazuh Dashboard (HTTPS)
sudo ufw allow 22/tcp      # SSH (if needed)

# Enable UFW
sudo ufw --force enable
```

**Why I recommend Option 2 for production:**

- Better security posture (this matters)
- Easier to troubleshoot network issues (you'll thank me later)
- Follows security best practices (your security team will appreciate this)
- Can be managed centrally (important for larger deployments)

**Network Troubleshooting Commands:**

```bash
# Check if ports are listening
sudo netstat -tlnp | grep -E ':(1514|1515|55000|9200|443)'

# Test connectivity from another machine
telnet YOUR_WAZUH_IP 1514

# Check firewall status
sudo ufw status verbose
```

**Common Network Issues I've Encountered (and how to avoid them):**

1. **Port conflicts:** Another service using port 1514 (this happens more often than you'd think)
2. **SELinux/AppArmor:** Blocking Wazuh processes (especially on RHEL/CentOS)
3. **Network policies:** Corporate firewalls blocking traffic (this is a pain to troubleshoot)
4. **DNS issues:** Hostname resolution problems (always use IP addresses for initial setup)

**Pro tip:** Always test network connectivity before proceeding. A failed installation due to network issues is frustrating and time-consuming (and I've seen it happen too many times).

---

### Step 3: Getting the Wazuh Installer - Version Matters

**Here's something important:** Always use the latest stable version. I've seen too many issues with outdated installers, and honestly, it's not worth the headache.

**Download the Installer:**

```bash
# Get the latest installer (always check for updates)
curl -sO https://packages.wazuh.com/4.12/wazuh-install.sh

# Verify the download
ls -la wazuh-install.sh
file wazuh-install.sh
```

**Make it Executable:**

```bash
chmod +x wazuh-install.sh
```

**Pre-Installation Checks:**

```bash
# Check available disk space (need at least 10GB free)
df -h

# Check available memory
free -h

# Verify internet connectivity
ping -c 3 packages.wazuh.com

# Check if any Wazuh processes are already running
ps aux | grep wazuh
```

**Common Download Issues:**

1. **Corporate proxy:** May block the download
2. **DNS resolution:** Check if [packages.wazuh.com](http://packages.wazuh.com/) resolves
3. **SSL certificates:** Some corporate environments have certificate issues
4. **Bandwidth:** Large download on slow connections

**Troubleshooting Download Problems:**

```bash
# If curl fails, try wget
wget https://packages.wazuh.com/4.12/wazuh-install.sh

# Check for proxy settings
echo $http_proxy
echo $https_proxy

# Test with verbose output
curl -v https://packages.wazuh.com/4.12/wazuh-install.sh
```

**Pro tip:** Always verify the installer checksum if you're in a high-security environment. Wazuh provides SHA256 checksums for verification (and honestly, it's a good practice even in lab environments).

---

### Step 4: Configuration File - The Heart of Your Deployment

**Here's where most people make mistakes:** The config file determines how Wazuh components communicate, and getting it wrong means starting over. I've seen this happen too many times.

**Download the Configuration Template:**

```bash
curl -sO https://packages.wazuh.com/4.12/config.yml
```

**Get Your Server's IP Address:**

```bash
# Find your server's IP
ip addr show | grep inet
# or
hostname -I
```

**Edit the Configuration File:**

```bash
nano config.yml
```

**Single-Node Configuration (All-in-One):**

```yaml
nodes:
  indexer:
    - name: node-1
      ip: "YOUR_VM_IP"  # Replace with your actual IP
      # For local testing, you can use "127.0.0.1"

  server:
    - name: wazuh-1
      ip: "YOUR_VM_IP"  # Same IP as indexer

  dashboard:
    - name: dashboard
      ip: "YOUR_VM_IP"  # Same IP as others
```

**Critical Configuration Tips (learn from my mistakes):**

1. **Use the same IP for all components** in single-node deployment (this is crucial)
2. **Don't use** [**localhost**](http://localhost/) - use the actual IP address (I've seen this cause issues)
3. **Verify the IP is correct** - wrong IP = failed installation (and you'll waste time troubleshooting)
4. **Save the file** - I've seen people forget to save changes (this is embarrassing but it happens)

**Advanced Configuration Options:**

```yaml
# For production environments, you might want to specify:
nodes:
  indexer:
    - name: node-1
      ip: "YOUR_VM_IP"
      # Optional: specify ports
      port: 9200

  server:
    - name: wazuh-1
      ip: "YOUR_VM_IP"
      # Optional: specify ports
      port: 1514

  dashboard:
    - name: dashboard
      ip: "YOUR_VM_IP"
      # Optional: specify ports
      port: 443
```

**Common Configuration Mistakes:**

1. **Wrong IP address** - Double-check your server's IP
2. **Mixed** [**localhost**](http://localhost/) **and IP** - Use consistent addressing
3. **Invalid YAML syntax** - Check indentation and quotes
4. **Missing quotes** - IP addresses should be in quotes

**Verification Commands:**

```bash
# Check if YAML is valid
python3 -c "import yaml; yaml.safe_load(open('config.yml'))"

# Verify IP is reachable
ping -c 1 YOUR_VM_IP

# Check if ports are available
netstat -tlnp | grep -E ':(9200|1514|443)'
```

**Pro tip:** Take a screenshot of your config file before proceeding. If the installation fails, you'll know exactly what you configured (and this has saved me hours of troubleshooting).

---

### Step 5: The Moment of Truth - Running the Installation

**Final Pre-Installation Checklist:**

```bash
# Verify everything is ready
echo "IP Address: $(hostname -I)"
echo "Disk Space: $(df -h / | tail -1)"
echo "Memory: $(free -h | grep Mem)"
echo "Config file exists: $(ls -la config.yml)"
```

**Launch the Installation:**

```bash
sudo ./wazuh-install.sh -a
```

**What the** `-a` flag does:

- Runs in **automatic mode** using your config.yml
- No interactive prompts (perfect for automation)
- Uses default settings for non-specified options

**This is where it gets interesting...**

**What Happens During Installation (5-15 minutes):**

1. **System Dependencies** - Installs Java, Python, and other requirements
2. **Wazuh Indexer** - Downloads and configures OpenSearch
3. **Wazuh Manager** - Installs the core analysis engine
4. **Wazuh Dashboard** - Sets up the web interface
5. **SSL Certificates** - Generates internal certificates for secure communication
6. **Service Configuration** - Configures systemd services
7. **Initial Setup** - Creates default users and configurations

**Monitoring the Installation:**

```bash
# In another terminal, monitor the installation
tail -f /var/log/wazuh-install.log

# Check system resources during installation
htop
```

**Common Installation Issues and Solutions:**

**Issue 1: Out of Disk Space**

```bash
# Check disk usage
df -h
# Clean up if needed
sudo apt clean
sudo apt autoremove
```

**Issue 2: Memory Issues**

```bash
# Check memory usage
free -h
# If needed, create swap space
sudo fallocate -l 2G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
```

**Issue 3: Network Timeout**

```bash
# Check internet connectivity
ping -c 3 packages.wazuh.com
# If behind corporate proxy, set proxy variables
export http_proxy=http://proxy.company.com:8080
export https_proxy=http://proxy.company.com:8080
```

**Issue 4: Permission Problems**

```bash
# Ensure you're running as root or with sudo
sudo -v
# Check file permissions
ls -la wazuh-install.sh
```

**What Success Looks Like:** When the installation completes successfully, you'll see:

- All services started and running (this is the good part)
- Default admin credentials displayed (write these down!)
- Dashboard accessible via HTTPS (you can finally see the interface)
- No error messages in the output (this is what we want to see)

**Post-Installation Verification:**

```bash
# Check if all services are running
sudo systemctl status wazuh-manager
sudo systemctl status wazuh-indexer
sudo systemctl status wazuh-dashboard

# Check if ports are listening
sudo netstat -tlnp | grep -E ':(1514|1515|55000|9200|443)'

# Test API connectivity
curl -k https://localhost:55000
```

**Pro tip:** If the installation fails, don't panic. Check the logs, fix the issue, and try again. I've never seen an installation that couldn't be fixed with proper troubleshooting (and I've seen some pretty messed up installations).

## Post-Installation: Verifying Your Success

**Congratulations!** You've just installed one of the most powerful open-source security platforms available. But here's the thing, installation is just the beginning. Let's verify everything is working correctly and set you up for success.

### What You've Actually Accomplished

**Your Wazuh deployment now includes:**

- **Wazuh Indexer** (Port 9200) - Your data warehouse powered by OpenSearch
	- **Storage capacity:** Depends on your disk space
	- **Search capability:** Full-text search across all security events
	- **Retention:** Configurable data retention policies
- **Wazuh Manager** (Ports 1514, 1515, 55000) - The brain of your security operations
	- **Agent capacity:** Can handle 1000+ agents (with proper resources)
	- **Rule processing:** Real-time analysis of security events
	- **API access:** RESTful API for integrations
- **Wazuh Dashboard** (Port 443) - Your security command center
	- **User interface:** Modern, responsive web interface
	- **Real-time monitoring:** Live security event visualization
	- **Customization:** Role-based dashboards and reports

### Verification Checklist

**Step 1: Check Service Status**

```bash
# All services should be running
sudo systemctl status wazuh-manager wazuh-indexer wazuh-dashboard

# Check if ports are listening
sudo netstat -tlnp | grep -E ':(1514|1515|55000|9200|443)'
```

**Step 2: Test API Connectivity**

```bash
# Test the Wazuh API
curl -k -u admin:Your_Password https://localhost:55000

# Test OpenSearch
curl -k https://localhost:9200
```

**Step 3: Access the Dashboard**

- Open your browser and navigate to [`https://YOUR_SERVER_IP:443`](https://your_server_ip/)
- Login with the credentials provided during installation
- You should see the Wazuh dashboard with default views

### Access Information

**Dashboard Access:**

- **URL:**[`https://YOUR_SERVER_IP:443`](https://your_server_ip/)
- **Username:**`admin`
- **Password:**`Your_Password` (from installation output)

**API Access:**

- **Base URL:**[`https://YOUR_SERVER_IP:55000`](https://your_server_ip:55000/)
- **Authentication:** Basic Auth or API Key
- **Documentation:** Available at `/api-docs`

**1\. Change Default Passwords**

```bash
# Change admin password
sudo /var/ossec/bin/manage_agents -a admin -p "NewSecurePassword"
```

**2\. Configure Log Retention**

```bash
# Edit indexer configuration
sudo nano /etc/wazuh-indexer/opensearch.yml
# Set appropriate retention policies
```

**3\. Set Up Monitoring**

```bash
# Monitor Wazuh health
sudo systemctl enable wazuh-manager
sudo systemctl enable wazuh-indexer
sudo systemctl enable wazuh-dashboard
```

### Common Post-Installation Issues

**Issue 1: Dashboard Not Accessible**

```bash
# Check if dashboard is running
sudo systemctl status wazuh-dashboard
# Check firewall rules
sudo ufw status
# Check SSL certificates
sudo ls -la /etc/wazuh-dashboard/opensearch_dashboards.yml
```

**Issue 2: High Memory Usage**

```bash
# Check memory usage
free -h
# Adjust JVM heap size if needed
sudo nano /etc/wazuh-indexer/jvm.options
```

**Issue 3: No Alerts Generated**

```bash
# Check if agents are connected
curl -k -u admin:Your_Password https://localhost:55000/agents
# Check rule processing
sudo tail -f /var/ossec/logs/alerts/alerts.json
```

### Performance Monitoring

**Monitor System Resources:**

```bash
# Check CPU usage
top -p $(pgrep wazuh-analysisd)

# Check memory usage
free -h

# Check disk usage
df -h /var/ossec/
```

**Monitor Wazuh Health:**

```bash
# Check agent connections
curl -k -u admin:Your_Password https://localhost:55000/agents

# Check rule processing
sudo tail -f /var/ossec/logs/alerts/alerts.json | head -20
```

### You're Ready for Production!

**What you've built:**

- A fully functional SIEM platform
- Real-time security monitoring capabilities
- Scalable architecture ready for growth
- Professional-grade security tooling

**Next steps:**

1. **Add your first agents** - Start monitoring your endpoints
2. **Configure custom rules** - Tailor detection to your environment
3. **Set up integrations** - Connect with other security tools
4. **Create dashboards** - Visualize your security posture

**Pro tip:** Don't try to do everything at once. Start with basic monitoring, then gradually add complexity as you become comfortable with the platform. Trust me on this, I've seen too many teams get overwhelmed trying to implement everything at once.

---

## What's Next?

Now that you have Wazuh running, it's time to put it to work. In the next chapter, we'll dive into **adding and managing agents** - the real workhorses that collect security data from your endpoints.

You'll learn:

- How to deploy agents on different operating systems
- Best practices for agent configuration
- Troubleshooting common agent issues
- Scaling your agent deployment

### Written by![FPT Metrodata Indonesia](https://news.fmisec.com/yH5BAEAAAAALAAAAAABAAEAAAIBRAA7)

FPT Metrodata Indonesia

## FPT Metrodata Indonesia

PT FPT Metrodata Indonesia (FMI) is a joint venture between FPT IS and Metrodata Electronics, focusing on providing Cybersecurity-as-a-Service—including SOC, managed security, professional services, consulting, and threat intelligence—to support Indonesia’s rapidly growing digital economy. FMI is expanding into AI and cloud GPU services to deliver innovative protection and solutions for enterprises. Learn more at https://fmisec.com.

### Published on

[![FPT Metrodata Indonesia Cyber Security](https://news.fmisec.com/yH5BAEAAAAALAAAAAABAAEAAAIBRAA7)

FPT Metrodata Indonesia Cyber Security

](https://news.fmisec.com/)

## FPT Metrodata Indonesia Cyber Security

FPT Metrodata Indonesia (FMI) provides news, analysis & guides on cybersecurity and threat intelligence for Indonesia & Vietnam. Visit https://news.fmisec.com. FMI: https://fmisec.com