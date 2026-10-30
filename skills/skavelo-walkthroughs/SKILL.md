---
name: skavelo-walkthroughs
description: Write or improve Skavelo walkthroughs, the step by step guides Skavelo shows users on their real screen, using the product map Skavelo learned. Use when someone asks for a walkthrough, a guided tour of a task, or to offer one at the right moment.
---

# Walkthroughs

A walkthrough is a named task with steps. Skavelo shows each step next to the real control on the user's screen, across pages.

## Steps

1. Get the agent with `list_agents`.
2. `list_walkthroughs` to see what exists. Skavelo drafts many from learning, so improve one before writing a new one.
3. `list_product_map_pages` to find the screens the task goes through, and the exact names of their buttons and fields.
4. Draft the walkthrough:
   - **Name:** the task as a user would say it, like "Send an invoice".
   - **Steps:** one action each, naming the control exactly as it appears, like "Click New invoice". Add `pageUrlPattern` (like `/invoices/new`) when the step is on a different page.
   - Optional `title` and `details` per step, for context the user needs, like what a field is for.
   - Up to 30 steps. Most good walkthroughs have 3 to 8.
5. Show the draft to the person, then `create_walkthrough` or `update_walkthrough`.
   - When updating, get the walkthrough first and keep each existing step's `id`, so Skavelo keeps where it found that control.

## Offering it at the right moment

Ask whether it should be offered before anyone asks, for example on a user's first visit to a page. If so, `create_walkthrough_offer`:
- **message:** one friendly line, 10 to 120 characters, no links.
- **trigger:** `page`, or `event` with the name the app sends to `Skavelo.event()`.
- **rules:** the pages and people it shows to.

Offers need an owner or admin, and plans limit how many can be switched on.
