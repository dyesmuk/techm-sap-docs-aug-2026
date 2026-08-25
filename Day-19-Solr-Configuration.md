# Day 19 — Wiring Up Search: Solr Configuration 🔎

**Duration:** 2.5 hrs
**Vibe check:** Yesterday you extended Commerce's data model. Today you make that data (and the existing catalog) properly searchable — configuring Solr indexes, running your first full index, and seeing your custom attribute actually show up as a search facet.

---

## 🎯 What You'll Walk Away With
- A completed custom extension, now integrated with search
- A working Solr index configuration, including a custom facet based on yesterday's custom attribute
- The ability to trigger and monitor a full/incremental Solr index job

---

## Part 1: How Solr Fits Into Commerce

Every product search and category filter you've used since Day 3 (including inside Spartacus on Day 16) is backed by **Solr**, not a live database query. Commerce indexes catalog data into Solr on a schedule (or on-demand), and search/filter requests hit that index instead of querying the database directly — much faster at scale, and it's what powers faceted navigation (price range sliders, brand filters, etc.).

### Indexed Types & Facets
Commerce's Solr configuration (`indexed types` and `index configuration` in Backoffice) defines *which* item types and attributes get indexed, and which of those become **facets** — filterable options shown in the storefront's search sidebar. Yesterday's custom `ProductReview` rating is a perfect candidate: index the average rating, expose it as a facet, and customers can filter by "4 stars & up."

### Full vs. Incremental Indexing
- **Full index** — rebuilds the entire Solr index from scratch. Needed after structural changes (like adding a new facet)
- **Incremental (update) index** — only reflects recent data changes, much faster, run frequently (often via CronJob, tying back to yesterday)

---

## 🧪 Hands-On Lab

### Lab 1: Finish the Extension
Complete any loose ends from yesterday's custom extension — confirm your `ProductReview` type is fully built and you have a handful of sample review records imported.

### Lab 2: Add a Custom Facet
In Backoffice's **Solr Index Configuration**, locate the indexed type for your product catalog. Add a new indexed property that pulls in an aggregated value from your `ProductReview` data (e.g., average rating per product), and mark it as a facet.

### Lab 3: Trigger a Full Index
In HAC (or Backoffice's indexing tools), trigger a **full index** run for your updated Solr configuration. Monitor its progress the same way you checked CronJob status back on Day 3/4.

### Lab 4: Verify in the Storefront
Back in your Spartacus storefront (Day 15-17), run a product search or browse a category. Confirm your new rating facet now appears in the filter sidebar, and that filtering by it actually narrows results correctly.

### Lab 5: Break It, Then Fix It
Deliberately misconfigure the facet (wrong field mapping or type), reindex, and observe what breaks in the storefront (facet missing, filter doesn't narrow results, or an indexing error in HAC). Fix the configuration and reindex to confirm it's resolved — the same "break it to understand it" habit from earlier in the program.

---

## ✅ Quick Recap Check

1. Why does Commerce search against a Solr index instead of querying the database directly?
2. What's the practical difference between a full index and an incremental index, and when would you need each?
3. What made your custom `ProductReview` data eligible to become a search facet?
4. How did you confirm (Lab 4) that your new facet was actually working end-to-end, not just configured?
5. What symptom did your deliberate misconfiguration (Lab 5) produce, and how did reindexing fix it?

---

## 👀 Coming Up on Day 20
The finish line — a wrap-up and open Q&A session to tie together everything from infra to storefront to customization.
