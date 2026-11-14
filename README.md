# ضامن | Dhamin

**Real estate brokerage platform for Jeddah (individual sellers & buyers)**
**منصة وساطة عقارية في جدة تربط الأفراد بأمان وشفافية**

Live demo / النسخة التجريبية: https://dhamin.onrender.com/
(hosted on a free tier: the first load may take ~50 seconds / الاستضافة مجانية وقد يتأخر أول تحميل حوالي 50 ثانية)

Built as a team project for the *Software and Interface Design* course (CS379) at Yanbu Industrial College.
مشروع فريق لمقرر تصميم البرمجيات والواجهات (CS379) في كلية ينبع الصناعية.

---

## Features / المميزات

- Browse and filter property listings with image galleries / تصفح العقارات مع فلاتر ومعرض صور
- Post and manage your own listings (up to 5 per user) / نشر وإدارة إعلاناتك (حد أقصى 5)
- Deal room: step-by-step deal flow, in-deal chat, and an auto-generated contract / غرفة الصفقة: مراحل واضحة، محادثة، وعقد
- Auctions and an investment simulator / المزادات ومحاكي الاستثمار
- Favorites, messages, and support tickets / المفضلة والرسائل وتذاكر الدعم
- Personal dashboard with charts and an admin panel / لوحة تحكم بالرسوم البيانية ولوحة إدارة
- Built-in assistant widget (Gemini, optional) / مساعد ذكي مدمج (اختياري)
- Arabic and English, dark mode, adjustable font size / عربي وإنجليزي ودارك مود وتكبير الخط
- Server-side protection: rate limiting, input validation (zod), trusted-origin checks / حماية من السيرفر وحدود طلبات وفحص مدخلات

## Tech Stack / التقنيات

| Layer | Tools |
|---|---|
| Frontend | React, Vite, Tailwind CSS, TypeScript |
| Backend | Node.js, Hono, Better Auth |
| Database | SQLite with Drizzle ORM |
| Validation | zod |

Brand colors / الألوان: #39AB79 · #041C16 · #FFFFFF · #F3F5F5 · #000000

## Run locally / التشغيل على جهازك

1. Install Node.js (LTS) from nodejs.org
2. In the project folder run:

```bash
npm install
npm run setup      # creates .env with a secret + database tables
npm run db:seed    # optional: demo users, properties and deals
npm run dev        # starts the server (:3000) and the UI (:5173)
```

Open http://localhost:5173

Demo accounts (password Demo@12345): khalid@demo.dhamin.test, sara@demo.dhamin.test, abdullah@demo.dhamin.test

## Useful commands / أوامر مهمة

| Command | Purpose |
|---|---|
| npm run dev | Development (server + UI) |
| npm run build | Build the UI into dist |
| npm start | Production: syncs tables, then serves the app |
| npm run db:push | Apply changes from server/db/schema.js |
| npm run db:studio | Browse the data (Drizzle Studio) |
| npm run db:seed -- --reset | Rebuild demo data |
| node scripts/smoke-test.js | Automated API test |

## Structure / الهيكل

```
server/    backend: server.js, auth.js, routes/ (API), db/schema.js, lib/
src/       frontend: pages/, components/, providers/, lib/api.ts
public/    static images and brand files
scripts/   setup.js, seed.js, smoke-test.js
data/      database and uploads (not pushed to GitHub)
```

## Deployment / النشر

Deploy from GitHub to Render or Railway. Build: npm install && npm run build. Start: npm start.
Environment variables: BETTER_AUTH_SECRET (random, 32+ chars), BETTER_AUTH_URL (your site URL), DATABASE_URL, UPLOAD_DIR, and optionally GEMINI_API_KEY. Attach a persistent volume if you need data to survive restarts.

## Docs / التوثيق

- GUIDE.md: full walkthrough, especially the backend (Arabic)
- server/API.md: API reference
