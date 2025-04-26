# **📌 Week 11: Monitoring & Logging (Day 56-60)**  
This week, you'll focus on **monitoring infrastructure performance** and **logging system activity** using **Prometheus, Grafana, and the ELK Stack (Elasticsearch, Logstash, and Kibana)**.

By the end of this week, you’ll understand:  
✅ **Why monitoring and logging are essential in DevOps**  
✅ **How to use Prometheus to collect and analyze system metrics**  
✅ **How to visualize metrics using Grafana dashboards**  
✅ **How the ELK stack is used for centralized logging**  

---

# **🗓️ Day 56: Introduction to Monitoring & Logging**  

### **🔹 What is Monitoring in DevOps?**  
Monitoring is the process of **tracking system performance, resource usage, and errors** to ensure reliability and efficiency.

### **🔹 Why Monitoring is Important?**  
✅ Detects performance bottlenecks  
✅ Helps troubleshoot issues before failures occur  
✅ Improves system reliability and uptime  

### **🔹 Types of Monitoring in DevOps**  
| **Type** | **Description** | **Example Tools** |
|----------|---------------|------------------|
| **Infrastructure Monitoring** | Tracks CPU, RAM, disk, and network usage | Prometheus, Datadog |
| **Application Monitoring** | Monitors application health and performance | New Relic, AppDynamics |
| **Log Monitoring** | Collects and analyzes log files | ELK Stack, Splunk |
| **Alerting** | Notifies teams of issues | Grafana, PagerDuty |

### **🔹 What is Logging?**  
Logging is the **process of capturing system and application events** to analyze errors and performance.

### **🔹 Key Differences Between Monitoring & Logging**  
| **Feature** | **Monitoring** | **Logging** |
|------------|--------------|------------|
| **Purpose** | Tracks system health | Records detailed events |
| **Data Type** | Metrics (CPU, RAM, Requests/sec) | Logs (text, errors, access logs) |
| **Tools** | Prometheus, Grafana | ELK, Splunk |

---

# **🗓️ Day 57: Setting Up Prometheus for Monitoring**  

### **🔹 What is Prometheus?**  
Prometheus is an **open-source monitoring system** used for collecting, storing, and analyzing metrics.

### **🔹 Installing Prometheus**  
#### **On Ubuntu/Linux:**
```bash
sudo useradd --no-create-home --shell /bin/false prometheus
sudo mkdir /etc/prometheus /var/lib/prometheus
wget https://github.com/prometheus/prometheus/releases/latest/download/prometheus-linux-amd64.tar.gz
tar xvf prometheus-linux-amd64.tar.gz
sudo mv prometheus-linux-amd64/prometheus /usr/local/bin/
sudo mv prometheus-linux-amd64/promtool /usr/local/bin/
```

### **🔹 Configuring Prometheus**
Create a configuration file `/etc/prometheus/prometheus.yml`:
```yaml
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'node_exporter'
    static_configs:
      - targets: ['localhost:9100']
```
Start Prometheus:
```bash
prometheus --config.file=/etc/prometheus/prometheus.yml
```

### **🔹 Accessing Prometheus Dashboard**  
Open **`http://localhost:9090`** in a browser to view metrics.

---

# **🗓️ Day 58: Visualizing Metrics with Grafana**  
