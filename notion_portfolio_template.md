# 🖥️ IT Professional Portfolio — Notion Template

> **How to use this:** Duplicate this page in Notion. Each section below becomes a Notion page or database. Use the Database views (Table, Board, Gallery) to filter and track your portfolio content.

---

## 📁 DATABASE 1 — Projects & Labs

**Create as:** Full-page Database (Table view)

### Properties (columns to add):

| Property | Type | Options / Notes |
|---|---|---|
| Title | Title | Name of project or lab |
| Type | Select | Work Project · Home Lab · Open Source · Freelance |
| Status | Select | In Progress · Complete · Paused |
| Year | Number | e.g. 2024 |
| Domain | Multi-select | Networking · Cloud · Security · Systems · Automation · Scripting |
| Technologies | Multi-select | Add as you go |
| Business Impact | Text | One-line quantified outcome |
| Time Invested | Number | Hours |
| Visibility | Select | Public (on portfolio site) · Private |
| Related Cert | Relation | Link to Certifications DB |
| GitHub Link | URL | Link to repo |
| Write-up | Files & Media | Upload PDF or link to Notion sub-page |

---

### 📄 Project Entry Template (sub-page)

When you click into a project, this is the page structure to follow:

---

**PROJECT TITLE**
`Type:` Work Project | Home Lab | Freelance
`Status:` Complete
`Year:` 2024
`Domain(s):` Networking · Security

---

#### 🔍 The Problem
*What was broken, missing, inefficient, or risky? Be specific.*

> Write 2–4 sentences describing the situation before you stepped in. What was the business impact of the problem? Who was affected?

---

#### 🛠️ What I Built / Did
*What exactly did you design, deploy, configure, automate, or fix?*

> Describe your approach and the technical solution. Be specific about tools, scale, and methodology. Avoid generic language — "I set up a server" is weak; "I deployed a Windows Server 2022 DC with AD DS, DNS, and DHCP, joined to a /24 subnet serving 80 workstations" is strong.

---

#### ⚙️ Technologies Used
- Tool / Platform 1 — how you used it
- Tool / Platform 2 — how you used it
- Tool / Platform 3 — how you used it

---

#### 📊 Business Impact (Quantified)
> This is the most important section. Always try to put a number on your work.

| Metric | Before | After | Change |
|---|---|---|---|
| e.g. Patch cycle time | 3 weeks | 48 hours | ↓ 83% |
| e.g. Helpdesk tickets | 45/month | 12/month | ↓ 73% |
| e.g. Engineering hours saved | 0 | 10 hrs/month | +10 hrs |

**Summary statement:**
> _One or two sentences summarising the impact in plain English for non-technical stakeholders._

---

#### 🧠 What I Learned
- Insight 1
- Insight 2
- What I would do differently next time

---

#### 📎 Artefacts
- [ ] Architecture diagram
- [ ] Script / config files (link to GitHub)
- [ ] Screenshots
- [ ] Write-up / blog post

---

---

## 📁 DATABASE 2 — Certifications Tracker

**Create as:** Full-page Database (Table view)

### Properties:

| Property | Type | Options / Notes |
|---|---|---|
| Certification | Title | Full cert name |
| Issuer | Select | CompTIA · Microsoft · Cisco · AWS · ISC2 · Other |
| Status | Select | Earned · In Progress · Planned |
| Date Earned | Date | |
| Expiry Date | Date | |
| Exam Code | Text | e.g. AZ-104 |
| Score | Number | If available |
| Study Hours | Number | Total hours invested |
| Study Resources | Text | Courses, books, labs used |
| Credential URL | URL | Credly, Acclaim, or cert verify link |
| Target Date | Date | If not yet earned |
| Related Projects | Relation | Link to Projects DB |

---

## 📁 DATABASE 3 — Skills Inventory

**Create as:** Full-page Database (Table view)

### Properties:

| Property | Type | Options / Notes |
|---|---|---|
| Skill | Title | e.g. PowerShell, Cisco IOS, Azure AD |
| Category | Select | Networking · Cloud · Security · Systems · Scripting · Tools |
| Proficiency | Select | Beginner · Intermediate · Advanced · Expert |
| Years Used | Number | |
| Used Professionally | Checkbox | |
| Last Used | Date | |
| Demonstrated In | Relation | Link to Projects DB |
| Notes | Text | Context or self-assessment |

---

## 📁 DATABASE 4 — Work Impact Log

**Create as:** Full-page Database (Timeline or Table view)

> Use this to track every time you make a measurable difference at work — even small things. This feeds directly into your CV and portfolio.

### Properties:

| Property | Type | Options / Notes |
|---|---|---|
| Title | Title | Short description of what you did |
| Date | Date | When it happened |
| Category | Select | Automation · Security · Infrastructure · Process · Cost saving · Uptime |
| Quantified Impact | Text | e.g. "Saved 4 hrs/week", "Reduced incidents by 30%" |
| Tools Used | Multi-select | |
| Stakeholders | Text | Who benefited (team, dept, whole company) |
| Added to CV | Checkbox | |
| Added to Portfolio | Checkbox | |

---

## 📁 DATABASE 5 — Learning Log

**Create as:** Full-page Database (Table view)

> Track courses, books, labs, videos, and practice exams — everything you're learning, even informally.

### Properties:

| Property | Type | Options / Notes |
|---|---|---|
| Resource | Title | Course or book name |
| Type | Select | Course · Book · Lab · YouTube · Documentation · CTF |
| Platform | Select | Udemy · TryHackMe · Microsoft Learn · CBT Nuggets · YouTube · Other |
| Topic | Multi-select | |
| Status | Select | Not started · In Progress · Complete |
| Start Date | Date | |
| Complete Date | Date | |
| Rating | Select | ⭐ · ⭐⭐ · ⭐⭐⭐ · ⭐⭐⭐⭐ · ⭐⭐⭐⭐⭐ |
| Related Cert | Relation | Link to Certifications DB |
| Notes | Text | Key takeaways |

---

## 🗂️ VIEWS TO SET UP

Once your databases are built, create these views:

**Projects DB views:**
- `All Projects` — Table, sorted by Year desc
- `Work Projects` — Filter: Type = Work Project
- `Home Labs` — Filter: Type = Home Lab
- `Public Portfolio` — Filter: Visibility = Public
- `By Domain` — Group by: Domain

**Certifications DB views:**
- `Active Certs` — Filter: Status = Earned, sorted by Expiry
- `Study Pipeline` — Filter: Status = In Progress or Planned
- `Expiring Soon` — Filter: Expiry within 6 months

**Learning Log views:**
- `Currently Studying` — Filter: Status = In Progress
- `Completed` — Filter: Status = Complete, sorted by Complete Date
- `By Platform` — Group by: Platform

---

## 📋 WEEKLY REVIEW CHECKLIST

*Pin this to your Notion sidebar. Check it every Friday.*

- [ ] Did I complete or make progress on any project? → Log it
- [ ] Did I solve a problem at work that had measurable impact? → Add to Work Impact Log
- [ ] Did I learn something new (course, lab, article)? → Add to Learning Log
- [ ] Is any certification expiring in the next 3 months? → Schedule renewal
- [ ] Is anything ready to add to the public GitHub portfolio site? → Update index.html

---

## 🎯 PORTFOLIO GOALS TRACKER

| Goal | Target Date | Status |
|---|---|---|
| Complete Security+ | Q2 2025 | 🟡 In Progress |
| Add 2 more lab write-ups | Q1 2025 | 🟡 In Progress |
| Publish portfolio site | Jan 2025 | ✅ Done |
| Reach 5 public projects | Q3 2025 | ⬜ Not started |
| Earn AZ-305 | Q4 2025 | ⬜ Not started |

---

*Last updated: 2025 — keep this living document current.*
