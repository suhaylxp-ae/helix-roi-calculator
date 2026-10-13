# Helix Value Calculator

**Disclaimer.** Independent personal project by Suhayl Patel. Not a BMC or BMC Helix tool, not a quote, and not a customer result. Views are my own. All defaults are illustrative assumptions.

A single-page, public portfolio model for **BMC Helix** value. **Simple mode** (default) is a 60-second estimate from a role and a handful of numbers. **Advanced mode** is the full nine-module engine. Cash vs released capacity vs optional upside stay separate; labour realisation (50% / 70%) is the default haircut; **true net ROI** is after licence and services.

Open `index.html` in a browser (or GitHub Pages). There is no build step. Chart.js is loaded from a CDN.

Live: https://suhaylxp-ae.github.io/helix-roi-calculator/

## Open locally

From this folder:

```bash
open index.html
```

Or start a tiny local server (needed if a browser blocks Chart.js on `file://`):

```bash
python3 -m http.server 8080
```

Then visit http://127.0.0.1:8080/

## How the page is structured

1. A sticky disclaimer at the top of every view.
2. **Simple mode:** pick CIO / Infrastructure / Service-Ops, enter up to six figures, get a conservative-to-expected value card. Copy link, print a one-pager, or open Advanced at the same values.
3. **Advanced mode:** product picker, per-module licence, derived inputs you can override, overlaps, and methodology. AI Agents only counts if ITSM and/or Change is selected.
4. **Global settings:** currency stored in USD; loaded hourly rates; selected-module licence + services (40% of year-1 licence); 3 or 5 year horizon; Conservative 50% and Expected 70% labour realisation; ramp 50 / 85 / 100%; optional Advanced redeploy % (default 100%).

This is **not** a BMC product, quote, or customer case study. Do not put real customer names or data in a public fork.

## Method

1. **Count each saving once, in sequence.**  
   Alert volume after noise reduction is what still gets triaged. Ticket volume after deflection is what still gets reassignment savings.

2. **Three ledgers.**  
   - **Cash** — budget items (retired tools, monitoring delta, avoided hires). Not haircut.  
   - **Capacity** — labour hours × role rate. Realisation (50% conservative / 70% expected) is applied when packing each scenario.  
   - **Upside** — shown, **never** in net ROI or payback (for example P1 business downtime).

3. **Redeployed capacity.**  
   Default **100%**: all realised labour is in ROI. The Advanced field can lower this if time will not be reused. Realisation (50% / 70%) is the single default haircut.

4. **MTTR is labour, not the outage clock.**  
   P1 labour = engineers × hands-on hours × reduction %. Elapsed business downtime is upside only.

5. **Hours cannot exceed the baseline in that area.**  
   If an input implies more hours saved than exist, the model caps the saving and shows a warning.

6. **Adoption ramp** (benefits, not licence): Year 1 **50%**, Year 2 **85%**, Year 3+ **100%**.

7. **Cost** = one-time services (month 0) + (sum of selected module licences) × years.

8. **Overlaps are subtracted, not only warned.** Patch cycles come out of the Change volume when TSSA is on; network alerts come out of the AIOps count; auto-remediated events come out of the post-suppression triage pool; ITSM extra deflection is capped at 40% even if Employee Navigator is off. Each deduction is listed once under **Overlaps handled**.

9. **Net ROI** = (ROI benefit − total cost) / total cost, where ROI benefit = ramped cash + ramped (capacity × realisation), with redeploy defaulting to 100%. Conservative and Expected are both shown.  
   **Payback month** is the first month where that cumulative benefit ≥ cumulative cost.

10. **Credibility warning** if modelled net ROI is above **5×**.

## Modules

Every numeric default is labelled **illustrative assumption**. Hours saved on a line cannot exceed that line’s baseline.

- **ITSM:** extra deflection first, then handle-time cut on remaining L1/L2 tickets (capacity).
- **AI Agents:** extra combined deflection (capped at 40%), routing, knowledge, change-risk, and reporting (capacity, after realisation).
- **Change & Problem:** effort and problem hours (capacity); avoided failures are cash if a unit cost is entered, otherwise **capacity** (rework hours). Patch changes are subtracted when TSSA is also on.
- **AIOps:** suppress noise first, then auto-remediation on the remaining pool, P1 labour, war rooms, service models (capacity). Downtime is upside only. Network alerts are subtracted when Network is also on.
- **Network:** onboarding and false-alert suppression (capacity). Those alerts are removed from the AIOps count when both modules are on.
- **CMDB/Asset:** update and audit hours (capacity); reclaim cash only if filled. Breach risk is unvalued upside text.
- **TSSA:** patch, vulnerability, and compliance hours (capacity). Patch cycles are subtracted from Change volume when both modules are on.
- **BHCO:** cloud / hardware / storage **cash**; planning hours capacity; capacity outages upside.
- **ESM:** non-IT cases — deflection first, then rework and status-enquiry cuts (capacity).

## Stack

One `index.html` file: HTML, CSS, and JavaScript. [Chart.js](https://www.chartjs.org/) from jsDelivr. Suitable for GitHub Pages.

Helix is a trademark of BMC Software.
