# Skavelo for AI assistants: MCP server, skills and Claude Code plugin

[Skavelo](https://skavelo.com) is an AI guide for web products: it learns your app on its own, answers your users' questions inside it, and shows them the way on their own screen.

This repository connects your AI assistant to Skavelo and teaches it the common setup jobs.

- **The MCP server:** `https://api.skavelo.com/mcp`, with OAuth sign-in. The first time you use it, Skavelo opens in your browser so you can approve the connection.
- **Five skills:**

| Skill | What it does |
| --- | --- |
| `skavelo-needs-attention` | Works through answers users rated not helpful, questions Skavelo couldn't answer and reported problems, and fixes each with a note, walkthrough or playbook |
| `skavelo-skills-from-openapi` | Turns an OpenAPI or Swagger spec into lookups and actions, created switched off |
| `skavelo-walkthroughs` | Writes and improves walkthroughs from the product map, and offers them at the right moment |
| `skavelo-playbooks` | Turns support macros and runbooks into troubleshooting playbooks |
| `skavelo-agent-review` | Reviews an agent's setup and suggests what to improve |

## Claude Code

```
/plugin marketplace add skavelo/ai-assistants
/plugin install skavelo@skavelo
```

Then run `/mcp`, choose **skavelo** and sign in. Ask something like "Review my Skavelo agent."

## Other assistants

Add `https://api.skavelo.com/mcp` as a remote MCP server; the [setup guide](https://help.skavelo.com/docs/developers/mcp-server) has the steps for Claude, ChatGPT, Cursor and VS Code. Assistants that support skills in the `SKILL.md` format can use each folder in `skills/` as it is.

## What an assistant can and can't do

It acts as the person who connected it, with their role, and can be connected read only. It can't delete anything, skills it creates start switched off, and test accounts, the handoff email address, file uploads and the widget icon stay in the Skavelo dashboard. Everything it creates is labelled with its name in the dashboard.

## License

MIT
