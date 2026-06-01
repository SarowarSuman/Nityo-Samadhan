<div align="center">

<img src="https://img.shields.io/badge/Status-Live-brightgreen?style=for-the-badge&logo=netlify" />
<img src="https://img.shields.io/badge/Firebase-Firestore-orange?style=for-the-badge&logo=firebase" />
<img src="https://img.shields.io/badge/Hosting-Netlify-00C7B7?style=for-the-badge&logo=netlify" />
<img src="https://img.shields.io/badge/Language-Bengali-blue?style=for-the-badge" />

<br/><br/>

# 🏘️ নিত্য সমাধান
### Community Service Directory

**"One person's experience becomes everyone's solution."**

[🌐 Live Demo](https://nityo-samadhan.netlify.app/) · [📋 Report Bug](https://github.com/SarowarSuman/nityo-samadhan/issues) · [💡 Request Feature](https://github.com/SarowarSuman/nityo-samadhan/issues)
</div>

---

## 🔥 The Problem

> Pipe burst at midnight. Electricity gone before an important exam. You need a technician urgently — but don't know who to call.

In rural Bangladesh, finding a trusted local service provider depends entirely on **word of mouth**. You call one neighbor, they call another, precious time is lost — sometimes in situations where time is everything.

**নিত্য সমাধান** digitizes that word of mouth. A crowdsourced, always-updated directory where residents contribute and everyone benefits.

---

## ✨ Features

| Feature | Description |
|--------|-------------|
| 📋 **9 Service Categories** | কারেন্ট মিস্ত্রী, রাজমিস্ত্রী, পানির মিস্ত্রী, মেডিকেল, পুলিশ, ফায়ার সার্ভিস & more |
| ⚡ **Real-time Sync** | Entries appear instantly across all devices — no refresh needed |
| 📞 **One-tap Call** | Direct phone call from any entry card |
| 🔒 **Admin Protection** | Only admin can delete entries — password protected |
| 📊 **Community Reporting** | 2 reports from different users = entry auto-hidden |
| 🚫 **Smart Filtering** | Bilingual profanity blacklist (Bengali + English) |
| 📱 **BD Phone Validation** | Only valid Bangladeshi formats accepted (017X, 018X, 019X...) |
| 🔤 **Quality Checks** | Blocks gibberish, keyboard smash & repeated characters |
| 📍 **Location Popup** | Area-specific notice discourages irrelevant entries |
| 🔍 **SEO Ready** | Sitemap submitted to Google Search Console |

---

## 🛠️ Tech Stack

### Why these specific choices — not just what, but why.

<table>
<tr>
<td width="33%" align="center">
<h3>⚡ Frontend</h3>
<b>HTML5 · CSS3 · Vanilla JS</b>
</td>
<td width="33%" align="center">
<h3>🔥 Database</h3>
<b>Firebase Firestore</b>
</td>
<td width="33%" align="center">
<h3>🚀 Hosting</h3>
<b>Netlify</b>
</td>
</tr>
</table>

### ⚡ Frontend — Pure HTML/CSS/JavaScript

Most developers default to React or Vue. I made a deliberate choice not to.

Bangladesh's rural internet is slow and inconsistent. A typical React app ships **200KB+** of JavaScript before rendering a single pixel. This app loads in **under 50KB** — fully functional within 1–2 seconds on 3G.

For a community service tool where someone might be in an emergency, **speed isn't a feature. It's a responsibility.**

Zero frameworks. Zero dependencies. Zero points of failure.

---

### 🔥 Backend & Database — Firebase Firestore

**Why not a custom backend (Node.js / PHP / Django)?**

A custom backend means:
- 💸 Paying for a server 24/7
- 🔧 Managing security patches manually
- 📉 Handling downtime and scaling yourself

For a free community tool, that's unsustainable.

**Why Firestore specifically over MongoDB, Supabase, or PlanetScale?**

All alternatives require a dedicated server layer. Firestore integrates **directly into the frontend** — true serverless, zero backend code.

```
User submits entry
       ↓
Firestore (WebSocket listener)
       ↓
All connected users see it instantly — no polling, no refresh
```

**Free tier capacity:**
| Metric | Daily Limit | Community Reality |
|--------|-------------|-------------------|
| Reads | 50,000/day | 500 users × 10 views = 5,000 |
| Writes | 20,000/day | ~50 new entries = 50 |
| Storage | 1 GB | Years of data |

This runs **free, indefinitely** for a community of this size.

---

### 🚀 Hosting — Netlify

**Why not cPanel, shared hosting, or a VPS?**

Traditional hosting = manual FTP uploads, SSL renewal headaches, single server location.

Netlify gives:
- 🌍 **Global CDN** — same load speed in Dhaka and Rajshahi
- 🔐 **Auto HTTPS** — no manual certificate management
- ⚡ **Deploy in seconds** — drag, drop, live
- 💰 **Completely free** — no hidden costs

---

## 🔐 Security Architecture

This isn't just a form that saves data. It's built **assuming people will try to misuse it.**

```
User Input
    │
    ├── ❌ Profanity Filter (Bengali + English blacklist)
    ├── ❌ Phone Validation (BD format regex)
    ├── ❌ Quality Check (gibberish, smash, repeated chars)
    ├── ❌ Duplicate Check (same number, same service)
    │
    ✅ Saved to Firestore
    │
    ├── Community can flag (2 flags = auto-hidden)
    └── Admin can permanently delete (password protected)
```

---

## 📁 Project Structure

```
nityo-samadhan/
│
├── index.html        # Entire application — frontend + Firebase logic
├── sitemap.xml       # For Google Search Console indexing
└── README.md         # You are here
```

**Single file architecture** — intentional. No build process, no node_modules, no CI/CD pipeline needed. Anyone can open it, read it, and understand the entire codebase in one sitting.

---

## 🚀 Run Locally

No installation. No npm install. No setup.

```bash
# Clone the repo
git clone https://github.com/yourusername/nityo-samadhan.git

# Open in browser
open index.html
```

> ⚠️ Firebase config is included for read access. To use your own Firestore instance, replace the `firebaseConfig` object in `index.html` with your own project credentials.

---

## 🎯 Target Area

> **Taherpur Municipality, Bagmara Upazila, Rajshahi District, Bangladesh**

Built specifically for this community — but the codebase is fully reusable for any locality. Fork it, replace the service categories and area text, and deploy in minutes.

---

## 📸 Screenshots

| Landing Page | Service Page | Admin Mode |
|-------------|-------------|------------|
| 9 service categories | Add & view entries | Delete protected |

---

## 🤝 Contributing

This project thrives on community. If you're from the area and want to contribute data, visit the live site. If you're a developer and want to fork this for your own locality:

1. Fork the repository
2. Replace `firebaseConfig` with your own Firebase project
3. Update service categories in the `services` array
4. Update area name in the popup HTML
5. Deploy to Netlify — free, 2 minutes

---

## 👤 Author

**Sarowar Suman**

[![Facebook](https://img.shields.io/badge/Facebook-1877F2?style=for-the-badge&logo=facebook&logoColor=white)](https://www.facebook.com/share/1REsHMSrZo/)

---

## 📄 License

MIT License — use it, fork it, build on it. Just don't forget where it came from. 🙌

---

<div align="center">

**Built with care for the people of Taherpur. 🏘️**

*"প্রতিবেশীর সাহায্যে প্রতিবেশী" — Neighbor helping neighbor.*

⭐ Star this repo if you think more localities deserve this tool!

</div>
