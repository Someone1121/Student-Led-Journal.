# Student-Led Journal

A student-run academic journal platform that uses AI-assisted evaluation to review research paper submissions before human publication. Students submit research papers, receive structured AI feedback, and high-quality submissions are flagged for editorial review and publication.

Built with **Next.js**, **Supabase**, **OpenAI (ChatGPT)**, and deployed on **Vercel**. Designed with **dark mode by default**.

---

## Features

### Research Paper Submission
Students can submit:
- Research paper content
- Paper title
- Author name
- School / institution
- Email address
- Abstract
- Field of study

All submissions are securely stored in Supabase.

---

### AI-Powered Evaluation
- Uses OpenAI’s cheapest viable ChatGPT model (configurable)
- Automatically evaluates submissions across:
  - Clarity
  - Argument strength
  - Structure
  - Evidence & citations
  - Originality
  - Writing quality
- Produces:
  - Overall score
  - Structured written feedback
  - Category-level strengths and weaknesses

---

### Student Feedback Dashboard
Students can view:
- AI-generated comments
- Visualized writing strengths (charts / bars / radar graphs)
- Submission status (Under Review, Needs Revision, Accepted)

---

### Editor Notification System
- Submissions exceeding a quality threshold trigger an email alert
- Editor reviews submissions manually before publication

---

### Publication System
- Approved papers are published on a separate public page
- Displays:
  - Title
  - Author
  - School
  - Abstract
  - Full paper content

---

### Real-Time Website Analytics
- Tracks total visits and active users
- Updates in real time using Supabase Realtime

---

### Dark Mode Interface
- Dark theme by default
- Minimal, academic-focused UI

---

## Tech Stack

- **Frontend:** Next.js (App Router)
- **Backend:** Supabase (PostgreSQL, Auth, Realtime)
- **AI:** OpenAI API (ChatGPT)
- **Email:** Resend / SMTP / Supabase Edge Functions
- **Deployment:** Vercel
- **Visualization:** Chart.js or Recharts

---

## Database Schema

### `submissions`
Stores all research paper submissions.

| Column | Type |
|------|------|
| id | uuid |
| title | text |
| author_name | text |
| school | text |
| email | text |
| abstract | text |
| paper_content | text |
| field_of_study | text |
| ai_score | numeric |
| ai_feedback | json |
| status | text |
| created_at | timestamp |

---

### `published_papers`
Stores editor-approved papers.

| Column | Type |
|------|------|
| id | uuid |
| submission_id | uuid |
| published_at | timestamp |

---

### `site_analytics`
Tracks real-time website usage.

| Column | Type |
|------|------|
| id | uuid |
| active_users | integer |
| total_visits | integer |
| updated_at | timestamp |

---

## Environment Variables

Create a `.env.local` file:

```env
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
SUPABASE_SERVICE_ROLE_KEY=

OPENAI_API_KEY=

EMAIL_FROM=
EDITOR_EMAIL=
