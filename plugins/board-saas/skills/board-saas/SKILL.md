---
name: board-saas
description: Run a hosted AI board meeting on a decision with the Board as a Service MCP tools. Use when the user wants advisors, a board, a second opinion or a structured debate on a business decision (pricing, hiring, fundraising, a launch, a pivot, build vs buy), or asks to read, share or list past board meetings.
---

# Board as a Service

The Board as a Service MCP server (`https://board.saas.pit.world/mcp`) runs a
board meeting on a decision brief: five AI advisors (CFO, Growth Marketer,
Operator, Founder-Time Strategist, Contrarian Investor) give verdicts and
debate, then a chair writes the minutes. The advisors are AI models running on
open models on the [c0mpute](https://c0mpute.com) network, not real directors.
The first call opens a browser to sign in.

1. Write a brief with the decision, at least two options ("do nothing" counts)
   and the constraints (budget, time, team). Add `company_data` (cash, burn,
   MRR, churn, headcount) if the user has it.
2. Call `run_meeting` with the brief. A meeting takes about 2 to 6 minutes.
   - `needs_clarification`: show the chair's questions, then call
     `clarify_meeting` with the user's answers.
   - `awaiting_payment`: the first meeting per account is free, later ones are
     $9; give the user the `checkout_url` and wait for them.
3. Poll `get_meeting` (with `brief: true` for a summary) until `done`, then
   give the user the recommendation, the vote, the strongest dissent and the
   `report_url`.

Reports are private. `share_meeting` makes a read-only link, `list_shares` and
`revoke_share` manage links, `list_meetings` lists past meetings and
`get_account` shows credits left.

Prefer to run the board locally inside Claude Code instead? Install the
`boardroom` plugin from this marketplace and run `/boardroom:meet`.
