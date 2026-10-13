# Helix Value Calculator

**Disclaimer.** Independent personal project by Suhayl Patel. Not a BMC or BMC Helix tool, not a quote, and not a customer result. Views are my own. All defaults are illustrative assumptions.

A single-page, public portfolio model for **BMC Helix** value across ITSM, AIOps, agentic AI, and related operations products. It is built to be honest: cash vs released capacity vs optional upside as separate ledgers, a slow adoption ramp, labour realisation haircuts, and **true net ROI** after licence and services.

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
2. A **product picker**. Only selected modules appear as tabs. Default: **ITSM Service Desk** and **AIOps**. Other products (AI Agents, Change & Problem, Network, CMDB/Asset, TSSA, BHCO, ESM) can be toggled on; most are stubs until the next modelling step.
3. **Global settings:** currency (USD / AED / GBP / EUR with a user-entered rate), stored internally in USD so switching never drifts; loaded hourly rates by role; annual licence; one-time services; 3 or 5 year horizon; Conservative (50%) or Expected (70%) labour realisation; 25 / 60 / 90% adoption ramp; % of released capacity redeployed into ROI (default 50%).
4. A **shared engine**. Each module registers benefit lines tagged `cash`, `capacity`, or `upside`.
5. An outputs panel that scrolls on its own.

This is **not** a BMC product, quote, or customer case study. Do not put real customer names or data in a public fork.

## Method

1. **Count each saving once, in sequence.**  
   Alert volume after noise reduction is what still gets triaged. Ticket volume after deflection is what still gets reassignment savings.

2. **Three ledgers.**  
   - **Cash** — budget items (retired tools, monitoring delta, avoided hires). Not haircut.  
   - **Capacity** — labour hours × role rate × realisation (50% or 70%).  
   - **Upside** — shown, **never** in net ROI or payback (for example P1 business downtime).

3. **Redeployed capacity.**  
   Only the entered % of realised capacity (default 50%) is converted into cash-equivalent ROI. The rest stays visible as capacity.

4. **MTTR is labour, not the outage clock.**  
   P1 labour = engineers × hands-on hours × reduction %. Elapsed business downtime is upside only.

5. **Hours cannot exceed the baseline in that area.**  
   If an input implies more hours saved than exist, the model caps the saving and shows a warning.

6. **Adoption ramp** (benefits, not licence): Year 1 **25%**, Year 2 **60%**, Year 3+ **90%**.

7. **Cost** = one-time services (month 0) + annual licence × years.

8. **Net ROI** = (ROI benefit − total cost) / total cost, where ROI benefit = ramped cash + ramped redeployed capacity.  
   **Payback month** is the first month where that cumulative benefit ≥ cumulative cost.

9. **Credibility warning** if modelled net ROI is above **5×**.

## Placeholder modules

ITSM and AIOps currently carry the working service-desk and operations maths from the first version. Remaining product tabs are structure-only until the next step.

## Stack

One `index.html` file: HTML, CSS, and JavaScript. [Chart.js](https://www.chartjs.org/) from jsDelivr. Suitable for GitHub Pages.

Helix is a trademark of BMC Software.
