# Vision — haeusler-wein.ch

## Overview
The website for the Häusler family vineyard (haeusler-wein.ch). A small one-page presence that introduces the winery, lists the current wines with prices, and points visitors at an email address to order or get in touch.

## Target user
Friends, neighbours, and local customers who want to read about the winery and order a bottle. Not a discovery channel and not an online shop — most visitors arrive already knowing the family.

## Primary goal
**Minimal long-term overhead.** All technical decisions are evaluated against this goal first. The site should still be working, with no maintenance, in 3–5 years.

If a change improves "modernity" or elegance but increases complexity or maintenance cost, it is not acceptable.

## Core jobs-to-be-done
1. **Introduce the winery** — short text and a few photos.
2. **Show the current wine(s)** — bottle, vintage, price, ordering email.
3. **Show contact and legal info** — Impressum, Datenschutz, age note.

## Success criteria
- Site is reachable on `haeusler-wein.ch` and `www.haeusler-wein.ch` over HTTPS.
- Editing wine details, prices, or text is a YAML edit and a `git push`.
- Site survives years without dependency upgrades, build breakage, or operational work.

## Non-goals
- E-commerce / shopping cart / online payment.
- Any dynamic or interactive feature requiring JavaScript.
- A CMS or admin UI.
- Multi-language or multi-page expansion (beyond the existing single page).
- Analytics, tracking, or third-party widgets.
