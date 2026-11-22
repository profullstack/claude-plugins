---
name: cheapestwayz
description: Find the cheapest way to get something done with the CheapestWayz MCP tools, compare DIY, online and local-business costs, request quotes from local businesses, or get a CheapestWayz referral link and earnings. Use when the user asks for the cheapest or least expensive way to do, fix, buy or get something, wants to compare doing it themselves against buying or hiring, or asks about their CheapestWayz referral link or commissions.
---

# CheapestWayz

The CheapestWayz MCP server (`https://cheapestwayz.com/mcp`) holds questions
like "What is the cheapest way to fix a leaking faucet?" with priced methods of
three kinds: DIY, online and local business. Methods are ranked by cost only.

1. Call `find_cheapest_way` with the task in plain words. It returns matching
   questions with the cheapest method overall and per kind, costs in US cents.
   Prices are member estimates unless marked source-linked: say so, and say when
   the author is an AI agent.
2. For detail, `get_question` or `compare_methods` (total or upfront cost).
3. Nothing fits? Offer to post the question with `ask_question` (sign-in).
4. Local help: `search_local_providers`, then `request_quotes`,
   `select_quote_recipients` and `send_quote_requests`. Sending shares the
   user's name and email with the businesses they chose, so show exactly what
   goes where and get a clear yes first.

Store links in results go through a click-out that may carry an affiliate tag;
when you pass one on, mention that CheapestWayz may earn a commission.

**Earning.** `get_referral_link` gives the user a link for the site, a question
or a method; `get_earnings` shows clicks, leads and commissions. A referral
earns 60% of the paid lead fees and affiliate commissions it brings in, paid to
the user's CoinPay wallet. These tools need sign-in: the first call opens a
browser to sign in with an email link or with CoinPay. Referrals never change
rankings.
