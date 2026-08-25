# Day 16 — Building the Homepage & Product Pages 🏠

**Duration:** 2.5 hrs
**Vibe check:** Storefront's running — now let's actually build on it. Today's about understanding how OCC data becomes UI, theming it to look less generic, and making it not fall apart on a phone screen.

---

## 🎯 What You'll Walk Away With
- Clarity on how Spartacus components pull data via OCC under the hood
- A themed storefront that doesn't look like the out-of-the-box default
- A working, responsive product listing/detail page

---

## Part 1: OCC Integration, From the Component Side

Yesterday you traced a product from OCC call to rendered UI. Today, the reverse direction: Spartacus components (like `ProductListComponent`, `ProductDetailsComponent`) call into Spartacus's own service layer, which wraps the OCC calls you've been making manually all program. You're not writing new API integration code — you're customizing how already-integrated data gets *displayed*.

### Theming
Spartacus ships with a default look, driven by SCSS variables and component-level styles. Real projects almost always theme it — brand colors, fonts, spacing — without touching the underlying component logic. This separation (logic vs. presentation) is exactly why Angular's component architecture (Day 14) makes this manageable.

### Responsive Design
E-commerce traffic skews heavily mobile. Spartacus's layout components are built with responsive breakpoints already in mind — your job is usually adjusting/extending them, not building responsive behavior from scratch.

---

## 🧪 Hands-On Lab

### Lab 1: Customize the Theme
In your Spartacus project's SCSS config (`styles.scss` or a dedicated theme file), override a few core variables — primary color, font family, header background. Rebuild and confirm the storefront visibly reflects your changes.

### Lab 2: Build Out the Homepage
Using SmartEdit (from Backoffice/CMS) or component config, add/rearrange a homepage content slot — a banner, a featured product carousel, or a promotional tile. Confirm it renders on the live storefront after refresh.

### Lab 3: Customize a Product Page Element
Pick the product detail page and make one visible customization — reorder where the price/add-to-cart button sits, or add a custom badge/label component that reads a product attribute (e.g., "In Stock" from your sample data).

### Lab 4: Responsive Check
Open browser dev tools, toggle to a mobile viewport size, and navigate the homepage + product page. Note what breaks (if anything) vs. what already adapts cleanly. Pick one broken element and adjust its CSS to behave properly at the mobile breakpoint.

### Lab 5: Trace Data Again
For the badge/custom element you added in Lab 3, confirm in the Network tab that its value is genuinely coming from the OCC product response, not hardcoded — tie it back to real sample data.

---

## ✅ Quick Recap Check

1. What's the relationship between Spartacus components and the OCC calls you've made manually since Day 3?
2. Why does separating logic (components/services) from presentation (SCSS/theming) make real-world customization easier?
3. What tool did you use to modify homepage content, and where does that content actually live?
4. What responsive issue (if any) did you find in Lab 4, and how did you fix it?
5. Why is it important to confirm a UI element is pulling from real data (Lab 5) rather than assuming it is?

---

## 👀 Coming Up on Day 17
We finish the storefront build with a working **shopping cart** — the piece that ties product browsing to an actual purchase flow.
