# Lab Provider Call — Prep Notes
### SAP Commerce (Hybris), Integration Suite & S/4HANA Training — 20 Days / 50 Hours

---

## 1. SAP Commerce Cloud
- [ ] Confirm version — 2211 LTS or current supported version
- [ ] Confirm Backoffice, HAC, OCC APIs, SmartEdit, Solr are all included and enabled
- [ ] Confirm a **sample storefront** ships pre-loaded — products, categories, customers, orders, catalogs (critical: Day 3 onward depends on this)
- [ ] Ask if sample data volume/variety is enough for search/facet labs (Day 19)

## 2. SAP Integration Suite / BTP
- [ ] Confirm Cloud Integration (CPI) and API Management are active
- [ ] Ask status of Event Mesh, Integration Advisor, Open Connectors — included, optional, or unavailable?
- [ ] Confirm SAP Identity Authentication Service (IAS) availability — needed for OAuth/SSO labs (Days 4, 11-12)

## 3. SAP S/4HANA Sandbox
- [ ] Confirm it's reachable as an **OData endpoint**, not just a UI demo
- [ ] Confirm product and customer data is pre-loaded (Day 13 depends on real records)
- [ ] Get the exact OData service names exposed by default

## 4. Access & Credentials
- [ ] Clarify access model — shared training account vs. individual logins per participant
- [ ] Confirm full permissions across Commerce, BTP, and S/4HANA
- [ ] Get actual hostnames/URLs now (courseware currently has placeholders to fill in)

## 5. Timeline & Readiness
- [ ] Confirm exact environment-ready date, with buffer before Day 1
- [ ] Flag two hard dependency points: **before Day 6** (Integration Suite hands-on) and **before Day 13** (S/4HANA OData)
- [ ] Ask about support/escalation path if something breaks mid-training, and expected turnaround

## 6. Cost
- [ ] Cost per participant per month
- [ ] What happens if the batch runs longer than 20 sessions

## 7. Local/Dev Tooling
- [ ] Confirm Docker, Minikube/Kind, kubectl, JDK, Maven, Git, MySQL, Solr, Tomcat, Postman, Spartacus are pre-installed on provided VMs or trivially installable
- [ ] This needs to be a solved problem before Day 1 — not troubleshot live

## 8. Dry-Run Access (ask for this explicitly)
- [ ] Request a personal test login a few days before the batch starts, to verify every environment touchpoint against the actual courseware before trainees log in

---

# Lab Environment Testing Guide
### To run once the provider confirms setup is ready

## ⏱️ Time Estimate: ~5-7 hours total
Best done as a single focused pass, or split across two half-days. Do this **2-3 days before Day 1** — not the night before — so there's real buffer to report and fix issues with the provider.

| Block | What You're Testing | Est. Time |
|---|---|---|
| Docker & Kubernetes | Local Docker/Kind cluster commands (Days 1-2) | ~30 min |
| SAP Commerce Cloud | Backoffice, HAC, OCC APIs, sample data, SmartEdit, Solr (Days 3-4, 10, 16-19) | ~90 min |
| SAP Integration Suite / BTP | Cockpit access, CPI iFlow build + deploy, API Management proxy, OAuth client config (Days 5-12) | ~90-120 min |
| S/4HANA OData | Metadata + GET/filter/sort/pagination calls (Day 13) | ~30-45 min |
| Spartacus Storefront | Install, connect to OCC backend, render sample data (Days 14-17) | ~45-60 min |
| Custom Extension & Solr | Extension scaffold, rebuild, reindex (Days 18-19) | ~30-45 min |

---

## ✅ What to Actually Check

### Docker & Kubernetes
- `docker info` and `kubectl cluster-info` respond cleanly
- Can build/run a container and deploy a basic app to the local cluster

### SAP Commerce Cloud
- Backoffice login works; sample products, customers, orders, catalogs are all visible
- HAC login works; can see cronjob monitoring, ImpEx console, Solr search status
- OCC API calls succeed against real product codes (`GET /occ/v2/{basesite}/products/{code}`)
- SmartEdit loads and can edit a CMS component
- Solr search returns results for the sample catalog

### SAP Integration Suite / BTP
- BTP cockpit login works; Integration Suite subscription is visible and launches
- Can create, deploy, and trigger a basic iFlow end-to-end (sender → transform → receiver)
- API Management: can create an API proxy and see it respond
- OAuth: can generate a client credentials token and use it against a secured endpoint
- Confirm actual hostnames/runtime URLs to swap into the courseware placeholders

### S/4HANA Sandbox
- `$metadata` endpoint responds and lists real entity sets
- GET calls against product/customer entities return real data
- `$filter`, `$orderby`, `$top`, `$skip` all work as expected

### Spartacus Storefront
- `ng add @spartacus/schematics` completes without errors against the given OCC backend
- Storefront loads and renders real sample products from the configured base site
- Add-to-cart, quantity update, and remove-item all persist correctly (refresh test)

### Custom Extension & Solr
- `ant extgen` and `ant clean all` complete successfully
- A custom item type can be defined, built, and imported via ImpEx
- A full Solr reindex completes and a new facet shows up correctly in search results

---

## 🚩 If Something's Broken
Note the exact step, error message, and screenshot if possible — send it back to the provider immediately rather than trying to work around it. Anything broken in Commerce/Integration Suite/S4HANA access is their fix, not something to patch around in your courseware.
