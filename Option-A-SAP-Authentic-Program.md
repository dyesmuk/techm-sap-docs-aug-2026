# Option A — SAP-Authentic Program
### SAP Commerce (Hybris), SAP Integration Suite & S/4HANA Training

---

## Executive Summary
A 20-day, 50-hour, fully hands-on program delivered entirely on **real SAP systems** — SAP Commerce Cloud, SAP Integration Suite, and an S/4HANA sandbox. Trainees work with the actual Backoffice, HAC, OCC APIs, SmartEdit, Spartacus storefront, Cloud Integration, and OData services they'll encounter on live client projects. No substitutes, no lookalike tools — this is screen-time on the exact platforms trainees will be billed against.

**Best suited for:** organizations that need trainees project-ready on named SAP tools immediately after the program — where "I've used the real SAP Commerce Backoffice" needs to be literally true.

---

## What's Required
- A provisioned SAP Commerce Cloud instance (Backoffice, HAC, OCC, SmartEdit, Solr, sample data)
- SAP BTP with Integration Suite enabled (Cloud Integration, API Management)
- An S/4HANA sandbox reachable via OData
- A local SAP Commerce development platform install for custom extension work (Days 18-19)

This can be sourced either through a **vendor-provisioned lab environment** (custom build, typically 1.5-3 weeks lead time) or an **SAP Learning Hub subscription** (per-trainee, includes live system access to Commerce Cloud, S/4HANA, and BTP).

---

## Trainee Prerequisites

### Must-Have
- Core Java & Object-Oriented Programming (classes, collections, exceptions) — needed to read Commerce's auto-generated model classes and follow platform architecture, not to hand-write backend Java
- Web/HTTP fundamentals (REST, JSON, HTTP methods, status codes)
- Basic command-line comfort
- Basic SQL / relational database concepts

### Good-to-Have
- Prior exposure to Angular or another SPA framework (TypeScript, components, routing)
- Basic understanding of OAuth 2.0 / authentication concepts
- Some prior exposure to Docker/Kubernetes
- Familiarity with e-commerce/retail domain concepts

**No custom Java or Spring coding is required.** The one substantial coding block is TypeScript/Angular work in the Spartacus storefront days (14-17).

---

## Day-Wise Delivery Schedule

| Day | Duration | Topics | Lab / Hands-on |
|---|---|---|---|
| **Day 1** | 2.5 hrs | Infrastructure Overview (SAP Commerce Cloud Infra, Cloud Native Commerce) · Docker Fundamentals · Docker Components | Build a custom image, persist data with volumes, connect containers over a network, run a multi-service stack with Docker Compose |
| **Day 2** | 2.5 hrs | Kubernetes Introduction · Kubernetes Workloads · Cloud Deployment overview (AKS, Automation Engine, CI/CD) | Deploy to a local cluster, expose via a Service, observe self-healing, scale on demand, rolling update and rollback |
| **Day 3** | 2.5 hrs | SAP Commerce Integration Basics (Architecture, Patterns, Web Services/OCC) | Tour Backoffice and HAC, call live OCC APIs against sample data, trace a real integration pattern |
| **Day 4** | 2.5 hrs | APIs & Security (OAuth 2.0) · Monitoring & Performance | Call a protected OCC endpoint unauthenticated vs. token-secured, investigate cronjob status/logs in HAC, diagnose an error |
| **Day 5** | 2.5 hrs | Extended Integration Overview — SAP CPI/Integration Suite, OData, SAP BTP, S/4HANA | Tour BTP cockpit and Integration Suite launchpad, browse pre-built integration content, fetch OData metadata and a first read from S/4HANA |
| **Day 6** | 2.5 hrs | SAP Integration Suite deep-dive (Event Mesh, Customer Data Cloud, IAS, CPQ) | Confirm/configure Integration Suite access and roles, locate Event Mesh and IAS configuration, verify Cloud Integration runtime health |
| **Day 7** | 2.5 hrs | Cloud Integration workspace, API Management overview | Explore integration packages and monitoring, create and deploy an API proxy, attach and test a rate-limit policy |
| **Day 8** | 2.5 hrs | iFlow development — Sender/Receiver, Content Modifier, Message Mapping | Create First iFlow — configure sender/receiver, deploy, trigger, and trace execution in Monitor |
| **Day 9** | 2.5 hrs | REST integration via CPI | SAP Commerce → CPI → External Shipping API — build, transform, deploy, verify via Postman |
| **Day 10** | 2.5 hrs | SAP Commerce Integrations Landscape — Headless Commerce, Payment, OMS, Data Hub, Marketing Cloud, Qualtrics | Inspect payment provider config in Backoffice, confirm headless OCC response, classify each integration by pattern |
| **Day 11** | 2.5 hrs | OAuth client configuration — inbound vs. outbound security | Create OAuth2 Client Credentials artifact, secure inbound endpoint, reference credential outbound, rotate a secret |
| **Day 12** | 2.5 hrs | Token-based security — structure, validation, scope | Generate and decode an access token, test expiry and scope rejection, run a fully authenticated round trip |
| **Day 13** | 2.5 hrs | OData service consumption | Product/customer retrieval from S/4HANA sandbox with filtering, sorting, pagination, field selection |
| **Day 14** | 2.5 hrs | Spartacus & Angular Foundations (Components, Modules, Services, DI, Routing, Reactive Forms, State Management) | Scratch component + service with DI, reactive form with validation, basic routing |
| **Day 15** | 2.5 hrs | Spartacus setup and configuration | Scaffold Spartacus, configure base URL/site/OCC version, run against live Commerce backend |
| **Day 16** | 2.5 hrs | OCC Integration, Theming, Responsive Design | Theme the storefront, customize homepage via SmartEdit, customize a product page element, fix responsive layout |
| **Day 17** | 2.5 hrs | Cart and checkout | Add/update/remove cart items with live persistence, complete checkout through to a placed order |
| **Day 18** | 2.5 hrs | Customization — Extension Development, Items.xml, Type System, CronJobs, Business Processes | Scaffold a custom extension, define a custom item type, rebuild, import sample data via ImpEx |
| **Day 19** | 2.5 hrs | Search configuration (Solr) · Path to Production (CI/CD, Cloud Portal) | Add a custom Solr facet, run a full reindex, verify live; walk through promoting the extension via CI/CD |
| **Day 20** | 2.5 hrs | Capstone: Commerce ↔ S/4HANA Integration · Program Wrap-up | Build an OAuth-secured iFlow taking a placed order and posting it to S/4HANA via OData, with a real-time availability check — followed by open Q&A |

---

## Why This Option
- Trainees leave with genuine, direct experience on the named platforms — no translation gap between training and live project work
- Every lab traces to a real, billable SAP skill
- Certification-adjacent — the skills map directly to SAP's own Commerce Cloud and Integration Suite learning paths

## Trade-Offs
- Requires a paid environment (vendor build or SAP Learning Hub)
- Vendor-built environments carry 1.5-3 weeks of lead time; confirm this against your training start date
