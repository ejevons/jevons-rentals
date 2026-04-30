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

- **Renewal deadline NOT passed** → offer 12-month renewal at current rent × 1.03. No administrative fee.
- **Renewal deadline HAS passed** → company policy: convert tenant to month-to-month. Never issue a notice to vacate. Never pursue holdover or eviction. Then issue the month-to-month rent increase notice below.
- **Already on month-to-month** → issue rent increase notice using the month-to-month formula below (rent + $25 admin fee, combined increase capped at 4.9%).

## Calculations

### 12-month renewal
- `new_rent = round(current_rent * 1.03, 2)`
- No administrative fee.

### Month-to-month
Base policy is a 4.5% rent increase plus a $25 monthly administrative fee. The combined increase (rent increase + fee) must not exceed 4.9% of current rent. Because 4.5% + $25 exceeds 4.9% for any rent below $6,250, the cap is the binding constraint in nearly every case.

```
fee = 25.00
combined_cap = current_rent * 0.049
combined_increase = min(current_rent * 0.045 + fee, combined_cap)
rent_increase = combined_increase - fee
new_rent = round(current_rent + rent_increase, 2)
new_total_charge = round(new_rent + fee, 2)
```

The notice must list the new rent and the $25 administrative fee as separate line items.

### Jurisdictional cap
If the local cap `c` is below 4.9%, replace `combined_cap` with `current_rent * c`. The combined total of rent increase plus the $25 fee must stay within `c`. If `current_rent * c < 25`, do not charge the administrative fee — issue the notice with rent capped at `current_rent * (1 + c)` and no fee.

### Owner-requested amount
Owner-requested amount `a`: `new_rent = min(a, round(current_rent * 1.049, 2))`. If the tenant is on month-to-month, the $25 fee still applies, and the combined total of `a` plus the fee must not exceed 4.9% of current rent — reduce `a` if necessary.

## Examples

| Scenario | Current rent | New rent | Admin fee | Total charge |
|---|---|---|---|---|
| 12-month renewal, no local cap below 3% | $1,500 | $1,545.00 | — | $1,545.00 |
| Month-to-month, no local cap below 4.9% | $1,000 | $1,024.00 | $25.00 | $1,049.00 |
| Month-to-month, no local cap below 4.9% | $1,500 | $1,548.50 | $25.00 | $1,573.50 |
| Month-to-month, no local cap below 4.9% | $2,000 | $2,073.00 | $25.00 | $2,098.00 |
| Month-to-month, city cap 3% | $2,000 | $2,035.00 | $25.00 | $2,060.00 |
| Owner tag "increase to $1,850", current $1,800 12-month (under 4.9% cap of $1,888.20) | $1,800 | $1,850.00 | — | $1,850.00 |
| Owner tag "increase to $2,000", current $1,800 12-month (over 4.9% cap) | $1,800 | $1,888.20 | — | $1,888.20 |
| Property tag "do not increase rent" | $1,500 | $1,500.00 | — | $1,500.00 (no notice) |
| Lease expired 30 days ago, no blocking tags | $1,500 | convert to M2M at $1,500, then apply M2M formula → $1,548.50 rent + $25 fee | $25.00 | $1,573.50 |
| Owner tag "intends to sell" | $1,500 | convert to M2M at $1,500 at expiration, no increase, no fee | — | $1,500.00 |

## Hard rules

- Never issue a notice to vacate for a holdover. Convert to month-to-month.
- Never let the combined increase (rent + fees) exceed 4.9% of current rent, regardless of owner request.
- Never skip the jurisdiction check or the property/owner/tenant tag check.
- No owner approval or notification required.
- The $25 administrative fee applies only to month-to-month tenants. 12-month renewals carry no fee.
