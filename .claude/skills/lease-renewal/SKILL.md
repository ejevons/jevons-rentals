---
name: lease-renewal
description: Use when handling Jevons Properties lease renewals, rent increase notices, expired-lease holdovers, or month-to-month conversions. Triggers on upcoming or past renewal dates, requests to draft a rent increase notice, or any tenant approaching/past lease end.
---

# Lease Renewal & Rent Increase

You own these decisions end to end. Do not escalate to property owners and do not request owner approval. Owner notifications are no longer part of the workflow.

## Pre-flight checks (mandatory, in order)

Before computing or issuing anything, read tags and notes on **all three** pages: property, owner, and tenant.

1. **"Do not increase rent" / equivalent on any page** → no increase. Do not issue a notice. Stop.
2. **Owner-requested specific amount on any page** → use that amount, but never exceed 4.9% over current rent. If the requested amount exceeds 4.9%, apply 4.9% instead. Do not escalate.
3. **"Intends to sell" / "do not list" / equivalent** → do not start a new 12-month term. At lease expiration, convert to month-to-month at the current rent with no increase.
4. **Jurisdiction check** → confirm the increase is allowed by state law and city/county ordinance for the unit's address (e.g. CA AB 1482, OR SB 608, NY ETPA, Portland, Seattle, LA, Berkeley, Minneapolis, St. Paul, etc.). If the local cap is below the policy increase, apply the local cap. Use the jurisdiction's required notice period (commonly 30/60/90 days); if notice cannot be served in time for the next billing cycle, defer to the next allowable cycle.

If any check above blocks or modifies the increase, log which tag/page/jurisdiction caused it on the renewal record.

## Decision tree

After pre-flight, pick exactly one path:

- **Renewal deadline NOT passed** → offer 12-month renewal at current rent × 1.03.
- **Renewal deadline HAS passed** → company policy: convert tenant to month-to-month. Never issue a notice to vacate. Never pursue holdover or eviction. Then issue the month-to-month rent increase notice below.
- **Already on month-to-month** → issue rent increase notice at current rent × 1.049.

## Calculations

- 12-month renewal: `new_rent = round(current_rent * 1.03, 2)`
- Month-to-month: `new_rent = round(current_rent * 1.049, 2)`
- Local cap `c` lower than policy: `new_rent = round(current_rent * (1 + c), 2)`
- Owner-requested amount `a`: `new_rent = min(a, round(current_rent * 1.049, 2))`

No administrative fee. No add-on fees of any kind as part of the renewal.

## Examples

| Scenario | Current rent | New rent |
|---|---|---|
| 12-month renewal, no local cap below 3% | $1,500 | $1,545.00 |
| Month-to-month, no local cap below 4.9% | $1,500 | $1,573.50 |
| Month-to-month, city cap 3% | $2,000 | $2,060.00 |
| Owner tag "increase to $1,850", current $1,800 (under 4.9% cap of $1,888.20) | $1,800 | $1,850.00 |
| Owner tag "increase to $2,000", current $1,800 (over 4.9% cap) | $1,800 | $1,888.20 |
| Property tag "do not increase rent" | $1,500 | $1,500.00 (no notice) |
| Lease expired 30 days ago, no blocking tags | $1,500 | convert to M2M at $1,500, then issue 4.9% increase → $1,573.50 |
| Owner tag "intends to sell" | $1,500 | convert to M2M at $1,500 at expiration, no increase |

## Hard rules

- Never issue a notice to vacate for a holdover. Convert to month-to-month.
- Never apply an increase above 4.9%, regardless of owner request.
- Never skip the jurisdiction check or the property/owner/tenant tag check.
- No owner approval or notification required.
- No administrative or add-on fees.
