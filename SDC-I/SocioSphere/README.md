# 🌐 Sociosphere

**Sociosphere** is a full‑stack social networking platform designed to deliver a modern, scalable, and performance‑optimized user experience. It enables users to connect, share posts, exchange messages, manage stories, and explore trending content in real time.

Built with a modular Node.js backend and a responsive frontend, Sociosphere is optimized for production‑ready deployments and cloud scalability.

---

## 🚀 Features

* 🔐 User Authentication & Authorization (JWT)
* 📝 Create, Edit, Delete Posts
* 💬 Real‑Time Messaging System
* 📸 Stories Management
* 🔔 Notifications
* 🏆 Leaderboard System
* 🧭 Explore Feed
* 📁 Media Upload Support
* 📊 Performance Monitoring
* 🧠 AI Integrations (Hugging Face)
* ✉️ Email Services

---

## 🛠️ Tech Stack

### Backend

* Node.js
* Express.js
* MongoDB
* JWT Authentication
* Twilio (OTP Services)
* Hugging Face API

### Frontend

* HTML
* CSS
* JavaScript

### Dev Tools

* Git & GitHub
* Postman
* VS Code

---

## 📁 Project Structure

```
Sociosphere
├── backend
│   ├── middleware
│   ├── models
│   ├── routes
│   ├── utils
│   ├── server.js
│   └── .env.example
├── frontend
│   ├── assets
│   ├── admin.html
│   └── index.html
└── README.md
```

---

## ⚙️ Installation & Setup

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/your-username/sociosphere.git
cd sociosphere
```

### 2️⃣ Backend Setup

```bash
cd backend
npm install
```

Create a `.env` file in the `backend` folder using `.env.example`:

```env
PORT=5000
MONGO_URI=your_mongodb_uri
JWT_SECRET=your_jwt_secret
OPENAI_API_KEY=your_openai_key
TWILIO_ACCOUNT_SID=your_twilio_sid
TWILIO_AUTH_TOKEN=your_twilio_token
HF_TOKEN=your_huggingface_token
```

Start Backend Server:

```bash
npm start
```

### 3️⃣ Frontend Setup

Open `frontend/index.html` in your browser or run using a local server.

---

## 📡 API Endpoints (Sample)

| Method | Endpoint           | Description       |
| ------ | ------------------ | ----------------- |
| POST   | /api/auth/login    | User Login        |
| POST   | /api/auth/register | User Registration |
| GET    | /api/posts         | Get All Posts     |
| POST   | /api/messages      | Send Message      |
| GET    | /api/notifications | Get Notifications |

---

## 📄 License

This project is licensed under the MIT License.

---

## 👨‍💻 Author

**Akhilesh Somari**
GitHub: [https://github.com/sakhilesh1907](https://github.com/sakhilesh1907)

---

> ⭐ If you like this project, consider giving it a star!
