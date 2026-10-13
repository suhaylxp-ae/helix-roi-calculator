# Helix Value Calculator

A single-page, public portfolio model for **BMC Helix** value in IT service management, AIOps, and agentic AI. It is built to be honest: ranges instead of a single heroic number, a slow adoption ramp, labour realisation haircuts, and **true net ROI** after licence and services.

Open `index.html` in a browser (or GitHub Pages). There is no build step. Chart.js is loaded from a CDN.

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

To publish on GitHub Pages, push this repo and enable Pages from the `main` branch root.

This is **not** a BMC product, quote, or customer case study. All default inputs are generic examples. Do not put real customer names or data in a public fork.

## What it models

- **Cost and consolidation:** tools you can actually retire, per-server monitoring cost today vs with Helix, and headcount growth you do not hire.
- **Operations:** alert noise (removed first), remaining triage, P1 labour, war rooms, reporting automation.
- **Service desk:** extra deflection beyond today’s self-service, then fewer reassignments on tickets that still reach an agent.
- **AI agents:** Virtual Agent / Employee Navigator, Knowledge Curator, Root Cause Analyzer, Ops Swarmer, Change Risk Advisor — each on/off with its own volume, minutes saved, and annual value.

Currency is USD or AED (`AED = USD × 3.6725`). Horizon is 3 or 5 years.

## Method

1. **Count each saving once, in sequence.**  
   Alert volume after noise reduction is what still gets triaged. Ticket volume after deflection is what still gets reassignment savings.

2. **MTTR is labour, not the outage clock.**  
   P1 value = engineers × hands-on hours × reduction %. Elapsed business downtime is never used in the ROI headline.

3. **Hours cannot exceed the baseline in that area.**  
   If an input implies more hours saved than exist, the model caps the saving and shows a warning.

4. **Labour is not cash.**  
   Freed time is multiplied by a realisation factor: **conservative 50%**, **expected 70%**. Cash items (retired tools, monitoring delta, avoided hires) are not haircut.

5. **Adoption ramp** (applied to benefits, not to licence):  
   Year 1 **25%**, Year 2 **60%**, Year 3+ **90%**.

6. **Cost** = one-time services (month 0) + annual licence × years.

7. **Net ROI** = (total benefit − total cost) / total cost.  
   **Payback month** is the first month where cumulative benefit ≥ cumulative cost, using monthly licence and ramped monthly benefit.

Two scenarios are always shown side by side. They share your operational inputs; they differ on labour realisation.

## Downtime upside (optional, excluded)

If you enter cost per minute of a P1 outage **and** average elapsed P1 minutes, the page shows a separate range. That figure is **never** included in total benefit, net value, net ROI, or payback. Mixing IT labour with business-loss dollars is how ROI models stop being honest.

## Guardrails worth knowing

- Agent values are **example assumptions**. Validate minutes and volumes against BMC’s published figures and your own telemetry. Turn an agent off if that work is already counted on another tab (for example Virtual Agent vs ticket deflection, Root Cause Analyzer vs MTTR hours).
- Monitoring “cost per server with Helix” is incremental estate cost. Do **not** put the Helix licence there; licence already sits in global inputs.
- “What has to be true” lists the three largest modelled drivers so a reviewer can attack the result instead of the formatting.

## Stack

One `index.html` file: HTML, CSS, and JavaScript. [Chart.js](https://www.chartjs.org/) from jsDelivr. Suitable for GitHub Pages.

## Disclaimer

Portfolio demonstration. Not affiliated with or endorsed by BMC Software. Helix is a trademark of BMC Software.
