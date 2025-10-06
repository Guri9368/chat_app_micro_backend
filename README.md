# 💬 ChatSync – Real-Time Microservices Chat App

🚀 **Microservices | MERN Stack | WebSockets | Redis | RabbitMQ | Docker | AWS EC2 | PM2**

A **real-time chat application** built using a **microservices architecture**, enabling scalable and reliable communication between users. ChatSync supports **instant messaging, typing indicators, media sharing**, and **OTP-based authentication** — all powered by a distributed system of **independent services**.

---

## 👨‍💻 Developer

**Name:** Gurmeet Singh Rathor  
**Email:** [gurigurmeet1234567@gmail.com](mailto:gurigurmeet1234567@gmail.com)

---

## 🧩 Project Overview

ChatSync is a **production-grade chat application** designed with **modular microservices**, ensuring **high scalability**, **fault tolerance**, and **maintainability**.  
It consists of three core services communicating asynchronously through **RabbitMQ** and maintaining **state synchronization** using **Redis**.

---

## 🏗️ Microservices Architecture

### 🔹 1. User Service
- Handles **user registration, login, and authentication** via **JWT tokens**.  
- Implements **OTP verification** through the Mail service (via RabbitMQ).  
- Uses **Redis** for efficient **session management** and **token caching**.

### 🔹 2. Chat Service
- Manages **real-time messaging** using **Socket.IO** and **WebSockets**.  
- Features:
  - Typing indicators  
  - Online/offline status tracking  
  - Message delivery acknowledgments  
  - Media sharing via **Multer** + **Cloudinary**

### 🔹 3. Mail Service
- Handles **email delivery and OTP verification** using **Nodemailer**.  
- Listens to **RabbitMQ queues** for OTP message requests from the User service.

---

## 🧱 Tech Stack

| Layer | Technologies |
|-------|---------------|
| **Frontend** | React.js, Tailwind CSS |
| **Backend Framework** | Node.js, Express.js |
| **Database** | MongoDB (Mongoose ORM) |
| **Cache & Session** | Redis |
| **Message Broker** | RabbitMQ (Dockerized) |
| **Storage** | Cloudinary (for media uploads) |
| **Realtime Communication** | Socket.IO, WebSockets |
| **Deployment** | AWS EC2, PM2 |
| **Containerization** | Docker |
| **Version Control** | Git, GitHub |

---

## ⚙️ Features

✅ **Real-time Chatting** using WebSockets & Socket.IO  
✅ **Typing Indicators** and **Online Status Tracking**  
✅ **JWT Authentication** and **Redis Session Management**  
✅ **Media Uploads** (images, videos, files) via Multer + Cloudinary  
✅ **OTP Email Verification** (RabbitMQ + Nodemailer)  
✅ **Microservices Communication** via **Dockerized RabbitMQ**  
✅ **PM2 Process Management** on **AWS EC2 Deployment**  

---

## 🏗️ System Architecture Diagram

```text
              ┌────────────────────────┐
              │      Frontend (React)  │
              └────────────┬───────────┘
                           │ REST / WS
           ┌───────────────┴────────────────┐
           │          API Gateway (Express) │
           └───────────────┬────────────────┘
                           │
    ┌──────────────────────┼─────────────────────────┐
    │                      │                         │
┌────────────┐       ┌────────────┐           ┌────────────┐
│ User       │<----->│ Chat       │<--------->│ Mail       │
│ Service    │       │ Service    │           │ Service    │
└────────────┘       └────────────┘           └────────────┘
     │                     │                        │
     │ JWT + Redis         │ Socket.IO + MongoDB    │ Nodemailer
     │                     │                        │
     └────────── RabbitMQ Message Queue ─────────────┘
🧰 Installation Guide
1️⃣ Clone the Repository
bash
Copy code
git clone https://github.com/<your-username>/ChatSync.git
cd ChatSync
2️⃣ Setup Environment Variables
Create a .env file in each service folder (user-service, chat-service, mail-service) with the following:

📦 User Service .env
ini
Copy code
PORT=5001
MONGO_URI=mongodb+srv://<your-db-uri>
JWT_SECRET=<your-jwt-secret>
REDIS_URL=redis://localhost:6379
RABBITMQ_URL=amqp://localhost
CLOUDINARY_CLOUD_NAME=<your-cloudinary-name>
CLOUDINARY_API_KEY=<your-api-key>
CLOUDINARY_API_SECRET=<your-api-secret>
💬 Chat Service .env
ini
Copy code
PORT=5002
MONGO_URI=mongodb+srv://<your-db-uri>
REDIS_URL=redis://localhost:6379
RABBITMQ_URL=amqp://localhost
CLOUDINARY_CLOUD_NAME=<your-cloudinary-name>
CLOUDINARY_API_KEY=<your-api-key>
CLOUDINARY_API_SECRET=<your-api-secret>
📧 Mail Service .env
ini
Copy code
PORT=5003
RABBITMQ_URL=amqp://localhost
EMAIL_USER=<your-email>
EMAIL_PASS=<your-app-password>
🐳 Dockerized RabbitMQ Setup
bash
Copy code
docker run -d --hostname my-rabbit --name rabbitmq \
-p 5672:5672 -p 15672:15672 rabbitmq:3-management
RabbitMQ Dashboard → http://localhost:15672
Default credentials → guest / guest

▶️ Running the Services
Start all services individually:
bash
Copy code
cd user-service && npm install && npm start
cd chat-service && npm install && npm start
cd mail-service && npm install && npm start
Or use PM2 for process management:

bash
Copy code
pm2 start ecosystem.config.js
pm2 save
pm2 startup
☁️ Deployment (AWS EC2)
SSH into your EC2 instance

Pull your codebase from GitHub

Install dependencies and start services using PM2

Configure NGINX reverse proxy for routing between services

Use sudo certbot for SSL (optional for HTTPS)

🔒 Authentication Flow
User registers → User Service generates OTP

OTP request sent to Mail Service via RabbitMQ

Mail Service sends OTP using Nodemailer

User verifies OTP → JWT issued and stored in Redis for session tracking

Real-time session active through WebSockets

🧪 Testing
To test locally:

Start RabbitMQ and Redis using Docker

Run each service (npm start)

Open multiple frontend clients and verify real-time updates, message delivery, and email OTP flow.

📸 Screenshots (Optional)
You can add demo images or GIFs here later:

Chat UI

Message Delivery

RabbitMQ Queue Dashboard

AWS EC2 Deployment Screenshot

🧠 Future Enhancements
 End-to-end encryption for private chats

 Group chat and channel creation

 Read receipts & message reactions

 Push notifications (Web & Mobile)

 CI/CD integration (GitHub Actions + AWS)

🤝 Contributing
Pull requests are welcome!
If you find bugs or have suggestions, open an issue or submit a PR.

🪪 License
This project is licensed under the MIT License.
Feel free to use and modify for educational or commercial purposes.

🌐 Live Demo & GitHub
🔗 Live Demo: Deployed on AWS EC2 (PM2 Managed)
💻 GitHub Repository: ChatSync – Real-Time Microservices Chat App

Built with ❤️ by Gurmeet Singh Rathor

yaml
Copy code

---
