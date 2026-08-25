# Day 3 — SAP Commerce Starts Talking: Integration Basics 🔌

**Duration:** 2.5 hrs
**Vibe check:** Infra's sorted. Now let's open the hood on SAP Commerce itself — specifically, how it talks to *everything else*: payment gateways, ERPs, marketing tools, external shipping APIs. Nothing in real e-commerce lives in isolation, and Commerce is built assuming that from day one.

> Your lab environment has SAP Commerce Cloud pre-loaded with Backoffice, HAC, OCC APIs, and sample data (products, categories, customers, orders) — we're using it directly today, no setup needed.

---

## 🎯 What You'll Walk Away With
- A working mental model of SAP Commerce's integration architecture and the common patterns it uses
- Clarity on what "web services" means in the Commerce world (hint: it's mostly OCC)
- Hands-on: navigate Backoffice + HAC, and make real API calls against a live Commerce instance

---

## Part 1: Integration Architecture

SAP Commerce doesn't run alone — it sits at the center of a web of systems:

```
   Payment Gateway ↘
   ERP / S4HANA    → SAP COMMERCE ← Storefront (Spartacus/Angular)
   Marketing Cloud  ↗              ← Backoffice (admin)
```

Every one of those arrows is an integration point, and each needs to be:
- **Reliable** — a failed payment sync can't silently vanish
- **Secure** — you're moving customer and order data
- **Observable** — when something breaks at 2 AM, someone needs to know why

That's the whole reason integration architecture is its own discipline, not an afterthought bolted on at the end.

### The Two Big Architectural Layers
- **Commerce-native layer** — Backoffice (admin console), HAC (Hybris Administration Console — your diagnostics and job-control panel), and the core data model (products, catalogs, customers, orders)
- **API layer** — OCC (Omni-Commerce Connect) REST APIs, which is how *everything external* — your storefront, mobile apps, third-party systems — reads and writes Commerce data

---

## Part 2: Integration Patterns

You'll see the same handful of patterns show up again and again across SAP's ecosystem:

| Pattern | What It Means | When You'll See It |
|---|---|---|
| **Synchronous REST** | Request → immediate response | Storefront fetching product data via OCC |
| **Event-driven / async** | Something happens → an event fires → interested systems react, no one's blocked waiting | Order placed → inventory system notified → shipping triggered |
| **Batch / scheduled sync** | Data moves on a schedule, not in real-time | Nightly catalog sync from a PIM system |
| **Middleware-brokered** | Two systems don't talk directly — an integration layer (like SAP Integration Suite, which we hit later this week) sits between them | SAP Commerce ↔ CPI ↔ External Shipping API |

**Why it matters:** picking the wrong pattern for the job is a classic integration mistake. You don't want a synchronous call blocking checkout while it waits on a slow external system — that's exactly what async/event-driven patterns exist to avoid.

---

## Part 3: Web Services in Commerce

When people say "SAP Commerce web services," 90% of the time they mean **OCC (Omni-Commerce Connect)** — Commerce's REST API layer. It exposes:
- Product & catalog data
- Cart & checkout operations
- Customer accounts & orders
- Search (backed by Solr)

This is the *exact same API* your Spartacus storefront will use later in the program — so getting comfortable with OCC today pays off directly on Day 15+.

---

## 🧪 Hands-On Lab

### Lab 1: Tour Backoffice
Log into **Backoffice** and locate:
- A product in the sample catalog — note its code
- A customer record
- An order

This is your admin's-eye view of the exact data OCC will expose via API.

### Lab 2: Explore HAC (Hybris Administration Console)
Log into **HAC** and check out:
- **Console → Impex/Groovy** tab (data import/scripting)
- **System → Monitoring** area (jobs, cronjobs — we'll dig deeper on Day 4)
- **Console → Solr Search** (search index status)

HAC is your go-to diagnostics panel — when something's misbehaving in Commerce, HAC is usually where you start looking.

### Lab 3: Call OCC APIs Directly
Using Postman (or `curl`), hit your sample storefront's OCC endpoints:

```bash
# Get product catalog info
curl "https://<your-commerce-host>/occ/v2/<basesite>/products/<product-code>"

# List products
curl "https://<your-commerce-host>/occ/v2/<basesite>/products/search?query=<keyword>"
```

Grab the exact `<basesite>` and a real `<product-code>` from what you found in Backoffice in Lab 1. Inspect the JSON response structure — this is the shape of data your future storefront will consume.

### Lab 4: Trace the Pattern
Pick any one integration pattern from the table above and, using what you saw in Backoffice/HAC, identify **one real example** of it in the sample data (e.g., is the product catalog synced via batch job? Check HAC's cronjob list). Be ready to share what you found.

---

## ✅ Quick Recap Check

1. What's the difference between what Backoffice does and what OCC APIs do?
2. Why would you choose an event-driven pattern over a synchronous REST call for "order placed → notify shipping"?
3. What does OCC stand for, and what's its role in the overall architecture?
4. Where would you look first in Commerce to diagnose a failed background job?
5. Name one integration pattern and a real scenario (from today's lab or otherwise) where it fits.

---

## 👀 Coming Up on Day 4
We go deeper into **securing** these integrations (OAuth 2.0, event-driven architecture in practice) and how you **monitor and troubleshoot** them once they're live.
