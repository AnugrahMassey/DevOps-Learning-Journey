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
