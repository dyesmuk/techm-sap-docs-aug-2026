# SAP Commerce (Hybris), SAP Integration Suite & S/4HANA Training
### Labs Requirement — Environment Configuration Checklist

**Context:** SAP Commerce Cloud training lab environment requirements, as requested by client (Enlink).

---

## 1. SAP Commerce Cloud — Mandatory

| Requirement | Detail | Status |
|---|---|---|
| Version | SAP Commerce Cloud 2211 LTS (or current supported version) | ⬜ Pending client provisioning |
| Modules | Backoffice, HAC, OCC APIs, SmartEdit, Solr | ⬜ Pending |
| Sample storefront | Pre-loaded, ready for training use | ⬜ Pending |
| Pre-loaded sample data | Products, categories, customers, orders, catalogs (to save setup time during training) | ⬜ Pending |
| **Free/open-source option?** | **No** — no free trial or open-source edition exists for SAP Commerce Cloud. Requires client-provided license/access, or a time-boxed trial via an SAP partner consultancy (qualification-based, not guaranteed). | — |

## 2. SAP Integration Suite / BTP — Mandatory

| Requirement | Detail | Status |
|---|---|---|
| Cloud Integration (CPI) | Supports CPI/iFlows, REST integration, OAuth, SAP Commerce integrations | ⬜ Pending |
| API Management | Required alongside CPI | ⬜ Pending |
| Optional add-ons | Event Mesh, Integration Advisor, Open Connectors | ⬜ Optional |
| **Free option?** | **Yes** — SAP BTP offers a genuine 90-day free trial (non-commercial, time-limited). This is self-serviceable and doesn't require client provisioning. | ✅ Can self-provision |

## 3. SAP S/4HANA — Sandbox

| Requirement | Detail | Status |
|---|---|---|
| Sandbox/demo instance | Integration endpoint for consuming OData services, reading product/customer data | ⬜ Pending |
| **Free option?** | **No standalone trial** — access comes via SAP Partner Portal test/demo/development licensing, which requires partner status. | — |

## 4. Access

| Requirement | Detail | Status |
|---|---|---|
| Login credentials | For all participants, or shared training accounts with full permissions across all systems above | ⬜ Pending |
| SAP Identity Authentication Service (IAS) | Confirmation needed — required to demo OAuth and single sign-on | ⬜ Pending confirmation |

## 5. Local Machine / VM Tools — Free, Self-Installable

| Tool | Purpose | Status (trainer PC) |
|---|---|---|
| Java JDK (OpenJDK) | Core runtime | ✅ Installed (Java 21) |
| IntelliJ IDEA Community / Eclipse | IDE | ✅ Installed (Eclipse) |
| Apache Maven | Build tool | ✅ Installed |
| Git + GitHub | Version control | ✅ Installed |
| Docker Desktop | Containerization | ✅ Installed |
| Minikube/Kind | Local Kubernetes | ✅ Installed (Kind) |
| kubectl | Kubernetes CLI | ✅ Installed |
| MySQL Community Server | Database | ✅ Installed |
| Apache Solr | Search | ⬅ Install pending (needed by Day 18-19) |
| Apache Tomcat | App server | ✅ Installed |
| Postman | API testing | ✅ Installed |
| Spartacus (open source) | Storefront | Installed via npm/Angular CLI at time of use (Day 15) |
| Free-trial Azure account | Cloud deployment (self-learning topic) | ⬜ Not yet set up |
| Free-trial SAP BTP account | See Section 2 | ⬜ Not yet set up |

---

## Open Items to Confirm with Client
1. Confirm SAP Commerce Cloud (2211 LTS) instance availability with pre-loaded sample data and sample storefront.
2. Confirm S/4HANA sandbox access route (partner license vs. client-provided).
3. Confirm SAP IAS availability for OAuth/SSO demo.
4. Confirm login credentials/shared training accounts for all participants.
5. Cost per participant per month, and arrangement to test the lab environment once ready (as originally requested by client).
