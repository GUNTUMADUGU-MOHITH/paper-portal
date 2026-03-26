# SBTET Question Paper Hub — C23 Scheme

A full-stack Flask web application for students to browse and download C23 scheme diploma question papers.

---

## 🚀 Setup & Run

### 1. Install dependencies
```bash
pip install -r requirements.txt
```

### 2. Run the app
```bash
python app.py
```

The app will start at **http://localhost:5000**

The database (`sbtet.db`) is created automatically with all subjects pre-loaded on first run.

---

## 📁 Project Structure

```
sbtet/
├── app.py                  # Flask backend
├── requirements.txt        # Python dependencies
├── sbtet.db                # SQLite database (auto-created)
├── templates/
│   ├── index.html          # Student home page
│   ├── papers.html         # Papers browsing page
│   ├── admin_login.html    # Admin login (hidden)
│   └── admin_dashboard.html # Admin panel
└── static/
    └── uploads/            # Uploaded PDF files (never deleted)
```

---

## 🔐 Admin Access

**Secret URL:** `http://localhost:5000/admin-0106-secret`

**Login Options:**
- Secret Code: `0106`
- Username: `admin` / Password: `sbtet@0106`

> ⚠️ This URL is completely hidden from the student-facing UI.

---

## 🎓 Student Features

- No login required
- Select Branch → Semester → Subject → Download
- Live search across subjects
- Quick semester filter buttons
- Download counter tracking
- Fully responsive UI

---

## 🌿 Branches & Semesters

**Branches:** CME, ECE, ME, CIVIL  
**Semesters:** 1 YEAR, 3 SEM, 4 SEM, 5 SEM

---

## 🛡️ Security Notes

- Files are **never deleted** from `/static/uploads/` — only DB records are removed
- Admin routes are protected by session authentication
- PDF-only file upload enforcement
- Files renamed with timestamps to prevent conflicts

---

## 🛠️ API Endpoints

| Method | Route | Description |
|--------|-------|-------------|
| GET | `/get-subjects?branch=&semester=` | Fetch subjects |
| POST | `/get-papers` | Fetch papers for a subject |
| GET | `/download/<id>` | Download + increment counter |
| POST | `/upload-paper` | Admin: upload PDF |
| POST | `/delete-paper` | Admin: remove from DB |
