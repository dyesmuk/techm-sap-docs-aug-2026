# Day 14 — Meet Spartacus & Angular ⚡

**Duration:** 2.5 hrs
**Vibe check:** New territory — we leave the backend/integration world and step into the storefront. Today's about building the mental model for Spartacus and refreshing the Angular concepts it's built on, before you install and start building tomorrow.

---

## 🎯 What You'll Walk Away With
- A clear picture of what Spartacus is and how it relates to headless commerce (Day 10) and OCC (Day 3)
- A refreshed, practical grasp of the Angular concepts Spartacus leans on hardest
- Hands-on: a small Angular refresher exercise to shake off the rust before tomorrow's real install

---

## Part 1: What Spartacus Actually Is

Remember headless commerce from Day 10? Spartacus is SAP's **reference storefront** — an Angular application that consumes SAP Commerce purely through OCC APIs (the exact same APIs you've been calling since Day 3). It's not magic; it's a well-architected Angular app making the same kind of REST calls you've already made by hand in Postman.

**Spartacus Architecture, in short:**
- **Libraries, not a monolith** — Spartacus is built as a set of Angular libraries (core, storefront UI components, feature libraries like checkout/cart) that you compose together, not one giant app you fork
- **Config-driven** — a lot of behavior (which base site, which OCC backend URL, feature toggles) is controlled through configuration rather than code changes
- **CMS-driven layout** — page structure/content often comes from Commerce's CMS (SmartEdit-managed), not hardcoded in the frontend

---

## Part 2: The Angular Concepts You'll Lean On

Quick, practical refresher — not a full Angular course, just what matters for the next four days:

| Concept | Why It Matters Here |
|---|---|
| **Components** | Every storefront UI piece (product card, cart summary, nav bar) is a component |
| **Modules** | Spartacus's features are organized into Angular modules you import selectively — you don't get everything by default |
| **Services** | Business logic and API calls (talking to OCC) live in injectable services, not components |
| **Dependency Injection (DI)** | How components get access to services without manually instantiating them — Angular wires it up for you |
| **Routing** | Maps URLs (`/product/123`) to the right component/page |
| **Reactive Forms** | Used heavily in checkout, login, address forms — form state managed reactively via RxJS observables, not plain template-driven binding |
| **State Management** | Spartacus uses NgRx-style state under the hood — cart contents, user session, etc. live in a central store rather than scattered across components |

**The throughline:** none of this is Spartacus-specific magic — it's standard Angular architecture, applied to commerce. If Angular fundamentals are solid, Spartacus is "just" a very well-organized Angular app with commerce-flavored components.

---

## 🧪 Hands-On Lab

*No Spartacus install yet — that's tomorrow. Today's lab is a focused Angular refresher using a lightweight scratch project.*

### Lab 1: Component + Service + DI, Minimal Example
In a scratch Angular project (or Stackblitz if you don't have one locally):
- Create a `ProductService` with a method `getProducts()` returning a hardcoded array of sample products
- Create a `ProductListComponent` that injects `ProductService` via its constructor and renders the list
- Confirm DI is working — the component never manually does `new ProductService()`

### Lab 2: Reactive Forms Warm-Up
Build a minimal reactive form (`FormGroup` with a couple of `FormControl`s — e.g., name + email) and:
- Log the form's value on every change (subscribe to `valueChanges`)
- Add a simple required-field validator and show/hide an error message based on validity

### Lab 3: Routing Refresher
Add two routes to your scratch project (`/products` and `/products/:id`), and confirm navigating to a specific ID correctly passes the route parameter into the target component.

### Lab 4: Talk About State
As a group discussion (or written note): in your `ProductListComponent` example, if the cart count needed to be shown in a totally unrelated nav bar component, how would you share that state without prop-drilling through unrelated components? This is exactly the problem Spartacus's state management layer solves.

---

## ✅ Quick Recap Check

1. What does "Spartacus consumes Commerce purely through OCC" actually mean in practice, given what you already know from Day 3?
2. Why does Spartacus ship as a set of composable libraries rather than one monolithic app?
3. What's the role of a service vs. a component in Angular's architecture?
4. Why are Reactive Forms particularly well-suited to something like a checkout flow?
5. What problem does centralized state management solve that plain component-to-component data passing doesn't?

---

## 👀 Coming Up on Day 15
Time to actually install Spartacus and get it talking to your SAP Commerce OCC backend.
