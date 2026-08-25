# SAP Commerce (Hybris), SAP Integration Suite & S/4HANA Training
### Delivery Schedule — 50 Hours Total

**Format:** 20 days x 2.5 hrs = **50 hours**
**Note:** Actual calendar dates to be provided by client. Day numbers below denote sequence only.

---

## Trainee Prerequisites

### Must-Have
- Core Java & Object-Oriented Programming (classes, collections, exceptions) — needed to read Commerce's auto-generated model classes and follow platform architecture, not to hand-write backend Java
- Web/HTTP fundamentals (REST, JSON, HTTP methods, status codes)
- Basic command-line comfort (used across Docker, Kubernetes, Ant, Git)
- Basic SQL / relational database concepts

### Good-to-Have
- Prior exposure to Angular or another SPA framework (TypeScript, components, routing) — Days 14-17 involve real hands-on TypeScript/Angular work
- Basic understanding of authentication/authorization concepts (OAuth 2.0, tokens)
- Some prior exposure to cloud/containerized environments (Docker, Kubernetes)
- Familiarity with e-commerce/retail domain concepts (products, catalogs, orders, categories)

---

## Scoping and Duration

Within 50 hours, iFlow development, REST integration, the Angular/Spartacus storefront, and custom extension development are delivered as guided, hands-on walkthroughs of pre-templated labs — real, working exercises extended by trainees — rather than independent from-scratch builds. This is what makes full coverage viable in the available time.

**No custom Java or Spring coding is required anywhere in this program.** Java knowledge is a comprehension prerequisite (reading generated model classes, following Commerce's architecture), not a hands-on coding deliverable. The one substantial coding block is TypeScript/Angular work in the Spartacus storefront days (14-17).

---

## Environment Notes

- SAP Commerce Cloud, SAP BTP/Integration Suite, and the S/4HANA sandbox are cloud-hosted and accessed via browser/API — no local install needed for these.
- Custom extension development (Days 18-19) requires a **local SAP Commerce development environment** (JDK, Ant, local DB, local Solr, local Tomcat) — this mirrors real-world SAP Commerce Cloud (CCv2) practice, where extensions are built and tested locally, then promoted to the cloud instance via CI/CD.
- Docker, Kubernetes tooling, Node.js/Angular CLI, and Postman are needed for their respective hands-on days regardless of hosting approach.
- Recommended: provision all of the above as a pre-configured, browser-accessible cloud VM per trainee, rather than requiring local installs on individual laptops — removes Day 1 setup friction and guarantees a consistent environment across the batch.

---

## Day-Wise Delivery Schedule

| Day | Topics | Lab / Hands-on |
|---|---|---|---|
| **Day 1** | Infrastructure Overview (SAP Commerce Cloud Infra, Cloud Native Commerce) · Docker Fundamentals (Architecture, Images, Containers) · Docker Components (Volumes, Networking, Docker Compose) | Build a custom image, persist data with volumes, connect containers over a network, run a multi-service stack with Docker Compose |
| **Day 2** | Kubernetes Introduction (Fundamentals, Architecture, Pods) · Kubernetes Workloads (ReplicaSets, Deployments, Services) · Cloud Deployment overview (AKS, Automation Engine, CI/CD) | Deploy to a local cluster, expose via a Service, observe self-healing, scale on demand, perform a rolling update and rollback |
| **Day 3** | SAP Commerce Integration Basics (Integration Architecture, Integration Patterns, Web Services/OCC) | Tour Backoffice and HAC, call live OCC APIs against sample data, trace a real integration pattern in the sample environment |
| **Day 4** | APIs & Security (Event-Driven Architecture, Integration APIs, OAuth 2.0) · Monitoring & Performance (Monitoring, Error Handling) | Call a protected OCC endpoint unauthenticated vs. token-secured, investigate cronjob status and logs in HAC, deliberately trigger and diagnose an error |
| **Day 5** | Extended Integration Overview — SAP CPI / SAP Integration Suite, OData, SAP BTP, S/4HANA Integration Overview | Tour the BTP cockpit and Integration Suite launchpad, browse pre-built integration content, fetch an OData metadata document and a first read from S/4HANA |
| **Day 6** | SAP Integration Suite deep-dive (Event Mesh, Customer Data Cloud, Identity Authentication Service, CPQ) | Confirm/configure Integration Suite access and roles, locate Event Mesh and IAS configuration, verify Cloud Integration runtime health |
| **Day 7** | Cloud Integration workspace, API Management overview | Explore integration packages and message monitoring, create and deploy an API proxy, attach and test a rate-limit policy |
| **Day 8** | iFlow development — Sender/Receiver, Content Modifier, Message Mapping | **Lab:** Create First iFlow — configure sender/receiver, add a Content Modifier and Message Mapping, deploy, trigger, and trace execution in Monitor |
| **Day 9** | REST integration via CPI — HTTP adapters, JSON transformation | **Lab:** SAP Commerce → CPI → External Shipping API — build the flow, transform the payload shape, deploy, and verify end-to-end via Postman |
| **Day 10** | SAP Commerce Integrations Landscape — Headless Commerce, Payment Integrations, OMS, SAP Data Hub, Marketing Cloud Integration, Qualtrics Integration | Inspect payment provider config in Backoffice, confirm a headless OCC response is frontend-agnostic, map each integration to its underlying pattern (sync/event-driven/batch/middleware-brokered) |
| **Day 11** | OAuth client configuration within Integration Suite — inbound vs. outbound security | **Lab:** Create an OAuth2 Client Credentials artifact, secure an iFlow's inbound endpoint, reference the credential in an outbound call, rotate a secret without touching flow logic |
| **Day 12** | Token-based security — token structure, validation, scope | **Lab:** Generate and decode an access token, use it against a secured endpoint, test expiry and scope-based rejection, run a fully authenticated round trip |
| **Day 13** | OData service consumption — query capabilities | **Lab:** Product and customer retrieval from the S/4HANA sandbox, with filtering, sorting, pagination, and field selection, combined into realistic composite queries |
| **Day 14** | Spartacus & Angular Foundations — Headless Commerce, Spartacus Architecture, Angular Fundamentals (Components, Modules, Services, Dependency Injection, Routing, Reactive Forms, State Management) | Build a scratch component + service with DI, a reactive form with validation, and basic routing — the Angular refresher underpinning Spartacus |
| **Day 15** | Spartacus setup and configuration | **Lab:** Scaffold a new Spartacus app, configure base URL/base site/OCC version, run it against the live Commerce backend, verify rendered data traces back to real OCC calls |
| **Day 16** | OCC Integration (component-to-API), Theming, Responsive Design | **Lab:** Theme the storefront, customize the homepage via SmartEdit, customize a product page element, fix a responsive layout issue |
| **Day 17** | Storefront build continuation — cart and checkout | **Lab:** Add/update/remove cart items with live persistence, verify state consistency across components, complete a checkout flow through to a placed order |
| **Day 18** | Customization & Enterprise Development — Extension Development, Items.xml, Type System, CronJobs, Business Processes | **Lab:** Scaffold a custom extension, define a custom item type via items.xml, rebuild, import sample data via ImpEx, inspect an existing CronJob configuration |
| **Day 19** | Search configuration (Solr) · Path to Production (CI/CD, Cloud Portal deployment) | **Lab:** Add a custom Solr facet from the new item type, run a full reindex, verify it live in the storefront; walk through promoting the local extension to the cloud instance via CI/CD |
| **Day 20** | Capstone: Commerce ↔ S/4HANA Integration · Program Wrap-up | **Lab:** Build an OAuth-secured iFlow that takes a placed Commerce order and posts it to the S/4HANA sandbox via OData, including a real-time availability check — followed by open Q&A |

---

## Delivery Notes

- **Framing:** Guided, hands-on walkthrough of pre-templated labs — every day includes real, working exercises, not conceptual-only walkthroughs.
- **Prerequisite dependency:** Days 14-17 (Angular/Spartacus storefront) assume trainees already have baseline Angular/TypeScript exposure per the agreed prerequisites — this is what keeps that block viable at 2.5 hrs/day.
- **Sequencing dependency:** Day 20's capstone deliberately sits at the end because it draws on OAuth (Days 11-12), OData (Day 13), iFlow-building (Days 8-9), and a real placed order (Day 17) — all of which need to already be in place.
- **External dependency:** SAP Commerce Cloud, SAP BTP/Integration Suite, and S/4HANA sandbox access must be provisioned and verified before Day 1 to avoid schedule slippage, particularly before Day 6 (Integration Suite hands-on begins), Day 13 (OData/S4HANA hands-on begins), and Day 20 (capstone requires all three systems working together).
- **Local environment dependency:** A local SAP Commerce development setup (JDK, Ant, local DB, local Solr, local Tomcat) must be ready before Day 18, alongside Node.js/Angular CLI before Day 14 and Docker/Kubernetes tooling before Day 1.
