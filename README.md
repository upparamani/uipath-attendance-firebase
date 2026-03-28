# 📋 UI Path Lab — Attendance System
### KLS Gogte Institute of Technology · ISE Department · 2025–26

> Serverless, real-time student attendance system for UI Path Lab sessions.
> Built for **Division A & B** · Hosted on GitHub Pages · Powered by Firebase Realtime Database.

---

## 🔗 Live URLs

| Role | URL |
|------|-----|
| 🎓 Student | `https://upparamani.github.io/UIPath-Attendance/` |
| 👩‍💻 Professor | `https://upparamani.github.io/UIPath-Attendance/?prof=1` |

---

## ✨ Features

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1faf9737-c454-43ee-8783-632bffc4d01a" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/db231174-e205-4c0e-a1e6-cc4ef087aacd" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/51338373-0c86-44a0-8eda-34464088337d" />


### 🎓 Student Side
- Select **Division A or B**
- Enter **USN** — name previews instantly
- Enter **4-digit session token** from the board
- One-click submit — permanent success screen after marking
- Blocks: wrong division, wrong token, invalid USN, duplicate submission

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/63dd628d-c14c-4f48-9887-7cf448aa09bb" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/db6957e6-1798-417c-be53-6934a110ef15" />

### 👩‍💻 Professor Side
- Password-protected dashboard (`?prof=1`)
- Select **Division**, **Date**, and **Period Time**
- **▶ Open** — starts session with a random 4-digit token
- **⏸ Pause** — freezes session (students cannot submit while paused)
- **▶ Resume** — resumes session
- **■ Close** — ends session and archives it
- **5-minute countdown timer** — auto-closes session at zero
- **Live Present / Absent / Total** stats updated instantly
- **Flash card** notification slides in from right when a student marks attendance
- **Status badge** — OPEN (green) / PAUSED (yellow) / CLOSED (grey)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/055567ab-73ac-4c7e-87f6-0dd0c73a4078" />

### 📥 Excel Export (KLS Format)
- Covers **all sessions** — each session = one column
- Up to **25 sessions** per export
- **Division filter** prompt if sessions span both divisions
- Column headers: `dd.mm.yyyy` + `h.mmam/pm` — rotated 90°
- Color-coded **P** (green) / **A** (red) per student per session
- **DAY TOTAL** row per session
- **Total attended** + **Attendance %** per student
- **Frozen panes** — header rows and SI/USN/Name columns stay fixed while scrolling
- Alternating row shading for readability
- Filename: `Attendance_UIPath_DivA_yyyy-mm-dd.xlsx`

### ⚡ Real-Time Updates
- Firebase Realtime Database — **no page refresh needed**
- Professor dashboard updates **instantly** when any student submits
- No polling — true push-based updates

---

## 🗂 File Structure

```
UIPath-Attendance/
├── index.html       ← Main app (all logic + UI)
├── students.js      ← Division A & B student lists
├── style.css        ← Base dark theme styles
└── README.md
```

---

## 🛠 Tech Stack

| Layer | Technology |
|-------|-----------|
| Hosting | GitHub Pages (free, static) |
| Database | Firebase Realtime Database |
| Frontend | Vanilla HTML + CSS + JavaScript |
| Fonts | Google Fonts — Sora + Space Mono |
| Excel | xlsx-js-style via CDN |

---

## 🔐 Professor Access

- Append `?prof=1` to the URL to reveal the Professor card on the home screen
- Dashboard is password protected — default password: `1111`
- Share the plain URL (without `?prof=1`) with students

---

## 📊 Data Structure (Firebase)

```json
{
  "attendance": {
    "sessions": [
      {
        "division": "A",
        "date": "2026-03-28",
        "period": "08:30",
        "token": 4172,
        "present": ["2GI23IS001", "2GI23IS006"],
        "times": { "2GI23IS001": "8:27:00 am" },
        "paused": false,
        "startTime": 1743150000000
      }
    ],
    "activeSession": null
  }
}
```

---

## 🚀 Setup (for new deployment)

1. **Firebase** — Create project → Enable Realtime Database → Set rules to `true/true`
2. **GitHub** — Create public repo → Enable Pages from `main` branch root
3. **Upload** — `index.html`, `students.js`, `style.css` to repo root
4. **Access** — Live in 1–2 minutes at your GitHub Pages URL

---

## 🔧 Admin Tool – Student List Generator (Built-in)

To simplify semester updates, this system includes a **built-in Excel → `students.js` generator**.

### 📌 Access

Open the system in professor mode:

```
https://your-link/index.html?prof=1
```

A floating **📂 button (bottom-right)** will appear.

Click it to open **Admin Tools → Students.js Generator**.

---

### 📥 How to Use

1. Obtain the official student list from office (Excel file)
2. Drag & drop the file into the generator panel
3. Select correct sheets for:

   * Division A
   * Division B
4. Click **✔ Process**
5. Click **⬇ Download students.js**
6. Replace the existing `students.js` file in the project

---

### ⚙️ What the Tool Handles Automatically

* Detects header row (even if not first row)
* Extracts **USN + Name**
* Removes duplicates
* Ignores empty / invalid rows
* Sorts students by USN
* Supports flexible Excel formats

---

### ⚠️ Important Notes

* Excel must contain columns with **“USN”** and **“Name”**
* Sheet1 → Division A, Sheet2 → Division B (default)
* Always verify student count before downloading
* Keep a backup of previous `students.js`

---

### 🎯 Benefits

* No coding required
* No Python / scripts needed
* Works directly in browser
* Reduces update time to **< 1 minute**

---

### 🔐 Visibility

This tool is:

* Available **only in professor mode**
* Hidden from students
* Does not affect attendance functionality

---

### 🚀 Recommended Workflow (Each Semester)

1. Get Excel from office
2. Open system → Admin Tool
3. Generate `students.js`
4. Replace file
5. Done

---

### 🧠 Future Improvements (Optional)

* Auto-download after processing
* Preview table before export
* Validation warnings (missing/duplicate entries)
* Integration with database (advanced use)

---


## 👨‍🏫 Maintained by

**Prof. Pandurang Upparamani**
Department of Information Science & Engineering
KLS Gogte Institute of Technology, Belagavi
