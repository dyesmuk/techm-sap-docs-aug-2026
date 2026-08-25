# Day 13 — Talking to S/4HANA via OData 📊

**Duration:** 2.5 hrs
**Vibe check:** Day 5 gave you a first peek at OData. Today you go properly hands-on — real GET operations against your S/4HANA sandbox, with filtering, sorting, and pagination, the exact skills you'd use to pull product and customer data into any consuming system (including Commerce).

---

## 🎯 What You'll Walk Away With
- Comfort constructing OData queries from scratch (not copy-pasting from docs)
- Real experience with `$filter`, `$orderby`, `$top`, `$skip` against live sandbox data
- A clear sense of how this data would flow into an integration like the ones you built Day 8-9

---

## Part 1: OData Query Basics, Refreshed

Quick recall from Day 5: OData is REST-based, self-describing (via `$metadata`), with built-in query capabilities. Today's the day you actually use those query capabilities properly.

| Parameter | What It Does | Example |
|---|---|---|
| `$filter` | Narrow results by a condition | `$filter=Price gt 100` |
| `$orderby` | Sort results | `$orderby=Price desc` |
| `$top` | Limit number of results | `$top=10` |
| `$skip` | Skip N results (pagination, paired with `$top`) | `$skip=20` |
| `$select` | Return only specific fields (lighter payloads) | `$select=ProductID,Price` |

**Why this matters for real integrations:** pulling *everything* every time is wasteful and slow. A well-built integration filters and paginates at the source, not by fetching everything and filtering client-side.

---

## 🧪 Hands-On Lab

### Lab 1: Product Retrieval
```bash
curl "https://<your-s4hana-host>/sap/opu/odata/sap/<ProductService>/Products?\$top=5"
```
Grab a handful of product records. Note the field names — you'll reference them for filtering next.

### Lab 2: Customer Retrieval
```bash
curl "https://<your-s4hana-host>/sap/opu/odata/sap/<CustomerService>/Customers?\$top=5"
```
Same idea, different entity set.

### Lab 3: Filtering
Pick a real field from Lab 1 (e.g., a price or category field) and filter on it:
```bash
curl "https://<your-s4hana-host>/sap/opu/odata/sap/<ProductService>/Products?\$filter=Price gt 500"
```
Try a second filter using a different operator (`eq`, `lt`, `ge`) and confirm results actually narrow down correctly.

### Lab 4: Sorting
```bash
curl "https://<your-s4hana-host>/sap/opu/odata/sap/<ProductService>/Products?\$orderby=Price desc&\$top=5"
```
Confirm the top 5 are genuinely the highest-priced ones — this is a good sanity check to build the habit of actually verifying, not just assuming, a query worked.

### Lab 5: Pagination
```bash
curl "https://<your-s4hana-host>/sap/opu/odata/sap/<ProductService>/Products?\$top=5&\$skip=0"
curl "https://<your-s4hana-host>/sap/opu/odata/sap/<ProductService>/Products?\$top=5&\$skip=5"
```
Confirm the second call returns a *different* set of 5 — that's page 2. This is exactly the pattern you'd use to page through a full catalog without pulling it all in one shot.

### Lab 6: Combine Everything
Write a single query that filters, sorts, and paginates at once — e.g., "top 5 most expensive products under a category, sorted descending, page 2." This mirrors a real-world request shape almost exactly.

---

## ✅ Quick Recap Check

1. What does `$metadata` give you that helps you construct queries like the ones above?
2. Why is filtering/pagination at the source (via OData query params) better than pulling everything and filtering afterward?
3. What's the combination of parameters you'd use to implement "page 3, 10 results per page"?
4. If a consuming system (like Commerce) only needed product ID and price, which parameter would trim the response down?
5. How would today's OData skills plug into the CPI iFlow pattern you built on Day 8-9?

---

## 👀 Coming Up on Day 14 & 15
We shift gears entirely — into the **storefront**. Spartacus architecture, Angular fundamentals, and getting Spartacus installed and running.
