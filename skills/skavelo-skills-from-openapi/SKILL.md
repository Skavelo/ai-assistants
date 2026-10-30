---
name: skavelo-skills-from-openapi
description: Turn an OpenAPI or Swagger spec into Skavelo skills, lookups that read a user's own data and actions that change it after they approve. Use when someone wants Skavelo to answer questions about a user's account, or do tasks for them, using their API.
---

# Skills from an API spec

Skavelo skills call the product's own API from the user's browser, with the user's session. **Lookups** (GET) read data so Skavelo can answer "which of my invoices are overdue?". **Actions** change something, and the user approves each one first.

## Steps

1. Get the agent with `list_agents`, and the spec's address or text from the person. Pasted text must be under about 200 KB; for larger specs, use the address.
2. `preview_skills_from_openapi` with the agent's ID and the spec. Nothing is saved yet.
3. `list_skills`, so you don't suggest one that already exists.
4. Recommend a short list, not everything in the spec. Good candidates:
   - Lookups for what users ask about their own account: status, totals, recent items, limits.
   - Actions for routine tasks users ask for help with, with clear inputs.
   - Leave out admin, billing, bulk and destructive operations unless the person asks for them by name.
5. For each one, check the description says **when** Skavelo should use it, in a sentence a user's question would match. Rewrite it if the spec's summary is vague.
6. Show the list and ask which to create.
7. `create_skill` for each one picked. Skills are created switched off.
8. Tell the person:
   - Lookups can be switched on with `update_skill` (`enabled: true`) if they ask.
   - Actions must be switched on in the Skavelo dashboard, under the agent's Skills, after someone checks them.
   - Their plan limits how many skills can be switched on at once.
