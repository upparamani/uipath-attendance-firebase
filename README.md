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

### 🎓 Student Side
- Select **Division A or B**
- Enter **USN** — name previews instantly
- Enter **4-digit session token** from the board
- One-click submit — permanent success screen after marking
- Blocks: wrong division, wrong token, invalid USN, duplicate submission

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

## 👨‍🏫 Maintained by

**Prof. Pandurang Upparamani**
Department of Information Science & Engineering
KLS Gogte Institute of Technology, Belagavi
