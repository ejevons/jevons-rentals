# Jevons Rentals — Static Marketing Site

This repository is the **public marketing site** for Jevons Property Management:
- Domain: rentals.jevonsproperties.com
- Content: `index.html`, `MARKETING-PLAYBOOK.md`, `POSTING-TEMPLATES.md`, `THIS-WEEKS-POSTS.md`, `sitemap.xml`, `CNAME`, `robots.txt`
- Render target: GitHub Pages (static)
- Purpose: rental listings, owner inquiries landing page, SEO

## Wrong-repo guard (read this first)

If you are a Claude Code or remote-agent session that arrived here expecting to author or modify **operational skills, scheduled tasks, MCP configs, lease/maintenance/onboarding policy, AppFolio automation, agent runtime configuration, or any `.claude/skills/` files**: **STOP. You are in the wrong repo.**

This repo has:
- No agent runtime
- No MCP server
- No scheduled-task harness
- No AppFolio integration
- No `.claude/skills/` (and must never gain one — see Hard Rules below)

The Jevons agent runtime lives in [`ejevons/jevons-ops`](https://github.com/ejevons/jevons-ops). All operational skills, scheduled tasks, lease policy, renewal policy, onboarding policy, maintenance policy, and any `.claude/` configuration belong there, in `~/jevons-properties/.claude/skills/` or `.claude/scheduled-tasks/`. The canonical lease-renewal skill is at [`ejevons/jevons-ops:.claude/skills/lease-renewal-coordinator/SKILL.md`](https://github.com/ejevons/jevons-ops/blob/main/.claude/skills/lease-renewal-coordinator/SKILL.md).

If your dispatched task references any of the above operational concerns, **exit with the message "wrong repo — redispatch against ejevons/jevons-ops" and do not commit anything to this repository**. Pushing operational policy here ships it to a public-facing marketing site where it can be mistaken for authoritative guidance, drift from the real canonical version, and may contain content (jurisdictions, notice periods, fee structures) that is wrong for the portfolio Jevons actually operates in.

This guard exists because on 2026-04-30, [PR #1 ("Add lease renewal skill")](https://github.com/ejevons/jevons-rentals/pull/1) merged a complete lease-renewal policy from a misrouted cloud Claude session. The policy contained generic CA/OR/NY jurisdictional content, missed the WA-specific Seattle SMC 7.24 carve-out, and contradicted the canonical lease-renewal-coordinator skill in jevons-ops. It was reverted in [PR #2](https://github.com/ejevons/jevons-rentals/pull/2). Don't repeat the pattern.

## Hard Rules

1. **No `.claude/` directory.** Not skills, not scheduled-tasks, not settings.json, not mcp-config.json, not anything. Operational agent configuration does not belong in a marketing repo.
2. **No operational policy.** Lease, rent, maintenance, eviction, onboarding, application, deposit, renewal, vendor, owner — none of these are authored, edited, or referenced in this repo.
3. **No agent skills.** SKILL.md files belong in `ejevons/jevons-ops:.claude/skills/`.
4. **Authority for any policy change is Enrique Jevons only** (mirrors jevons-ops Hard Constraint #22). A cloud Claude session is not authorized to author policy in any repo without Enrique's approval, and certainly not in this one.

## What this repo does contain

| File | Purpose |
|---|---|
| `index.html` | Static landing page |
| `MARKETING-PLAYBOOK.md` | Marketing strategy + voice guide for listings |
| `POSTING-TEMPLATES.md` | Reusable copy templates for Zillow / social posts |
| `THIS-WEEKS-POSTS.md` | Weekly posting plan (Claude can author/update freely) |
| `sitemap.xml` | SEO |
| `CNAME` | GitHub Pages custom-domain config |
| `robots.txt` | Crawler directives |

Edits to any of the above for marketing/SEO purposes are in scope. Anything else is not.
