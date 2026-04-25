# BuildTrack CMS

A simple, bilingual (EN/FR) customer management system built for a small construction business that was still running on paper.

---

## The Story

A friend of a friend runs a small construction company in the Gatineau/Ottawa area. They've been managing everything on paper — customer contacts, job details, follow-ups, the works. Binders full of handwritten notes, phone numbers on sticky notes, project statuses kept in their head.

They wanted something simple to keep track of their customers and deal with day-to-day operations — nothing fancy, no enterprise software with 200 features they'd never touch. Just a clean system where they can:

- Look up a customer's info quickly
- See what jobs are ongoing, done, or on hold
- Jot down notes and follow-ups
- Print a report when they need one

So we built **BuildTrack CMS** — a lightweight, no-nonsense customer management tool designed specifically for their workflow. It's bilingual (French and English) because that's the reality of doing business in the Outaouais region.

## What It Does

- **Customer directory** — Personal clients and companies, with contact info, address, tax ID (NEQ), and a work description field
- **Project tracking** — Link jobs to customers with statuses: ongoing, completed, on hold, cancelled
- **Notes & follow-ups** — Timestamped notes per customer to keep track of calls, decisions, and next steps
- **Search & filter** — Find customers fast by name, phone, email, or company. Filter by type and status
- **Print reports** — Generate a clean, print-friendly customer report with all their info, projects, and notes
- **CSV export** — Export the full customer list to a spreadsheet
- **Bilingual UI** — Toggle between French and English at any time
- **Dark mode** — Because why not

## Tech Stack

| Layer | Tech | Why |
|---|---|---|
| Frontend | React 19 + TypeScript | Modern, maintainable, component-based |
| Build tool | Vite 8 | Fast dev server and builds |
| Styling | Tailwind CSS + shadcn/ui | Clean UI without writing tons of CSS |
| Data | localStorage | No server needed — data stays in the browser |
| Hosting | None required | Runs locally or deploy free on Vercel/Netlify |

## Getting Started

### Prerequisites

- Node.js 20+ installed
- pnpm (recommended) or npm

### Install & Run

```bash
# Clone or unzip the project
cd BuildTrack_CMS

# Install dependencies
pnpm install

# Start the dev server
pnpm dev
```

The app opens at `http://localhost:5173`. That's it — no database setup, no environment variables, no config files to edit.

### Build for Production

```bash
pnpm build
```

The output goes to `dist/` — static files you can drop on any hosting provider or open directly.

## Project Structure

```
src/
├── App.tsx          # Main app — all views (dashboard, customers, detail, settings)
├── i18n.ts          # All EN/FR translations
├── types.ts         # Data models (Customer, Project, Note) + helpers
├── store.ts         # localStorage persistence, sample data, CSV export
├── index.css        # Tailwind directives + print styles
├── main.tsx         # React entry point
└── components/ui/   # shadcn/ui component library
```

## Key Design Decisions

**Why localStorage and not a real database?**
The client is one person. They don't need multi-user access, cloud sync, or an account system right now. localStorage means zero hosting cost, zero maintenance, and their data never leaves their computer. If they outgrow this, we can plug in Supabase (Postgres + auth) without rewriting the app.

**Why bilingual?**
The business operates in Gatineau, QC. Clients speak French and English. The default language is French.

**Why are the forms "placeholders"?**
The client has their own paper forms with specific fields. We built a generic version first to get them started — the fields can be swapped to match their exact forms once they decide what they want.

**Why no login/auth?**
It's a single-user system for now. The data model supports admin and sub-admin roles so we can add authentication later when needed.

## Roadmap

Things we might add depending on what the client needs:

- [ ] **Supabase integration** — Real database, authentication, multi-device access
- [ ] **Sub-admin accounts** — Let employees access the system with limited permissions
- [ ] **Desktop app** — Electron or Tauri version that runs offline as a native app
- [ ] **File attachments** — Photos of job sites, signed contracts, receipts
- [ ] **Invoice generation** — Basic invoice/quote PDF generation
- [ ] **Custom form builder** — Let the client configure their own form fields
- [ ] **Calendar view** — See project timelines and follow-up dates on a calendar

## Deployment (Free Options)

If the client wants to access this from their phone or multiple devices:

1. **Vercel** (recommended) — `pnpm build`, drag the `dist/` folder to vercel.com. Free tier is more than enough.
2. **Netlify** — Same process, drag and drop deploy.
3. **GitHub Pages** — Free static hosting if the repo is on GitHub.

Note: With localStorage, data is per-browser. To share data across devices, we'd need to add Supabase or another backend.

## License

Private project — built for a specific client. Not open source (yet).

---

Built with care for a real business that needed a real solution, not another subscription.
