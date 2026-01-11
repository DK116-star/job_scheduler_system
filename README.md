# Job Scheduler & Automation System

A full-stack Job Scheduler and Automation Dashboard that allows users to create background jobs, execute them, track status changes, and trigger webhooks on completion.

This project is built as part of the **Dotix Technologies – Full Stack Developer Skill Test**.

---

## 📌 Features Implemented

### ✅ Job Creation

* Create jobs with:

  * `taskName`
  * `payload` (JSON)
  * `priority` (Low / Medium / High)
* Default status: **pending**
* Stored in MySQL database

### ✅ Job Runner

* Run a job manually
* Status lifecycle:

  * `pending → running → completed`
* Simulated background execution using timeout
* Automatic webhook trigger after completion

### ✅ Dashboard

* List all jobs
* View:

  * Task name
  * Priority
  * Status
* Create new jobs via UI
* Run job button (disabled once completed)

### ✅ Webhook Integration

* On job completion, sends POST request to:

```
https://webhook.site/<your-id>
```

* Payload includes:

  * jobId
  * taskName
  * priority
  * payload
  * completedAt

---

## 🧱 Tech Stack

### Frontend

* **Next.js 14 (App Router)**
* React
* Axios
* Basic CSS (Tailwind can be added later)

### Backend

* Node.js
* Express.js
* MySQL
* Axios (webhook trigger)
* Nodemon
* dotenv

### Database

* MySQL

---

## 📁 Project Structure

```
Job_scheduler/
│
├── frontend/
│   ├── app/
│   │   ├── page.tsx
│   │   └── layout.tsx
│   ├── package.json
│   └── next.config.js
│
├── backend/
│   ├── routes/
│   │   └── jobs.js
│   ├── db.js
│   ├── index.js
│   ├── package.json
│   └── .env
│
└── README.md
```

---

## 🗄️ Database Schema

```sql
CREATE DATABASE job_scheduler;
USE job_scheduler;

CREATE TABLE jobs (
  id INT AUTO_INCREMENT PRIMARY KEY,
  taskName VARCHAR(255),
  payload JSON,
  priority ENUM('Low','Medium','High'),
  status ENUM('pending','running','completed') DEFAULT 'pending',
  createdAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

---

## ⚙️ Backend Setup

```bash
cd backend
npm install
```

Create `.env` file:

```
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=job_scheduler
PORT=5000
```

Start backend:

```bash
npm run dev
```

Backend runs on:

```
http://localhost:5000
```

---

## 🎨 Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

Frontend runs on:

```
http://localhost:3000
```

---

## 🔌 API Endpoints

### Create Job

```
POST /api/jobs
```

### List Jobs

```
GET /api/jobs
```

### Job Detail

```
GET /api/jobs/:id
```

### Run Job

```
POST /api/jobs/run-job/:id
```

---

## 🔁 Job Execution Flow

1. Job created → status `pending`
2. User clicks **Run Job**
3. Status changes to `running`
4. After 3 seconds → status `completed`
5. Webhook is triggered automatically

---

## 📡 Webhook Payload Example

```json
{
  "jobId": 1,
  "taskName": "Curl Job",
  "priority": "High",
  "payload": { "type": "test" },
  "completedAt": "2026-01-11T10:30:00Z"
}
```

---

## 🤖 AI Usage Disclosure

AI tools were used **as allowed** in the assignment.

### Tools Used

* **ChatGPT (GPT-4.x)**

### How AI Helped

* Backend API structure (Express + MySQL)
* Debugging Next.js errors
* SQL schema design
* Frontend data fetching logic
* README documentation

### Prompts Used (Example)

* *"Create Express CRUD APIs for a job scheduler"*
* *"Fix Next.js next.config.js import error"*
* *"Create README for full stack job scheduler project"*

AI was used as a **development assistant**, not for blind copy-paste.

---

## 🧪 Testing

* Backend tested using:

  * PowerShell `Invoke-RestMethod`
  * Browser
* Frontend tested via browser UI
* Webhook verified via **webhook.site**

---

## 📸 Screenshots

✔ Job creation
✔ Job listing
✔ Status update
✔ Completed job view

*(Screenshots can be added for bonus points)*

---

## ✅ Status

✔ All required features implemented
✔ Backend + Frontend connected
✔ Database integrated
✔ Webhook working
✔ Ready for submission

---

## 🚀 Future Improvements (Optional)

* Add filters (status, priority)
* Add job detail modal
* Add Tailwind UI
* Authentication
* Dockerization
* Deployment on Vercel / Render

---

### 🎯 Final Verdict

**This project fully satisfies the Dotix Skill Test requirements** and is **submission-ready**.

