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

