## **📌 Week 3: Bash Scripting (Day 15-20)**
This week, we focused on **Bash scripting**, an essential skill for automating tasks in **DevOps**. Bash scripts help execute multiple commands in a sequence, making it easier to manage servers, automate deployments, and monitor system performance.

---

## **🔹 Day 15: Introduction to Bash Scripting**

### **What is Bash?**
- Bash (**Bourne Again Shell**) is a command-line interpreter used in **Linux**.
- A **Bash script** is a file that contains a set of commands executed in sequence.
- Scripts **automate** repetitive tasks such as file management, system monitoring, and deployment.

### **Why Use Bash Scripting in DevOps?**
✅ Automate server tasks  
✅ Schedule maintenance jobs  
✅ Manage user permissions and logs  
✅ Monitor system performance  

### **Creating Your First Bash Script**
1️⃣ Open a terminal and create a new file:
   ```bash
   nano hello.sh
   ```
2️⃣ Add the following code:
   ```bash
   #!/bin/bash
   echo "Hello, DevOps Engineer!"
   ```
3️⃣ Save and exit (`CTRL + X`, then `Y`, and press **Enter**).
4️⃣ Give execution permission:
   ```bash
   chmod +x hello.sh
   ```
5️⃣ Run the script:
   ```bash
   ./hello.sh
   ```
💡 **Explanation:**
- `#!/bin/bash` → Shebang, specifies that Bash should run the script.
- `echo` → Prints output to the terminal.
- `chmod +x` → Makes the script executable.

---

## **🔹 Day 16: Variables & User Input**
