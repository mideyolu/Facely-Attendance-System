# 🧑‍💻 FacelyV1 — Facial Recognition Attendance System

![Status](https://img.shields.io/badge/Status-Active-success)
![Version](https://img.shields.io/badge/Version-1.0.0-blue)
![License](https://img.shields.io/badge/License-MIT-green)

---

## 📖 Project Overview

**FacelyV1** is an advanced, AI-driven application designed to automate user enrollment and daily attendance tracking using real-time facial recognition. Built with a fast, decoupled architecture, it leverages deep learning models to seamlessly identify users via webcam feeds and log attendance in real time.

### 🎯 Purpose

To provide organizations, schools, and event organizers with a **touchless, highly accurate, and scalable** solution for managing attendance—eliminating manual data entry and reliance on legacy hardware such as fingerprint scanners.

---

## 🛠 Tech Stack

### Frontend

- **React.js (Vite)** – High-performance UI rendering  
- **React Router** – Client-side routing  
- **Custom Hooks** – `useCamera`, `useFaceLoop`, `useFaceModel`, `useLive`  
- **CSS3** – Responsive and modern styling  

### Backend

- **FastAPI** – Asynchronous Python web framework  
- **Uvicorn** – ASGI server  
- **Pydantic** – Data validation and schema definitions  

### AI / Machine Learning

- **FaceNet512 (ONNX Runtime)** – 512D face embeddings  
- **MediaPipe** – High-precision face detection  
- **FAISS** – Fast vector similarity search  
- **OpenCV** – Image preprocessing  

### Database

- **CSV (Flat-file storage)** – Lightweight persistence using `pandas`  

---

## 📂 Project Structure

```text
.
├── app/
│   ├── backend/
│   │   ├── data/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── services/
│   │   ├── config.py
│   │   ├── db.py
│   │   ├── main.py
│   │   ├── modelconfig.py
│   │   └── requirements.txt
│   └── frontend/
│       ├── public/
│       ├── src/
│       │   ├── components/
│       │   ├── hooks/
│       │   ├── services/
│       │   ├── App.jsx
│       │   └── main.jsx
│       ├── package.json
│       └── vite.config.js
```

---

## ✨ Features

- Automated user enrollment via webcam  
- Real-time facial recognition  
- Duplicate attendance prevention  
- Interactive analytics dashboard  
- High-speed FAISS-powered inference  

---

## 🔄 System Workflow

1. User opens the frontend and camera initializes  
2. Frames are captured and encoded as base64  
3. Data is sent to backend APIs  
4. Backend pipeline:
   - OpenCV preprocessing  
   - MediaPipe face detection  
   - FaceNet embedding generation  
5. FAISS performs similarity search  
6. Attendance is logged if threshold is met  
7. UI updates instantly  

---

## 🚀 Installation & Setup

### 1. Clone Repository

```bash
git clone https://github.com/mideyolu/Facely-Attendance-System.git
cd Attendance-System
```

### 2. Backend

```bash
cd app/backend
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

pip install -r requirements.txt

uvicorn main:app --reload
```

### 3. Frontend

```bash
cd app/frontend
npm install
npm run dev
```

---

## 📡 API Endpoints

| Method | Endpoint            | Description              |
|--------|-------------------|--------------------------|
| POST   | /enroll           | Register user            |
| POST   | /attendance       | Recognize & mark         |
| GET    | /enroll/stats     | Enrollment analytics     |
| GET    | /attendance/stats | Attendance analytics     |

---

## 🗄 Database

- **enrollments.csv** → user data + embeddings  
- **attendance.csv** → attendance logs  

---

## 🧠 AI Details

- Face embeddings: **FaceNet512 (ONNX)**  
- Search engine: **FAISS (IndexFlatIP)**  
- Metric: **Cosine Similarity (via L2 normalization)**  

---

## 🔐 Authentication

Currently **not implemented**.  
Recommended: JWT + Role-Based Access Control (RBAC).

---

## 🌍 Deployment

### Backend

```bash
gunicorn main:app -w 4 -k uvicorn.workers.UvicornWorker
```

### Frontend

```bash
npm run build
```

---

## ⚙️ Environment Variables

```env
VITE_API_URL=http://localhost:8000
```

---

## 📸 Screenshots

| Dashboard |
|----------|
| ![](onboarding.png) |
| ![](enroll-dashboard.png) |
| ![](attendance-dashboard.png) |

---

## 🛡️ Liveness Detection

### Challenges

| Challenge | Metric | Threshold |
|----------|--------|----------|
| Blink | EAR | < 0.19 |
| Mouth | MAR | > 0.35 |
| Head Left | Yaw | > 0.015 |
| Head Right | Yaw | < -0.015 |

---

## 🔮 Future Improvements

- Move to PostgreSQL / vector DB  
- Add deep learning anti-spoofing  
- Implement authentication (JWT)  
- Improve low-light accuracy  
- Add mobile apps  
- Dockerize system  

---

## 👥 Contributors

- **Donatus Valentine** – Group Leader  
- **Oluwuyi Olumide** – Tech Lead  
- **Ahmad El-Hussein**

**Others:**
- Ademola  
- Sa'ad Abdul  

---

## 🙏 Acknowledgments

This project was supported by:

- **:contentReference[oaicite:0]{index=0} (NCAIR)**  
- Under **:contentReference[oaicite:1]{index=1} (NITDA)**  

### Facilitators

| Role | Name |
|------|------|
| Lead Facilitator | **:contentReference[oaicite:2]{index=2}** |
| Supporting Facilitator | **:contentReference[oaicite:3]{index=3}** |
| Supporting Facilitator | **:contentReference[oaicite:4]{index=4}** |

---

## 📜 License

Licensed under the **MIT License**
