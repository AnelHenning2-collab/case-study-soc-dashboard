# SOC Dashboard Redesign
### Reducing Alert Fatigue for Security Operations Center Analysts

🔴 **[Live App → logicalcoders--soc-dashboard.retool.app](https://logicalcoders--soc-dashboard.retool.app/)**

**Role:** Digital Product Designer (UX Research · Interaction Design · Prototype)  
**Tools:** Adobe XD · Figma · Miro · Excel · Retool · Supabase  
**Timeline:** 8 weeks  
**Target Companies:** CrowdStrike · SentinelOne · Splunk · Palo Alto Networks  

---

## The Problem

Security Operations Center analysts face a crisis that no firewall can fix: **alert fatigue**.

The average enterprise SOC receives over **11,000 alerts per day**. Analysts are expected to investigate, triage, and resolve threats across dashboards that were built by engineers for engineers — dense, data-heavy interfaces with no hierarchy, no prioritization, and no consideration for the cognitive load of the humans staring at them for 10-hour shifts.

The result: **critical alerts get missed**. Not because analysts are incompetent — but because the interface failed them.

This case study documents the end-to-end redesign of a SOC analyst dashboard with one clear objective:

> **Help analysts see what matters most, faster.**

---

## Research

### User Interviews

I conducted structured interviews with 5 security analysts across three experience levels — junior analyst (1–2 years), mid-level analyst (3–5 years), and senior analyst (5+ years).

**Key findings:**

| Pain Point | % of Analysts Who Cited It |
|---|---|
| Cannot distinguish critical from low-severity alerts at a glance | 100% |
| Dashboard requires too many clicks to reach investigation view | 80% |
| No context around alerts — just raw data | 80% |
| Cannot track status of open investigations in same view | 60% |
| Color coding is inconsistent or inaccessible | 60% |

**Direct quotes from research sessions:**

> *"I have 400 open alerts right now. I don't know which ones matter. The dashboard doesn't tell me."*  
> — Junior SOC Analyst, Financial Services

> *"By hour six of my shift, everything looks the same. Red, red, red. I've stopped trusting the severity labels."*  
> — Mid-level Analyst, Healthcare

### Competitive Analysis

I audited three existing SOC dashboards — Splunk SIEM, Microsoft Sentinel, and a generic open-source SIEM — against five usability criteria:

| Criteria | Splunk | MS Sentinel | Open Source |
|---|---|---|---|
| Alert priority hierarchy visible at a glance | ✗ | Partial | ✗ |
| Investigation context on same screen | ✗ | ✗ | ✗ |
| Accessible color system | Partial | Partial | ✗ |
| One-click investigation launch | ✗ | Partial | ✗ |
| Analyst workload visibility | ✗ | ✗ | ✗ |

**Gap identified:** No existing tool surfaces the **three things analysts actually need first**: What is critical right now? What am I already working on? What can wait?

### Defining the Problem Statement

> Security analysts cannot effectively prioritize their response because existing dashboards treat all alerts as equal and require excessive navigation to reach actionable information.

---

## Design Process

### Information Architecture

Before wireframing, I restructured the information hierarchy based on analyst mental models from research:

```
LEVEL 1 — What needs immediate action? (Critical alerts, SLA breaches)
LEVEL 2 — What am I currently working on? (Active investigations)
LEVEL 3 — What is the broader threat picture? (Trends, patterns, metrics)
LEVEL 4 — Historical & reporting data
```

This became the layout logic for every screen.

### Low-Fidelity Wireframes

Three layout concepts were sketched and presented to three analysts for feedback:

- **Concept A:** Split-panel (alert list left, investigation detail right)
- **Concept B:** Priority-first grid (3 zones: Critical / Active / Queue)
- **Concept C:** Timeline-based view (chronological with severity overlays)

**Analyst preference: Concept B** — the priority-first grid matched how analysts described their mental triage process.

### Design Decisions

**Decision 1: The 3-Zone Layout**
The dashboard opens to three clearly delineated zones:
- 🔴 **CRITICAL** — alerts requiring immediate response (auto-sorted by severity score + age)
- 🟡 **IN PROGRESS** — analyst's active investigations with status and time elapsed
- ⬜ **QUEUE** — all other alerts, sorted by score, collapsible

**Decision 2: Severity Scoring Visible at Card Level**
Each alert card shows:
- Severity score (1–100)
- MITRE ATT&CK tactic tag
- Time since detection
- Affected asset count
- One-click "Investigate" button

**Decision 3: Accessible Color System**
Moved away from red/green binary (inaccessible for color-blind users) to a combined color + shape + label system meeting WCAG AA standards.

**Decision 4: Analyst Workload Panel**
Added a sidebar showing team workload distribution — how many open investigations per analyst — enabling supervisors to reassign without leaving the dashboard.

---

## High-Fidelity Prototype

### Screen 1: Dashboard Home — Priority View
Three-zone grid. Critical alerts surface automatically. Each card shows severity score, MITRE tactic, asset count, and elapsed time. One-click investigation launch.

### Screen 2: Investigation Detail View
Launches in-line (no page navigation). Shows alert timeline, related events, affected assets, recommended playbook steps, and analyst notes — all in one panel.

### Screen 3: Alert Configuration Panel
Allows analysts to configure severity thresholds, suppression rules, and notification preferences without leaving the dashboard context.

### Screen 4: Team Workload View
Supervisor-level view showing investigation load per analyst, open SLA timers, and escalation flags.

---

## Usability Testing

### Method
Moderated usability testing with 4 participants (2 junior analysts, 2 mid-level). Each completed 5 tasks using a clickable Adobe XD prototype.

### Task Completion Results

| Task | Original Dashboard | Redesigned Dashboard |
|---|---|---|
| Identify the highest severity alert | 47 seconds avg | 8 seconds avg |
| Launch investigation for a critical alert | 6 clicks avg | 1 click avg |
| Check status of active investigations | Not possible in single view | 4 seconds avg |
| Adjust alert severity threshold | 4 screens avg | 1 screen avg |
| Reassign investigation to another analyst | Not available | 2 clicks avg |

### Participant Feedback

> *"This is the first dashboard that actually tells me what to do first."*  
> — Participant 2, Mid-level Analyst

> *"The severity score on each card changes everything. I know in 3 seconds which one needs me."*  
> — Participant 4, Junior Analyst

---

## Outcomes & Impact

| Metric | Before | After |
|---|---|---|
| Time to identify critical alert | 47 sec | 8 sec (**83% reduction**) |
| Clicks to launch investigation | 6 | 1 (**83% reduction**) |
| Analyst-reported confidence in triage decisions | 40% | 85% |
| Color accessibility compliance | Fail | WCAG AA Pass |

---

## Reflection

**What worked:** The 3-zone priority layout immediately resonated with analysts because it matched their existing mental model — they already think in terms of critical/active/queue. The design validated that mental model rather than forcing a new one.

**What I would do differently:** I would invest more research time in understanding SIEM integration constraints earlier in the process. Several design decisions required revision once I understood the data structure limitations of the underlying alert pipeline.

**What this taught me:** Security tooling fails users not because of technical limitations — but because the people building them have rarely sat in a SOC chair for a 10-hour shift. Domain knowledge is not optional in security UX. It is the entire foundation.

---

## About the Designer

**Anèl Henning** — Digital Product Designer with MS Cybersecurity (Purdue Global, 2026), BFA Graphic Design (MICA), BS Computer Science, and HIPAA Business Associate Certification. Based in Tampa, FL.

[Portfolio](https://anel-henning.github.io/ux-cybersecurity-portfolio) · [GitHub](https://github.com/AnelHenning2-collab) · [Email](mailto:logicalcoders@outlook.com)
