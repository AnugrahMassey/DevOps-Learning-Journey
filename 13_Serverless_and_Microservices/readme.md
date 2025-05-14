## 📅 **Week 14: Serverless & Microservices (Days 71–75)**

This week, you're diving into two powerful modern software architecture paradigms: **Serverless Computing** and **Microservices**. These are widely used in scalable, event-driven, cloud-native applications.

---

### ✅ **Day 71: Introduction to Serverless Computing**

#### 🔹 What is Serverless?

Serverless is a cloud-native development model that allows you to build and run applications without managing servers. The cloud provider automatically handles the infrastructure, scaling, and maintenance.

#### 🔹 Benefits:

* No server management
* Auto-scaling
* Pay-per-use
* Quick deployment

#### 🔹 Key Serverless Providers:

* **AWS Lambda**
* **Google Cloud Functions**
* **Azure Functions**

#### 🔹 Common Use Cases:

* Event-driven tasks (e.g., file uploads, database triggers)
* Real-time notifications
* Webhooks & APIs
* Automation scripts

---

### ✅ **Day 72: Understanding AWS Lambda**

#### 🔹 What is AWS Lambda?

AWS Lambda lets you run code without provisioning or managing servers. You write your logic, and AWS handles the rest.

#### 🔹 Core Concepts:

* **Function** – The code you want to run.
* **Event Source** – What triggers the function (e.g., S3, API Gateway).
* **Execution Role** – IAM permissions to execute actions (like reading from S3).

#### 🔹 Example Use Case:

1. A file is uploaded to S3.
2. S3 triggers a Lambda function.
3. The function processes the file (e.g., image resizing, parsing).

#### 🔹 Hello World Example:

```python
def lambda_handler(event, context):
    return {
        'statusCode': 200,
        'body': 'Hello from Lambda!'
    }
```

> You can write Lambda functions in Python, Node.js, Go, Java, etc.

---

### ✅ **Day 73: API Gateway + Lambda (Building Serverless APIs)**

#### 🔹 What is API Gateway?

A fully managed service to create, publish, and manage RESTful APIs that can trigger Lambda functions.

#### 🔹 Why Use It?

* Connect your Lambda functions to the web.
* Handle request/response transformations.
* Add security via API keys, rate limiting, etc.

#### 🔹 Workflow:

1. Create Lambda function.
2. Create API Gateway and configure routes.
3. Connect routes to Lambda.
4. Deploy API → You get a public endpoint (URL).

#### 🔹 Example Use Case:

* Build a REST API with CRUD functionality backed by Lambda and DynamoDB.

---

### ✅ **Day 74: Introduction to Microservices Architecture**

#### 🔹 What are Microservices?

A design approach where applications are composed of small, independent services that communicate over APIs.

#### 🔹 Characteristics:

* Single Responsibility Principle (each service does one thing)
* Independent deployment
* Lightweight communication (e.g., REST, gRPC, message queues)

#### 🔹 Benefits:

* Scalability
* Faster development
* Better fault isolation
* Easier to adopt new tech per service

#### 🔹 Challenges:

* Complexity in communication
* Monitoring & logging across services
* Deployment orchestration

---

### ✅ **Day 75: Building a Microservices Project (Conceptual)**
