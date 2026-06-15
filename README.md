# GLT SafePass
### Secure Children's Check-in System
**God's Love Tabernacle International Church · Lekki, Lagos**

---

## What is GLT SafePass?

GLT SafePass is a secure digital check-in and check-out system for the Children's Church at God's Love Tabernacle. It ensures every child can only be collected by an authorised parent or guardian using a unique one-time pickup code.

**Live app:** https://gltlekkichildrenchurchcheckin.vercel.app

---

## Features

- 🔐 **Secure check-in/out** with unique pickup codes (GLT-XXX-XXXX)
- 📱 **WhatsApp & SMS** code delivery to parents
- 🖨️ **Print slip** option for parents without smartphones
- 👨‍👩‍👧 **Parent profiles** with emergency contacts and authorised pickup persons
- 👶 **Child profiles** with medical alerts, medication, and feeding instructions
- 🩺 **Care instructions** visible to stewards at check-in
- 🎒 **Belongings log** at check-in, verified at pickup
- ⏱️ **Duration tracking** — how long each child has been inside
- 📊 **Live dashboard** with real-time headcount and class breakdown
- 📋 **Export reports** to CSV (Excel compatible)
- 👤 **Role-based access** — Super Admin, Admin, Steward
- 📱 **Mobile & tablet optimised** — works on any device
- 🌐 **Multi-device** — all devices share real-time data via Supabase

---

## Tech Stack

| Layer | Service | Cost |
|-------|---------|------|
| Frontend | Single HTML file | Free |
| Hosting | Vercel | Free |
| Database | Supabase (PostgreSQL) | Free |
| Delivery | WhatsApp deep links + SMS | Free |

**Monthly cost: ₦0**

---

## Project Structure

```
glt-safepass/
├── index.html              ← The entire app (single file)
├── README.md               ← This file
├── scripts/
│   ├── 01_reset_and_setup.sql   ← Run first: creates all tables
│   └── 02_v5_upgrade.sql        ← Upgrade script (if migrating)
└── docs/
    ├── SETUP_GUIDE.md           ← Step-by-step Supabase + Vercel setup
    └── USER_PLAYBOOK.md         ← Staff user guide
```

---

## Quick Setup

### 1. Database (Supabase)
1. Go to [supabase.com](https://supabase.com) and create a free project
2. Open **SQL Editor** and run `scripts/01_reset_and_setup.sql`
3. Go to **Settings → API Keys** and note your:
   - Project URL: `https://xxxxx.supabase.co`
   - Publishable key: `sb_publishable_ey...`

### 2. Deploy (Vercel)
1. Push this repository to GitHub
2. Go to [vercel.com](https://vercel.com) and import the GitHub repo
3. Deploy — Vercel will serve `index.html` automatically

### 3. First login
1. Open your Vercel URL
2. The app detects no accounts exist and shows **Super Admin Registration**
3. Fill in your details and create your Super Admin account
4. Go to **Admin tab** to create steward accounts for your team

---

## Auto-deploy (push to update)

Once connected to GitHub + Vercel:
1. Edit `index.html` locally (or in GitHub web editor)
2. Commit and push to the `main` branch
3. Vercel auto-deploys in ~30 seconds
4. All devices see the update immediately — no re-sharing links

---

## Supabase credentials

> ⚠️ The Supabase URL and publishable key are embedded in `index.html`.
> The publishable key is safe to expose — it's designed for browser use with Row Level Security enabled.
> Never embed your **secret key** (service role key) in the frontend.

---

## Database schema

```sql
stewards    — Staff accounts (name, username, password, role, phone, email)
parents     — Parent profiles (name, phone, whatsapp, email, emergency contacts)
children    — Child profiles (name, age, class, parent_id, medical notes)
sessions    — Check-in/out log (child_id, code, times, steward IDs, belongings)
```

---

## Export formats

From the Dashboard → Reports section:
- **Today's Attendance CSV** — full session log for the day
- **All Sessions CSV** — complete historical log
- **Children Register CSV** — all child and parent details
- **Parents Register CSV** — all parent profiles
- **Weekly Summary CSV** — attendance totals grouped by date

All CSV exports open directly in Microsoft Excel or Google Sheets.

---

## Roles

| Role | Access |
|------|--------|
| Super Admin | Full access, cannot be deleted |
| Admin | Manage children, parents, stewards |
| Steward | Check-in and check-out only |

---

## Support

Built and maintained by **Digital Masterpiece**
Zoho Authorised Partner · Lagos, Nigeria
contact@digitalmasterpiece.com

*God's Love Tabernacle International Church · Lekki, Lagos · glt.church*
