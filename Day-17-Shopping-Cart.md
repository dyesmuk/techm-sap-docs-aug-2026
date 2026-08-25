# Day 17 — Shopping Cart, Made Real 🛒

**Duration:** 2.5 hrs
**Vibe check:** Browsing products is only half a storefront. Today's about the part that actually matters commercially — add to cart, update quantities, see totals update live, all wired to real Commerce cart APIs.

---

## 🎯 What You'll Walk Away With
- A working cart flow: add, update, remove, view totals
- Understanding of how Spartacus manages cart **state** (tying back to Day 14's state management discussion)
- Confirmation that cart operations are hitting real OCC cart endpoints, not local mock data

---

## Part 1: Cart State, Properly Understood

Recall Day 14's state management discussion — the cart is the textbook example of *why* centralized state matters. The cart count needs to show correctly in the nav bar, the cart page, and the checkout flow simultaneously — all reading from the same source of truth, all updating reactively when it changes.

### How It Actually Works
- Adding a product triggers a call to Commerce's cart OCC endpoint (creating/updating a cart entry server-side)
- Spartacus's cart service holds the resulting state and exposes it as an observable
- Any component (nav bar badge, cart page, mini-cart dropdown) subscribes to that same observable — update once, reflected everywhere

This is the same DI + service + reactive pattern from Day 14's Angular refresher, just applied to a real, meaningful piece of storefront functionality.

---

## 🧪 Hands-On Lab

### Lab 1: Add to Cart
On a product page, use the "Add to Cart" action. Then:
- Confirm the nav bar cart icon/count updates
- Open dev tools → Network tab, find the actual OCC call that fired (should hit a `/carts/.../entries` endpoint or similar)

### Lab 2: Update Quantity
On the cart page, change a line item's quantity. Confirm:
- The line total and cart total both update
- Another OCC call fired to persist the change (not just a local UI update)

### Lab 3: Remove an Item
Remove a cart line entirely. Confirm the cart count and totals adjust correctly, and check the corresponding OCC call (likely a DELETE).

### Lab 4: Verify Server-Side Persistence
Refresh the entire browser page. Confirm your cart contents survive the refresh — proving the cart lives on the server (via Commerce), not just in local browser/component state that would vanish on reload.

### Lab 5: Multi-Component Consistency Check
With items in your cart, navigate between the homepage, a product page, and the cart page. Confirm the cart count shown in the nav bar stays consistent everywhere, without you manually refreshing anything — that's the shared state/observable pattern from Part 1, working as designed.

---

## ✅ Quick Recap Check

1. Why is the shopping cart such a good real-world example of why centralized state management matters?
2. When you add a product to cart, what actually happens server-side vs. client-side?
3. How did Lab 4 prove the cart isn't just client-side state?
4. What pattern from Day 14 (DI, services, observables) is directly responsible for the nav bar badge staying in sync across pages?
5. If the cart count didn't update in the nav bar after an add-to-cart action, where would you start debugging?

---

## 👀 Coming Up on Day 18 & 19
Back to the backend — customization and enterprise development. Extensions, the type system, CronJobs, business processes, and configuring Solr search.
