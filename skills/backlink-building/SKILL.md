---
name: backlink-building
description: Negotiate backlink placements with site owners who have replied to Mentiohunt outreach — checks whether their site is actually a good fit for the user's product, figures out what the owner wants in exchange for the link, and drafts a counter-offer (testimonial, reciprocal link, comped access, guest content, etc.) for the user to review before anything is sent. Use this whenever the user mentions Mentiohunt opportunities or replies, negotiating a guest post or link placement, a site owner asking for payment or something in exchange for a backlink, working through an outreach/prospect reply queue, or asks things like "what do these people want" or "check my opportunities."
---

# Backlink Negotiator

Mentiohunt automates backlink discovery and outreach up through a prospect's first reply. Everything after that — reading what the site owner actually wants, deciding whether the site is worth it, and negotiating terms — is left to the user. This skill is that missing step.

The core judgment call here isn't mechanical: a reply saying "sure, $150 for a dofollow link" means something different from a resource-page editor asking "can you also link back to us?" Read each thread for what's actually being asked, not just keywords, and treat the two reference files below as judgment aids, not lookup tables to pattern-match against.

## Workflow

### 1. Find the product being promoted

Before anything else, work out what product/site this negotiation is for and what it can credibly offer a site owner (testimonials, a free/comped account, a reciprocal link, co-marketing, guest content, etc.). Get this from context, not from the user:

1. Check the current working directory / codebase first — a README, `package.json` description, marketing copy, docs, or landing page usually says what the product is and who it's for.
2. If that's not conclusive, query the Mentiohunt MCP tools for account and product data (account details, tracked products/sites, tracked pages). If Mentiohunt's MCP tools aren't loaded yet, they're likely deferred — search for them (e.g. `ToolSearch` with a query like "mentiohunt") before concluding they're unavailable. If no Mentiohunt MCP connection exists at all, tell the user to set one up per `https://mentiohunt.com/agents.txt` before you can pull live opportunities.
3. Only if both of those come up empty, ask the user directly for a short product description, target audience, and what they're able to offer site owners in return for a link.

Don't skip to step 3 just because step 1 takes an extra look around the filesystem — that's the whole point of trying it first.

### 2. Pull opportunities with a live reply

Use the Mentiohunt MCP read-only tools to fetch opportunities that already have a reply from the site owner (not brand-new or merely-contacted ones — those don't need negotiation yet). Filter by product and status where the tools support it. If the user asked about a specific domain or opportunity, just fetch that one.

### 3. Check whether the site is actually a good fit

Mentiohunt's own domain rating and fit score are a starting signal, not the final word — they're generic, not scored against this specific product. For each opportunity, fetch the actual prospect page (and the surrounding site if the page alone doesn't tell you enough) and judge:

- **Topical relevance** — would this product's actual target audience plausibly read this page?
- **Editorial quality** — real editorial content and engaged audience, versus thin/templated pages, obvious PBN or link-farm patterns (rotating outbound links, no real content, disconnected niches).
- **Placement type** — a resource page, roundup, directory listing, and guest post all carry different effort/value tradeoffs; factor that in alongside the DR.

Form your own view here before reading the reply — you want to know whether this is worth pursuing *before* you get anchored on what the owner is asking for.

### 4. Read the thread and work out the actual ask

The reply thread is free text — there's no field that says "wants: $150." Read it and classify what's being requested: a flat payment, a paid guest post, a reciprocal link back, a product mention/swap, a flat refusal of free placements, or something else. Note the exact terms (price, conditions, deadline) if any are given.

### 5. Decide: accept, counter, or decline

Weigh the fit assessment from step 3 against the ask from step 4. Read `references/negotiation-rubric.md` for how to combine these into a recommendation — it covers cases like a strong-fit site asking for a reasonable non-cash exchange (usually accept), a weak-fit site asking for payment (usually decline), and the murkier cases in between where the right call depends on how much the placement is actually worth to this product.

### 6. Pick what to pitch

If the answer isn't a plain yes, decide what to offer instead of or alongside it. Read `references/pitch-menu.md` for options (testimonials, reciprocal links, comped access, co-marketing, guest content, expert quotes/data) and guidance on which tend to land with which type of site. Only pitch things the product can actually deliver — check back against what step 1 established.

### 7. Draft the reply

Write a reply email that:
- Responds directly to what they asked for, rather than a generic template.
- References something specific from their site or their message, so it doesn't read as a form letter.
- Matches their tone (a casual blogger and a formal editor warrant different registers).
- States the counter-offer plainly if there is one.

### 8. Always stop for approval before sending

Present the fetched context, your fit assessment, the interpreted ask, your recommendation with reasoning, and the drafted reply to the user. Do not call a send/reply tool (e.g. `send_prospect_reply`) on your own initiative under any circumstances — sending contacts a real person and can't be undone, so it needs explicit per-message approval every time, even if the user approved a similar message earlier in the session. Once the user approves and you send it, update the opportunity's status via the Mentiohunt MCP tool to reflect the outcome (e.g. negotiating, accepted, declined).
