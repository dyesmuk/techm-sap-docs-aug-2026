# SAP Commerce (Hybris), SAP Integration Suite & S/4HANA Training
### Delivery Schedule — 48 Hours Total

**Format:** 19 days x 2.5 hrs + Day 20 x 0.5 hr (Q&A) = **48 hours**
**Note:** Actual calendar dates to be provided by client. Day numbers below denote sequence only.

---

## Trainee Prerequisites

### Must-Have
- Core Java & Object-Oriented Programming (classes, collections, exceptions)
- Web/HTTP fundamentals (REST, JSON, HTTP methods, status codes)
- Basic command-line comfort (used across Docker, Kubernetes, Maven, Git)
- Basic SQL / relational database concepts

### Good-to-Have
- Prior exposure to Angular or another SPA framework (TypeScript, components, routing)
- Basic understanding of authentication/authorization concepts (OAuth 2.0, tokens)
- Some prior exposure to cloud/containerized environments (Docker, Kubernetes)
- Familiarity with e-commerce/retail domain concepts (products, catalogs, orders, categories)

---

## Scoping and Duration

Please note before we lock dates: within 48 hours, a few blocks (iFlow dev, REST integration, Angular/Spartacus storefront, custom extension dev) will land as guided walkthroughs of working examples rather than independent builds — those topics normally take longer elsewhere. We'll pre-template the labs to make the most of the time.

If trainees need to be production-capable on these instead, we'd want closer to 60-65 hours. Let me know which direction you'd prefer.

---

## Day-Wise Delivery Schedule

| Day | Duration | Topics | Lab / Hands-on |
|---|---|---|---|
| **Day 1** | 2.5 hrs | Infrastructure Overview (SAP Commerce Cloud Infra, Cloud Native Commerce) · Docker Fundamentals (Architecture, Images, Containers) · Docker Components (Volumes, Networking, Docker Compose) | Docker install/verify, basic container run |
| **Day 2** | 2.5 hrs | Kubernetes Introduction (Fundamentals, Architecture, Pods) · Kubernetes Workloads (ReplicaSets, Deployments, Services) · Cloud Deployment overview (AKS, Automation Engine, CI/CD) | Local K8s cluster (Kind) basic deployment |
| **Day 3** | 2.5 hrs | SAP Commerce Integration Basics (Integration Architecture, Integration Patterns, Web Services) · APIs & Security (Event-Driven Architecture, Integration APIs, OAuth 2.0) | Conceptual walkthrough / architecture diagrams |
| **Day 4** | 2.5 hrs | Monitoring & Performance (Monitoring, Error Handling, Performance) · Recap & buffer | Q&A / consolidation |
| **Day 5** | 2.5 hrs | Extended Integration Overview — SAP CPI / SAP Integration Suite, OData, SAP BTP, S/4HANA Integration Overview | Conceptual walkthrough |
| **Day 6** | 2.5 hrs | SAP Integration Suite deep-dive (Event Mesh, Customer Data Cloud, Identity Authentication Service, CPQ) | **Lab:** SAP Integration Suite Environment Setup, Login to SAP BTP |
| **Day 7** | 2.5 hrs | Cloud Integration exploration, API Management overview | **Lab:** Explore Cloud Integration, API Management |
| **Day 8** | 2.5 hrs | iFlow development concepts | **Lab:** Create First iFlow, Configure Sender/Receiver, Content Modifier, Message Mapping, Deploy iFlow, Trigger Integration, Monitor Execution |
| **Day 9** | 2.5 hrs | REST integration via CPI concepts | **Lab:** REST API Integration using CPI — HTTP Sender/Receiver Adapter, JSON Transformation, Deploy, Test via Postman, SAP Commerce → CPI → External Shipping API |
| **Day 10** | 2.5 hrs | SAP Commerce Integrations overview — Headless Commerce, Payment Integrations, OMS, SAP Data Hub, Marketing Cloud Integration, Qualtrics Integration | Conceptual walkthrough |
| **Day 11** | 2.5 hrs | OAuth client configuration concepts | **Lab:** OAuth Client Configuration |
| **Day 12** | 2.5 hrs | Token-based security concepts | **Lab:** Client Credentials Flow, Generate Access Token, Secure APIs, Token Validation |
| **Day 13** | 2.5 hrs | OData service consumption concepts | **Lab:** OData Service Consumption — GET Operations, Product Retrieval, Customer Retrieval, Filtering, Sorting, Pagination |
| **Day 14** | 2.5 hrs | Spartacus & Angular — Headless Commerce, Spartacus Architecture, Angular Fundamentals, Components, Modules, Services · Topics: Dependency Injection, Routing, Reactive Forms, State Management | Guided Angular refresher exercises |
| **Day 15** | 2.5 hrs | Spartacus setup concepts | **Lab:** Install Spartacus |
| **Day 16** | 2.5 hrs | Topics: OCC Integration, Theming, Responsive Design | **Lab:** Homepage Development, Product Pages |
| **Day 17** | 2.5 hrs | Storefront build continuation | **Lab:** Shopping Cart |
| **Day 18** | 2.5 hrs | Customization & Enterprise Development — Extension Development, Items.xml, Type System, CronJobs, Business Processes · Topics: Solr, Rule Engine, Personalization | Conceptual walkthrough |
| **Day 19** | 2.5 hrs | Custom extension & search config concepts | **Lab:** Create Custom Extension, Solr Configuration |
| **Day 20** | 0.5 hr | Wrap-up | **Q&A** |

---

## Delivery Notes
- **Framing:** Guided, hands-on walkthrough of pre-templated labs (working examples extended by trainees) — not independent from-scratch builds. This is necessary to fit the 48-hour window; see prerequisites and scope notes for context.
- **Prerequisite dependency:** Days 14-17 (Angular/Spartacus storefront) assume trainees already have baseline Angular/TypeScript exposure per the agreed prerequisites — this is what keeps that block viable at 2.5 hrs/day.
- **External dependency:** SAP Commerce Cloud, SAP BTP/Integration Suite trial, and S/4HANA sandbox access must be provisioned and verified before Day 1 to avoid schedule slippage, particularly before Day 6 (Integration Suite) and Day 13 (OData/S4HANA).
