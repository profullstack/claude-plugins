---
name: c0mpute-hosting
description: Publish a website on the c0mpute peer-to-peer network with the c0mpute MCP tools. Use when the user wants to host, deploy, publish or share a static site, landing page, HTML file, demo or docs page and get a public URL without a server, or asks to update, list or take down a site they put on c0mpute.
---

# Hosting a site on c0mpute

The c0mpute MCP server (`https://c0mpute.com/api/mcp`) publishes files as a site
on the c0mpute network: content-addressed chunks, at least three self-healing
copies on independent machines, served by every gateway at
`https://gateway.c0mpute.com/s/<site_id>/`. The first call opens a browser to
sign in with CoinPay (a CoinPay DID is required).

1. Build the site as plain files with an `index.html` at the root. Relative
   links only (the site is served under `/s/<site_id>/`).
2. Call `hosting_push` with a `name` (1-63 of a-z, 0-9, `-`) and `files`:
   `[{ "path": "index.html", "type": "text/html", "text": "..." }, ...]`.
   Up to 1 MiB of inline text per push.
3. Poll `hosting_push_status` with the same name every 5-10 seconds until
   `status` is `live`, then give the user the `url`.
4. Push the same name again to ship a new version. `hosting_pushes` lists the
   user's sites; `hosting_push_rm` takes one down.

With no node of their own, sites go through the shared **cloud node**: free,
inline text files only (HTML, CSS, JS, SVG, Markdown), names first come first
served across accounts, up to 5 sites per account. If a name is taken, pick
another. People who run `c0mpute chat connect hosting` on their own machine
publish through it instead, with paid preferred hosts and media files.

Other tools on the same server: `chat` and `list_models` (open models on the
network, billed to the user's compute balance), `promo_video` and
`promo_status` (a 20-40 s promo video for a website).
