# Sample Project Write-Up
### Format guide for your IT portfolio

Use this as the template for every project and lab you document.
The annotations in [brackets] explain what to write — delete them in your final version.

---

---

# Automated Patch Management Pipeline — 340 Endpoints

**Type:** Work Project
**Status:** Complete
**Year:** 2024
**Domain(s):** Systems Administration · Automation · Security
**Technologies:** PowerShell · WSUS · SCCM · Windows Server 2022 · Active Directory

---

## 🔍 The Problem

[Describe the situation you inherited or the gap you identified. Include the business impact of the problem — not just the technical issue. Answer: why did this matter to the business?]

Our organisation was managing software updates for 340 Windows endpoints through a manual process: an administrator would log into WSUS, approve updates, then manually verify patch status on each device group over the following weeks. The entire cycle took 3 weeks from patch release to confirmed deployment.

This meant that during any given month, critical CVEs published by Microsoft remained unpatched on production machines for up to 21 days — a significant exposure window. Additionally, the process consumed approximately 12–15 hours of senior IT engineer time each month, time that could not be spent on higher-value work.

---

## 🛠️ What I Built

[Be specific and technical. Name the tools, the scale, the architecture. Avoid vague language. A hiring manager or peer reviewer should be able to picture exactly what you did.]

I designed and implemented a four-stage automated patching pipeline:

**Stage 1 — Patch sourcing and approval**
Configured WSUS synchronisation to run nightly. Wrote a PowerShell script (`Approve-CriticalUpdates.ps1`) that auto-approves updates classified as Critical or Security after a 48-hour staging window, allowing the IT team to review and veto before production rollout.

**Stage 2 — Deployment rings**
Segmented the 340 endpoints into three deployment rings using Active Directory OUs:
- Ring 0: 10 IT-owned test machines (immediate deployment)
- Ring 1: 80 non-critical workstations (72-hour delay)
- Ring 2: 250 production and executive endpoints (7-day delay after Ring 1 success)

**Stage 3 — Monitoring and alerting**
Built a PowerShell monitoring script (`Check-PatchCompliance.ps1`) that queries WSUS for compliance status, generates a daily HTML report, and emails it to the IT manager. Devices below 90% compliance after the deployment window trigger an automated alert.

**Stage 4 — Remediation**
Configured a scheduled task (using SCCM baseline deployments) to force-install outstanding updates on non-compliant devices and reboot outside business hours (02:00–04:00 window).

All scripts are version-controlled in a private GitHub repository with inline documentation.

---

## ⚙️ Technologies Used

- **WSUS (Windows Server Update Services)** — central update management, approval rules, deployment rings
- **PowerShell 5.1** — automation scripts for approval, reporting, and compliance checking
- **SCCM (System Center Configuration Manager)** — software deployment, baseline compliance, inventory
- **Active Directory OUs** — used to define and target deployment ring groups
- **Windows Server 2022** — WSUS and SCCM infrastructure
- **Task Scheduler** — orchestrating script execution on schedule
- **SMTP relay** — automated daily compliance reports via email

---

## 📊 Business Impact (Quantified)

| Metric | Before | After | Change |
|---|---|---|---|
| Patch cycle time (critical CVE to full deployment) | 21 days | 48 hours | ↓ 77% |
| Unpatched critical CVEs at any given time | ~18 avg | ~1 avg | ↓ 94% |
| IT engineer time spent on patching | 13 hrs/month | 1 hr/month (review only) | ↓ 92% |
| Patch compliance rate (org-wide) | 71% | 97% | ↑ 26pp |
| Patch-related helpdesk tickets | 8/month | 2/month | ↓ 75% |

**Plain English summary:**
The automated pipeline reduced the time it takes to patch a critical vulnerability across all 340 devices from three weeks to two days — cutting the organisation's exposure window by 77%. It also freed up a full working day of engineering time every month that is now spent on proactive infrastructure work instead of manual patching.

---

## 🧠 What I Learned

- **WSUS at scale needs its own maintenance.** WSUS databases grow large quickly and need regular cleanup (`wsusutil.exe cleanupagent`) — I automated this as well after discovering it as a problem mid-project.
- **Deployment rings are essential.** The first rollout attempt without rings caused 3 production machines to reboot during business hours. Rings plus maintenance windows solved this entirely.
- **Compliance reporting is where the business case is.** The daily HTML compliance report was the most-appreciated output — management could see patch status at a glance without logging into anything.
- **What I'd do differently:** In a cloud-forward environment, I'd replace WSUS with Microsoft Intune + Windows Update for Business for simpler ring management and cloud reporting dashboards.

---

## 📎 Artefacts

- [x] Architecture diagram (see below)
- [x] PowerShell scripts — [github.com/yourusername/patch-automation](https://github.com)
- [x] Sample compliance report (HTML)
- [ ] Blog post — in progress

---

## Architecture Diagram

```
                     ┌─────────────────────────────────────┐
                     │         WSUS Server                  │
                     │  - Nightly sync from Microsoft        │
                     │  - Auto-approve after 48hr staging    │
                     └──────────────┬──────────────────────┘
                                    │ Approves updates
              ┌─────────────────────┼────────────────────┐
              ▼                     ▼                     ▼
     ┌─────────────┐      ┌─────────────────┐   ┌─────────────────────┐
     │   Ring 0    │      │     Ring 1      │   │       Ring 2        │
     │  10 IT PCs  │      │ 80 workstations │   │  250 production PCs │
     │  Immediate  │      │  +72hr delay    │   │  +7 day delay       │
     └──────┬──────┘      └────────┬────────┘   └──────────┬──────────┘
            │                     │                        │
            └─────────────────────┴────────────────────────┘
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │  Compliance Monitor  │
                         │  (PowerShell script) │
                         │  Daily HTML report → │
                         │  Email to IT Manager │
                         └──────────────────────┘
                                    │
                         Below 90%? │
                                    ▼
                         ┌──────────────────────┐
                         │  SCCM Remediation    │
                         │  Force install       │
                         │  Reboot: 02:00–04:00 │
                         └──────────────────────┘
```

---

---

## 📝 Notes on writing your own entries

**On quantifying impact** — if you don't have exact numbers, estimate honestly:
- "Saved approximately 10 hours per month based on previous manual effort"
- "Reduced ticket volume by an estimated 50% based on category comparison, month-over-month"
- Estimated numbers are fine as long as you label them as estimates

**On lab projects** — the same format works. For labs, the "Business Impact" section becomes "What this demonstrates" — what skill, concept, or security principle does the lab prove you understand?

**Length** — aim for 300–500 words in the main body. Long enough to be credible, short enough to be readable.

**Tone** — write as if explaining to a senior engineer who wasn't there. Technical enough to be convincing, clear enough that a non-technical manager can extract the value.
