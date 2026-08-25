# Day 15 — Spinning Up Spartacus 🎬

**Duration:** 2.5 hrs
**Vibe check:** Today the storefront becomes real. You'll install Spartacus, point it at your SAP Commerce OCC backend, and see actual sample-data products render in a browser — the payoff for everything since Day 3.

---

## 🎯 What You'll Walk Away With
- A running Spartacus storefront, connected to your live sample Commerce instance
- Comfort navigating the Spartacus project structure
- Confirmation that what you see in the browser traces directly back to the OCC calls and sample data you've been working with all along

---

## Part 1: What "Installing Spartacus" Actually Involves

Unlike yesterday's scratch Angular project, Spartacus setup follows a defined path via the Spartacus schematics (an Angular CLI add-on that scaffolds the whole thing for you). The key configuration you'll need going in:

- **Base URL** — your SAP Commerce OCC backend host
- **Base Site** — which site (from your sample data) the storefront should represent
- **OCC prefix/version** — matches the API path structure you've been calling manually since Day 3

Getting these three right is 90% of "why isn't my storefront showing data" troubleshooting.

---

## 🧪 Hands-On Lab

### Lab 1: Scaffold a New Spartacus App
```bash
ng new my-storefront --style=scss --routing=false
cd my-storefront
ng add @spartacus/schematics
```
Follow the prompts — when asked for your OCC backend base URL, use your SAP Commerce host from earlier labs (same one you used in Day 3/9 Postman calls).

### Lab 2: Configure the Base Site
Locate the generated `app.module.ts` (or the Spartacus config file, depending on version) and confirm the `context.baseSite` matches the sample site you explored in Backoffice on Day 3. If it's wrong, the storefront will run but show no products — a great first debugging lesson.

### Lab 3: Run It
```bash
npm start
```
Open the app in your browser. You should see the storefront shell load — header, footer, and (if base site/backend config is correct) actual product data from your sample catalog.

### Lab 4: Trace a Product Back to OCC
Pick a product visible on the storefront homepage. Open your browser's dev tools → Network tab, refresh, and find the actual OCC API call that fetched it. Compare the response shape to the raw `curl`/Postman calls you made on Day 3 — same API, now rendered as real UI instead of raw JSON.

### Lab 5: Break the Config on Purpose
Temporarily change the `baseSite` to a nonexistent value, restart, and observe what happens (likely an empty page or errors in the console/network tab). Fix it back. This "break it, see the failure, fix it" loop is exactly how you'll debug configuration issues in the real world.

---

## ✅ Quick Recap Check

1. What are the three key config values that determine whether Spartacus can talk to your Commerce backend?
2. What did you actually run to add Spartacus to a fresh Angular project?
3. In Lab 4, how did you confirm the storefront's product data traces back to the same OCC API you used manually on Day 3?
4. What symptom would you expect if the `baseSite` config were wrong, based on Lab 5?
5. Why is deliberately breaking a config (Lab 5) a useful exercise, even though it feels counterintuitive?

---

## 👀 Coming Up on Day 16 & 17
We start actually building — homepage development, product pages, theming, responsive design, and a working shopping cart.
