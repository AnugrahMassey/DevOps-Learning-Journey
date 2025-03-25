# 🗓 Week 4 Detailed Notes: Networking & Security (Days 21-25)

Welcome to **Week 4** of your DevOps learning journey! This week, we will cover the fundamentals of **Networking and Security**. Networking is a core concept in DevOps for understanding how servers, applications, and users communicate. You'll also explore network security concepts like firewalls, SSH, and load balancers.

---

## ✅ **Day 21: Introduction to Networking**

### 📌 **What is Networking?**
- Networking refers to the interconnection of multiple devices for data exchange.
- It allows computers to share resources and communicate using established protocols.

### 📚 **Types of Networks:**
1. **LAN (Local Area Network)**: Limited to a small geographical area like an office.
2. **WAN (Wide Area Network)**: Connects networks over large areas, like the internet.
3. **MAN (Metropolitan Area Network)**: Covers a city or campus.

### 📡 **Essential Networking Components:**
- **Router:** Connects different networks.
- **Switch:** Connects devices within a network.
- **Firewall:** Ensures network security.
- **DNS Server:** Resolves domain names to IP addresses.

### 🧑‍💻 **Basic Networking Commands:**
- `ifconfig` or `ip a` - Display network interfaces and IP addresses.
- `ping <IP>` - Test connectivity to a device.
- `traceroute <IP>` - Trace the path packets take to reach a host.
- `nslookup <domain>` - Get IP from a domain.
- `curl <URL>` - Send HTTP requests to a server.

---

## ✅ **Day 22: TCP/IP Model and OSI Model**

### 📌 **TCP/IP Model Overview:**
- **Transmission Control Protocol/Internet Protocol (TCP/IP)** is the communication standard of the internet.
- It has 4 layers:
  1. **Application Layer** - HTTP, FTP, DNS
  2. **Transport Layer** - TCP, UDP
  3. **Internet Layer** - IP, ICMP
  4. **Network Access Layer** - Ethernet, Wi-Fi

### 📌 **OSI Model Overview:**
- **Open Systems Interconnection (OSI)** model has 7 layers:
  1. **Physical Layer** - Hardware like cables, switches.
  2. **Data Link Layer** - MAC addresses and Ethernet frames.
  3. **Network Layer** - IP addressing and routing.
  4. **Transport Layer** - Reliable data transmission.
  5. **Session Layer** - Manages sessions between applications.
  6. **Presentation Layer** - Data formatting and encryption.
  7. **Application Layer** - User interaction (HTTP, SMTP).

### 🧑‍💻 **Practical Commands:**
- `telnet <IP> <Port>` - Check connectivity at the transport layer.
- `tcpdump` - Capture network packets.
- `curl -I <URL>` - View HTTP headers.
- `wget <URL>` - Download files from servers.

---

## ✅ **Day 23: Firewalls and Network Security**

### 📌 **What is a Firewall?**
- A **Firewall** is a security device that monitors and controls network traffic.
- It applies rules to allow or block specific traffic.

### 📚 **Types of Firewalls:**
1. **Network Firewalls** - Protect entire networks.
2. **Host Firewalls** - Protect individual devices.
3. **Cloud Firewalls** - Managed by cloud providers like AWS, Azure, and GCP.

### 🧑‍💻 **Firewall Management Commands:**
- Using **UFW (Uncomplicated Firewall)**:
  ```bash
  sudo ufw enable
  sudo ufw allow 80/tcp
  sudo ufw status
  ```
- Using **iptables**:
  ```bash
  sudo iptables -L
  sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
  ```

---

## ✅ **Day 24: SSH (Secure Shell)**

### 📌 **What is SSH?**
- **SSH (Secure Shell)** is a secure network protocol for remote server management.
- It uses port **22** by default.

### 📚 **Key Concepts:**
- **Public and Private Keys** - Used for authentication.
- **Password Authentication** - Less secure.
- **SSH Agent** - Manages private keys.

### 🧑‍💻 **Common SSH Commands:**
- Connect to a remote server:
  ```bash
  ssh user@server_ip
  ```
- Generate SSH key pair:
  ```bash
  ssh-keygen -t rsa
  ```
- Copy key to server:
  ```bash
  ssh-copy-id user@server_ip
  ```
- Transfer files securely using SCP:
  ```bash
  scp file.txt user@server_ip:/path/to/destination
  ```

---

## ✅ **Day 25: DNS and Load Balancers**

### 📌 **What is DNS?**
- **Domain Name System (DNS)** translates domain names into IP addresses.
- **Example:** `www.google.com` → `142.250.72.46`

### 📚 **DNS Components:**
1. **Resolver:** Client-side query tool.
2. **Root Servers:** Direct requests to appropriate TLD servers.
3. **TLD Servers:** Handle domains like `.com`, `.org`.
4. **Authoritative DNS Servers:** Store actual IP address mappings.

### 🧑‍💻 **DNS Commands:**
- Get IP address of a domain:
  ```bash
  nslookup example.com
  dig example.com
  ```
- Test DNS resolution:
  ```bash
  host example.com
  ```

### 📌 **What is a Load Balancer?**
- A **Load Balancer** distributes incoming traffic across multiple servers to ensure reliability and performance.

### 📚 **Types of Load Balancers:**
1. **Layer 4 Load Balancer:** Operates at the Transport Layer using TCP or UDP.
2. **Layer 7 Load Balancer:** Operates at the Application Layer using HTTP or HTTPS.

### 🧑‍💻 **Common Load Balancer Tools:**
- **Nginx** - Acts as a reverse proxy and load balancer.
- **HAProxy** - Provides TCP and HTTP load balancing.

---

## 📊 **Weekly Summary**
- **Day 21:** Learned the basics of networking, types of networks, and essential commands.
- **Day 22:** Covered the TCP/IP and OSI models, explored how data flows through networks.
- **Day 23:** Gained insights into firewall management using UFW and iptables for network security.
- **Day 24:** Explored SSH for secure remote access, generated keys, and transferred files.
- **Day 25:** Understood DNS and Load Balancers, learning how domain names are resolved and how traffic is distributed.

You are now well-versed with the fundamentals of networking and security — a crucial part of DevOps! 🎉

Next week, you'll dive into **Docker Basics** to explore containerization and container management. 🚀

---

