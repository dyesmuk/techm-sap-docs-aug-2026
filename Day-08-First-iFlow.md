# Day 8 — Build Your First iFlow 🏗️

**Duration:** 2.5 hrs
**Vibe check:** All the exploring is done. Today you build a real integration flow from a blank canvas — sender to receiver, with actual data transformation in between. This is the day CPI stops being theory.

---

## 🎯 What You'll Walk Away With
- A real iFlow, built from scratch, deployed and running
- Comfort with the core building blocks: Sender, Receiver, Content Modifier, Message Mapping
- The ability to trigger an integration and trace it through Monitor

---

## Part 1: The Anatomy of an iFlow

Every iFlow, no matter how complex, boils down to the same shape:

```
[Sender] → [Processing Steps] → [Receiver]
```

- **Sender** — where the message enters the flow (an external system calling an endpoint, a scheduled timer, a message queue)
- **Processing steps** — the actual work: transforming data, routing based on conditions, enriching content
- **Receiver** — where the processed message ends up (another API, a database, a file)

### Two Steps You'll Use Constantly

**Content Modifier** — the Swiss Army knife of iFlow steps. Use it to set/change headers, properties, or the message body itself. Think of it as "edit the message as it passes through."

**Message Mapping** — visually maps fields from a source data structure to a target structure (e.g., Commerce's order format → the format an external shipping API expects). No manual field-by-field code — you draw the connections.

---

## 🧪 Hands-On Lab

### Lab 1: Create the iFlow Shell
- In **Cloud Integration → Design**, create a new **Integration Package** (or use one from earlier)
- Inside it, create a new **Integration Flow** — name it something like `demo-order-sync`

### Lab 2: Configure Sender & Receiver
- Add an **HTTPS Sender** adapter — this is the entry point that'll accept an inbound call
- Add an **HTTPS Receiver** adapter pointing to a test endpoint (use a mock endpoint service like `https://httpbin.org/post`, or your sample OCC endpoint)

### Lab 3: Add a Content Modifier
- Drop a **Content Modifier** step between sender and receiver
- Add a header (e.g., `X-Source: sap-commerce`) and a property that captures part of the incoming payload

### Lab 4: Add Message Mapping
- Add a **Message Mapping** step
- Define a simple source structure (e.g., an order object with `orderId`, `customerName`, `total`) and map it to a target structure with renamed/restructured fields
- This is where you'll see the drag-and-connect mapping UI in action

### Lab 5: Deploy & Trigger
- **Deploy** the iFlow
- Once deployed, trigger it manually:
  ```bash
  curl -X POST "https://<your-cpi-runtime-url>/http/demo-order-sync" \
    -H "Content-Type: application/json" \
    -d '{"orderId": "1001", "customerName": "Jane Doe", "total": 249.99}'
  ```

### Lab 6: Monitor Execution
- Go to **Monitor → Message Processing**
- Find your run — check the status (Completed/Failed), and open it to see the message payload at each step of the flow. Watch how the Content Modifier and Message Mapping each transformed the message along the way.

---

## ✅ Quick Recap Check

1. What are the three core parts every iFlow has, regardless of complexity?
2. What's the practical difference between what a Content Modifier does vs. what Message Mapping does?
3. Why might you use a mock endpoint (like httpbin) instead of a real receiver while building/testing?
4. If your iFlow shows "Failed" in Monitor, what's the first thing you'd check?
5. What did triggering the flow via `curl` actually simulate, in real-world terms?

---

## 👀 Coming Up on Day 9
We build a proper REST integration end-to-end — SAP Commerce → CPI → an external shipping API — complete with JSON transformation and Postman testing.
