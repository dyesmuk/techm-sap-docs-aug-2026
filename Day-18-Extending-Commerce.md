# Day 18 — Extending Commerce From the Inside 🧩

**Duration:** 2.5 hrs
**Vibe check:** Everything so far has used Commerce as-is. Today's about extending it — adding your own data model, custom business logic, scheduled jobs, and workflow processes. This is where Commerce stops being a black box and becomes something you actually shape.

---

## 🎯 What You'll Walk Away With
- A real custom extension scaffolded in your Commerce instance
- A new custom item type defined via `items.xml`
- Working understanding of CronJobs and Business Processes — and where Solr, Rule Engine, and Personalization fit into the bigger picture

---

## Part 1: The Extension Model

SAP Commerce is built on **extensions** — self-contained modules that add data models, logic, or UI. The platform itself is basically a collection of extensions (core, commerce services, backoffice, etc.) — custom development just means adding your own to that same pattern.

### items.xml — Your Data Model
Every custom extension typically has an `items.xml` defining new **item types** (Commerce's version of entities/classes) — their attributes, relationships to existing types (like extending `Product` with a custom attribute), and how they're persisted. This is the **Type System** in action: Commerce generates Java model classes and DB tables from what you declare here.

### CronJobs — Scheduled Work
Any recurring background task (catalog sync, cache warmup, cleanup jobs) is modeled as a CronJob — itself just another item type, configured with a trigger (schedule) and a job implementation. You've already seen these in HAC's monitoring view back on Day 3/4 — now you understand what's actually behind that list.

### Business Processes
Multi-step workflows (order fulfillment, approval chains) are modeled as **Business Processes** — essentially state machines defined declaratively, where each step can call custom logic and transition based on conditions/events.

---

## Part 2: The Supporting Cast

- **Solr** — powers Commerce's product search and faceted navigation (category filters, price ranges). Tomorrow's lab goes hands-on here.
- **Rule Engine** — drives dynamic behavior (promotions, personalized pricing rules) based on conditions, without hardcoding logic per scenario
- **Personalization** — tailors content/product recommendations per customer segment, often working alongside the Rule Engine and CDC (Day 6) data

---

## 🧪 Hands-On Lab

### Lab 1: Scaffold a Custom Extension
Using Commerce's extension generation tool:
```bash
ant extgen
```
Follow the prompts to generate a new extension (e.g., `myextension`) with a basic template. Add it to your `localextensions.xml` and rebuild:
```bash
ant clean all
```

### Lab 2: Define a Custom Item Type
In your new extension's `items.xml`, define a simple custom type — for example, a `ProductReview` item with attributes like `rating`, `comment`, and a relation back to `Product`. Rebuild and confirm (via HMC/Backoffice or ImpEx) that the new type and its table now exist.

### Lab 3: Import Sample Data via ImpEx
Write a small ImpEx script to create a few sample `ProductReview` records tied to real products from your sample catalog, and import it via HAC's ImpEx console (from Day 3).

### Lab 4: Explore an Existing CronJob
Back in HAC's monitoring view, open the configuration of any existing CronJob (not one you're building) and identify its trigger schedule and its job class. Connect this to what you just learned about how CronJobs are modeled as item types.

### Lab 5: Sketch a Business Process
On paper/shared doc, sketch a simple business process for "customer submits a review" — states, transitions, and any conditions (e.g., auto-publish if rating ≥ 4, otherwise route to moderation).

---

## ✅ Quick Recap Check

1. What does `items.xml` actually generate for you once you rebuild?
2. How do CronJobs relate to the Type System concept you just learned?
3. What's the difference in purpose between the Rule Engine and Personalization, even though they often work together?
4. What did Lab 3 (ImpEx import) let you verify about your new custom type?
5. In your Lab 5 sketch, what would trigger a transition from "submitted" to "published" vs. "needs moderation"?

---

## 👀 Coming Up on Day 19
We finish the extension work and configure **Solr** — getting your custom data and search behavior properly indexed and queryable.
