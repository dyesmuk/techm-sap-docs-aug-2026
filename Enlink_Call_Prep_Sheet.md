# Enlink Client Call — Prep Sheet
### SAP Commerce (Hybris) Training — Discussion / Tech Eval / Demo

---

## Proposed Agenda (open the call with this)

| # | Item | Time |
|---|---|---|
| 1 | Recap of scope & prerequisites | 2 min |
| 2 | Delivery schedule walkthrough — TOC, narrative approach | 10 min |
| 3 | Technical demo | 10-15 min |
| 4 | Tech eval / Q&A | 15 min |
| 5 | Open items — access, cost, IAS, timeline | 10 min |

---

## Demo Checklist

- [ ] Live Docker build + run of sample containerized app (Day 1 lab preview)
- [ ] Local Kind cluster — deploy/scale that container (Day 2 lab preview)
- [ ] Walk through the 3 delivery docs: Delivery Schedule, Consolidated Lab Activities, Labs Requirement checklist
- [ ] Explain ShopKart/QuickShip narrative thread (Sonu, Monu, Pooja, Isha) — verbal is fine, no slide needed
- [ ] **If done tonight:** SAP BTP free trial Cockpit walkthrough — Cloud Integration / API Management tiles

**Tonight, if time permits:** sign up for SAP BTP free trial, spend 15-20 min in Cloud Integration. Materially strengthens Day 5-9 credibility tomorrow.

---

## Tech-Eval Talking Points (be conversational, not encyclopedic)

- **Docker/K8s:** Deployment vs ReplicaSet vs Service; why containerize Commerce workloads
- **SAP Commerce basics:** Backoffice vs HAC vs OCC APIs vs SmartEdit — what each is for
- **CPI/Integration Suite:** what an iFlow is, sender/receiver adapters, why OAuth client credentials flow fits system-to-system calls
- **OData:** GET / filter / sort / pagination — standard REST-over-metadata concepts
- **Spartacus:** Angular-based, headless storefront consuming OCC APIs
- **Extension dev:** Items.xml defines custom types; where CronJobs/business processes fit

---

## Open Items to Get Commitments On

- [ ] SAP Commerce Cloud (2211 LTS) instance + sample data — timeline?
- [ ] S/4HANA sandbox — via their SAP partner license, or do they point us to one?
- [ ] SAP IAS availability confirmation (OAuth/SSO demo)
- [ ] Login credentials / shared training accounts for participants
- [ ] **Cost per participant per month** — come with an answer or a clear "will follow up by [date]"
- [ ] Confirm 50-hour / 2.5-hr-per-day format works
- [ ] Confirm delivery dates starting next week

---

## Scope Framing — Have This Ready If Asked

> "Within 50 hours, blocks like iFlow dev, REST integration, Angular/Spartacus storefront, and custom extension dev will land as **guided walkthroughs of pre-templated working examples** — not independent from-scratch builds. If trainees need to be production-capable on these instead, we'd want closer to **60-65 hours**."

State this plainly if they ask "can trainees actually build this on their own after?"
