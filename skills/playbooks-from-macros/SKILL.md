---
name: skavelo-playbooks
description: Turn support macros, runbooks or troubleshooting docs into Skavelo playbooks, the checks Skavelo runs when a user reports a problem, and what to do for each finding. Use when someone wants Skavelo to troubleshoot an issue the way their support team does.
---

# Playbooks from support macros

A playbook tells Skavelo how to work out a kind of problem: when it applies, what to check, and what to do for each finding, including when to hand off to a person.

## Steps

1. Get the agent with `list_agents`, and the macro, runbook or doc from the person.
2. `list_playbooks` so you don't duplicate one. `list_skills` and `list_walkthroughs` too: checks can use lookups, and outcomes can point to walkthroughs.
3. Draft the playbook:
   - **name:** the problem, like "Invoice emails not arriving".
   - **when:** what users say or see when it applies, 10 to 600 characters.
   - **checks** (up to 10), each one of:
     - `lookup`: read their data with a lookup skill (give its `skillId`).
     - `screen`: something Skavelo can see on the page, like an error message.
     - `ask`: a question for the user.
   - **outcomes** (up to 10): each `finding` with the `action` to take, and a `workflowId` when a walkthrough shows the fix.
   - **handoff:** when to pass the user to a person.
4. Show the draft, then `create_playbook`. New playbooks start switched off.
5. Suggest `set_playbook_status` with `testing`, so the team can try it with Try it in the dashboard before users see it. Switch it `on` only when the person asks.

Playbooks need an owner or admin, and plans limit how many can be switched on.
