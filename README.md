\# 🚀 Microservices Containerization Project

\---

\#\# 📌 Overview

This project demonstrates how to containerize a Node.js-based microservices application using Docker and Docker Compose.

The application consists of:

\- ✅ User Service → Port 3000 

\- ✅ Product Service → Port 3001 

\- ✅ Gateway Service → Port 3003 

\---

\#\# 🧱 Project Structure

submission/ ├── user-service/ │ ├── Dockerfile │ └── app.js ├── product-service/ │ ├── Dockerfile │ └── app.js ├── gateway-service/ │ ├── Dockerfile │ └── app.js ├── docker-compose.yaml └── README.md

```

---

## 🧠 Application Flow

```

Client (Browser / curl) ↓ Gateway Service (Port 3003\) ↓ ┌───────────────┬───────────────┐ ↓ ↓ User Service Product Service (Port 3000\) (Port 3001\)

![][image1]

```

### 🔁 Flow Explanation

1. User sends request to Gateway  
2. Gateway routes request:
   - `/api/users` → User Service  
   - `/api/products` → Product Service  
3. Backend services process request  
4. Gateway returns response to user  

✅ Communication happens via Docker network using service names:
```

http://user-service:3000 http://product-service:3001

````

---

## ⚙️ Prerequisites

- Docker
- Docker Compose

---

## 🐳 Install Docker (if not installed)

### ✅ Ubuntu

```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
````

Verify:

Shell  
docker \--version  
Show more lines  
---

### **✅ macOS (Homebrew)**

Shell  
brew install \--cask docker  
Show more lines

Then start Docker Desktop.

---

## **🧰 Install Docker Compose**

### **✅ Ubuntu**

Shell  
sudo apt install docker-compose \-y  
Show more lines

Verify:

Shell  
docker-compose \--version  
Show more lines  
---

## **🚀 Setup Instructions**

1. Clone the repository:

Shell  
git clone https://github.com/\<your-username\>/Microservices-Task.git  
cd submission  
Show more lines

![][image2]

1. Build and start all services:

Shell  
docker-compose up \--build  
Show more lines

![][image3]  
---

## **✅ Verify Running Containers**

Shell  
docker ps  
Show more lines

You should see:

* user-service ✅  
* product-service ✅  
* gateway-service ✅

![][image4]  
---

## **🌐 Access Services**

### **Direct Access:**

* User Service:  
   [http://localhost:3000/users](http://localhost:3000/users)

![][image5]

* Product Service:  
   http://localhost:3001/products

![][image6]

---

### **Gateway Access (Main Entry Point):**

* Users API:  
   [http://localhost:3003/api/users](http://localhost:3003/api/users)

![][image7]

* Products API:  
   http://localhost:3003/api/products

![][image8]

---

## **🧪 Testing**

### **✅ Using curl**

Shell  
\# User Service  
curl http://localhost:3000/users

\# Product Service  
curl http://localhost:3001/products

\# Gateway Service  
curl http://localhost:3003/api/users  
curl http://localhost:3003/api/products  
Show more lines

![][image9]  
---

## **🛠 Troubleshooting**

### **❌ Containers not starting**

Shell  
docker-compose logs  
Show more lines  
---

### **❌ Restart services**

Shell  
docker-compose down  
docker-compose up \--build  
Show more lines  
---

### **❌ Port already in use**

Shell  
sudo lsof \-i :3000  
kill \-9 \<PID\>  
Show more lines  
---

### **❌ Docker not running**

Shell  
sudo systemctl start docker  
Show more lines  
---

## **⚡ Docker Best Practices Used**

* ✅ Lightweight base image (`node:18-alpine`)  
* ✅ Production dependencies only  
* ✅ Optimized layer caching  
* ✅ Service-to-service communication using Docker networking  
* ✅ Clean and modular service structure

---

## **⚠️ Challenges Faced**

### **1\. npm SSL Certificate Issue**

* Error: `UNABLE_TO_GET_ISSUER_CERT_LOCALLY`  
* ✅ Solution:  
  * Installed `ca-certificates`  
  * Disabled strict SSL temporarily

---

### **2\. npm ci Failure**

* Error: Requires `package-lock.json`  
* ✅ Solution:  
  * Replaced with:

```
npm install --omit=dev
```

---

### **3\. Service Communication Failure**

* Issue: Using `localhost` between containers  
* ✅ Solution:  
  * Used service names:

```
http://user-service:3000
```

---

### **4\. Missing Routes (Cannot GET /)**

* Issue: Root route not defined  
* ✅ Solution:  
  * Added `/` endpoint for better testing

---

### **5\. Port Conflicts**

* Issue: Services not starting due to port usage  
* ✅ Solution:  
  * Verified and freed ports

---

## **✅ Conclusion**

* Successfully containerized Node.js microservices  
* Used Docker Compose for orchestration  
* Enabled inter-service communication  
* Verified all services via API endpoints

---

## **📝 Author**

Shagun Maheshwari
