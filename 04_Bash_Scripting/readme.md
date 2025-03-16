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

### **What Are Variables?**
A **variable** stores data that can be used later in the script.

#### **Declaring and Using Variables**
```bash
#!/bin/bash
name="DevOps Engineer"
echo "Welcome, $name!"
```
💡 **Explanation:**
- `name="DevOps Engineer"` → Assigns a value to `name`.
- `$name` → Retrieves and prints the variable value.

### **Taking User Input**
```bash
#!/bin/bash
read -p "Enter your name: " username
echo "Hello, $username!"
```
💡 **Explanation:**
- `read -p "Message" variable` → Prompts user for input.
- `$username` → Stores and prints user input.

### **Environment Variables**
```bash
echo "Home Directory: $HOME"
echo "Current Directory: $PWD"
echo "Shell Used: $SHELL"
```
💡 **Common Environment Variables:**
- `$HOME` → User’s home directory.
- `$PWD` → Current working directory.
- `$SHELL` → Shell type in use.

---

## **🔹 Day 17: Conditional Statements & Loops**

