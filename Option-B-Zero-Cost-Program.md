# Option B — Zero-Cost / Concepts-First Program
### Headless Commerce & SAP Integration Suite Foundations

---

## Executive Summary
A 20-day, 50-hour, fully hands-on program at **zero licensing cost** — no vendor-provisioned lab, no per-trainee subscription, no environment lead time. The SAP Integration Suite portion runs on **real SAP tooling** via SAP BTP's permanent Free Tier. Where SAP Commerce Cloud itself would be required, the program uses **Medusa.js**, a self-hosted, open-source headless commerce platform, as the reference architecture — same real-world patterns, different branding on that portion.

**Important, stated plainly:** this is **not** SAP Commerce (Hybris) training. Roughly half the program (Integration Suite, OAuth, OData, infra) is genuine, unmodified SAP tooling at zero cost. The other half (commerce backend, storefront, extension development) uses an architecturally equivalent open-source platform because no free or open-source path to SAP Commerce Cloud exists.

**Best suited for:** organizations that want trainees fluent in the underlying architecture (headless commerce, event-driven integration, OAuth security, cloud-native infra) fast and at no cost, where specific SAP Commerce Cloud screen-time isn't a hard requirement — or as a foundation layer before a shorter, paid SAP Commerce Cloud module.

---

## What's Required
- A free, self-registered SAP BTP account with Free Tier Integration Suite capabilities enabled
- A self-hosted Medusa.js instance (runs locally or on any free-tier cloud VM)
- Free public SAP OData sandboxes (ES5 Gateway demo / SAP Business Accelerator Hub) for OData practice
- Standard open-source dev tooling (Docker, Kubernetes, Node.js, Angular CLI, Git, Postman)

No vendor engagement, no provisioning lead time, no ongoing subscription cost.

---

## Trainee Prerequisites

### Must-Have
- Core programming fundamentals & OOP concepts (TypeScript is used hands-on throughout)
- Web/HTTP fundamentals (REST, JSON, HTTP methods, status codes)
- Basic command-line comfort
- Basic SQL / relational database concepts

### Good-to-Have
- Prior exposure to Angular or another SPA framework
- Basic understanding of OAuth 2.0 / authentication concepts
- Some prior exposure to Docker/Kubernetes
- Familiarity with e-commerce/retail domain concepts

---

## Day-Wise Delivery Schedule

| Day | Status | Topics | Lab / Hands-on |
|---|---|---|---|
| **Day 1** | Open-source | Infrastructure Overview (Cloud-Native Architecture) · Docker Fundamentals · Docker Components | Build a custom image, persist data with volumes, connect containers over a network, run a multi-service stack with Docker Compose |
| **Day 2** | Open-source | Kubernetes Introduction · Kubernetes Workloads · Cloud Deployment concepts (managed K8s, CI/CD) | Deploy to a local cluster, expose via a Service, observe self-healing, scale on demand, rolling update and rollback |
| **Day 3** | Open-source substitute | Headless Commerce Integration Basics — Architecture, Integration Patterns, REST APIs (using Medusa as reference) | Explore Medusa's Admin panel, call its Store/Admin REST APIs against sample data, trace a real integration pattern |
| **Day 4** | Open-source substitute | APIs & Security (OAuth 2.0 concepts) · Monitoring & Error Handling | Call the Medusa API unauthenticated vs. with a valid API key/JWT, inspect logs and errors, diagnose a failure |
| **Day 5** | **Real SAP (free)** | Extended Integration Overview — SAP Integration Suite, OData, SAP BTP, ERP integration concepts | Tour a real BTP Free Tier cockpit and Integration Suite launchpad, fetch a real OData metadata document and first read |
| **Day 6** | **Real SAP (free)** | SAP Integration Suite deep-dive (Event Mesh, Identity Authentication, integration content) | Configure Integration Suite capabilities and roles on BTP Free Tier, verify Cloud Integration runtime health |
| **Day 7** | **Real SAP (free)** | Cloud Integration workspace, API Management overview | Explore integration packages and monitoring, create and deploy a real API proxy, attach and test a rate-limit policy |
| **Day 8** | **Real SAP (free)** | iFlow development — Sender/Receiver, Content Modifier, Message Mapping | Create First iFlow — configure, deploy, trigger, and trace execution in Monitor |
| **Day 9** | **Real SAP (free)** | REST integration via CPI | Headless commerce → CPI → external API — build, transform, deploy, verify via Postman |
| **Day 10** | Open-source substitute | Commerce Integrations Landscape — Headless Commerce, Payments, OMS, Data Sync, Marketing/CX patterns | Inspect a payment plugin's config in Medusa, classify each integration by pattern |
| **Day 11** | **Real SAP (free)** | OAuth client configuration — inbound vs. outbound security | Create OAuth2 Client Credentials artifact, secure inbound endpoint, reference credential outbound, rotate a secret |
| **Day 12** | **Real SAP (free)** | Token-based security — structure, validation, scope | Generate and decode an access token, test expiry and scope rejection, run a fully authenticated round trip |
| **Day 13** | **Real SAP (free)** | OData service consumption | Product/customer retrieval from a free public SAP OData sandbox — filtering, sorting, pagination, field selection |
| **Day 14** | Open-source | Angular Foundations for Headless Storefronts | Scratch component + service with DI, reactive form with validation, basic routing |
| **Day 15** | Open-source substitute | Scaffolding a Headless Storefront — connecting Angular to a real commerce backend | Build a new Angular app, connect it to Medusa's Store API, verify rendered products trace to real API calls |
| **Day 16** | Open-source substitute | Theming, Homepage & Product Pages, Responsive Design | Theme the storefront, build homepage/product components pulling live Medusa data, fix responsive layout |
| **Day 17** | Open-source substitute | Cart & Checkout | Add/update/remove cart items via Medusa's cart API, complete checkout through to a placed order |
| **Day 18** | Open-source substitute | Extending the Commerce Platform — Custom Modules, Data Models, Scheduled Jobs, Workflows | Build a custom Medusa module with a new data entity, define its schema, write a scheduled job |
| **Day 19** | Open-source substitute | Search Configuration · Path to Production (CI/CD) | Configure Meilisearch/Typesense with a custom facet, reindex, verify live; walk through a CI/CD pipeline (GitHub Actions) |
| **Day 20** | **Real SAP + substitute** | Capstone: End-to-End Order Sync Integration · Program Wrap-up | Build an OAuth-secured iFlow (real BTP Free Tier) taking a placed order and posting it via OData to a self-hosted mock ERP endpoint (Apache Olingo) — followed by open Q&A |

---

## Why This Option
- Zero licensing cost, zero lead time — can start almost immediately after BTP account setup
- The Integration Suite skills (Days 5-9, 11-12, part of 20) are 100% authentic, transferable SAP experience
- Architectural patterns taught (headless commerce, OAuth security, event-driven integration, cloud-native infra) transfer directly regardless of which commerce platform a trainee later works on
- Fully self-contained — no dependency on any third party's provisioning timeline

## Trade-Offs
- **Not SAP Commerce Cloud training** — trainees won't have touched Backoffice, HAC, SmartEdit, or Spartacus specifically
- If trainees need to be immediately project-ready on real SAP Commerce Cloud screens, this program alone won't get them there
- Best positioned either as a standalone foundations program, or as a lower-cost base layer with a short, paid SAP Commerce Cloud module added on top later
