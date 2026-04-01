## Resilient by Design: Storm Infrastructure vs. Emergency Response

## Decision Statement
Should national policymakers invest limited resources in upgraded storm infrastructure to prevent disasters or enhanced emergency response capacity to better manage disasters when they occur, given the increasing frequency and intensity of extreme weather events and the goals of UN Sustainable Development Goal 11 (Sustainable Cities and Communities)?

## Executive Summary
Policymakers around the world face an increasingly critical strategic dilemma that will define their communities' resilience for decades: allocate scarce resources toward preventing disasters through upgraded infrastructure, or toward managing disasters through enhanced emergency response capabilities. Framed through the lens of UN SDG 11 — "Make cities and human settlements inclusive, safe, resilient and sustainable" — and the Sendai Framework for Disaster Risk Reduction 2015–2030, this decision carries profound implications for public safety, economic stability, and equitable urban development as extreme weather events transform from exceptional occurrences into routine threats.

The financial stakes are staggering and accelerating at a global scale. Global economic losses from natural catastrophes reached an estimated $417 billion in 2024, a 15% increase above the decade average, with insured losses hitting a record $154 billion. For the first time in history, 21 separate incidents in a single year resulted in multi-billion-dollar insurance claims. The UNDRR's Global Assessment Report 2025 documents that total disaster costs now exceed $2.3 trillion annually when cascading and ecosystem costs are included — a figure that has grown from $70–80 billion per year (1970–2000) to $180–200 billion (2001–2020) in direct costs alone. This acceleration leaves nations with less time and fewer resources to recover between events, forcing policymakers to make impossible choices about where to invest limited budgets.

The economic case for prevention appears compelling: research consistently demonstrates that $1 invested in pre-disaster hazard mitigation avoids at least $6 in disaster response and rebuilding costs. However, the case for enhanced emergency response is equally compelling and addresses different but critical vulnerabilities. No infrastructure can be hardened against all possible scenarios, especially as climate change introduces unprecedented nonstationary conditions. When infrastructure fails, effective emergency response saves lives and accelerates recovery. The Sendai Framework explicitly recognizes both imperatives — Priority 3 calls for investing in disaster risk reduction for resilience, while Priority 4 calls for enhancing disaster preparedness for effective response.

The decision is particularly difficult because disasters affect nations inequitably. In 2023, North America suffered the largest absolute losses ($69.57 billion), but this represented only 0.23% of GDP, while Micronesia's $4.3 billion in losses represented 46.1% of subregional GDP. The insurance protection gap stood at $263 billion in 2024 — 63% of total losses left uninsured — with coverage remaining below 1% in countries like Bangladesh, India, and Nigeria. SDG 11's explicit focus on protecting "the poor and people in vulnerable situations" creates a tension between economic efficiency (invest where assets are most valuable) and social equity (protect those most vulnerable to harm).

The governance architecture has expanded significantly: the number of countries with national disaster risk reduction strategies grew from 57 in 2015 to 131 by October 2024 under the Sendai Framework. But implementation lags far behind policy adoption. As of March 2024, only 64% of Small Island Developing States and 60% of Least Developed Countries had national DRR strategies, and even among those that do, a significant portion of disaster-related funding remains focused on response rather than prevention. With the Sendai Framework approaching its 2030 expiration and over 1.2 billion additional people expected to live in cities by 2050, the choices made now will shape whether growing urban populations face compounding disaster risk or improving resilience.

---

## Milestone 2: Data Exploration & System Mapping

### Data Sources

Four datasets were used for the exploratory data analysis. Full source documentation is available in [data/README.md](data/README.md), and the data preparation process is documented in [Wrangling.md](Wrangling.md).

1. **FEMA Disaster Declarations Summaries** — All federally declared disasters in the U.S. from 1953 to 2024 (OpenFEMA)
2. **Global Economic Damage from Natural Disasters** — Economic damage by disaster type by year, 1900–present (Our World in Data / EM-DAT)
3. **FEMA Hazard Mitigation Assistance Projects** — Project-level data on federal mitigation grants (OpenFEMA)
4. **World Risk Index** — Country-level disaster risk, exposure, and vulnerability scores, 2011–2021 (World Risk Report)

### APA Citations

Federal Emergency Management Agency. (2026). *OpenFEMA dataset: Disaster declarations summaries — v2*. U.S. Department of Homeland Security. https://www.fema.gov/openfema-data-page/disaster-declarations-summaries-v2

EM-DAT, CRED / UCLouvain. (2025). *The international disasters database*. Centre for Research on the Epidemiology of Disasters. Retrieved from https://ourworldindata.org/grapher/economic-damage-from-natural-disasters

Federal Emergency Management Agency. (2026). *OpenFEMA dataset: Hazard mitigation assistance projects — v4*. U.S. Department of Homeland Security. https://www.fema.gov/openfema-data-page/hazard-mitigation-assistance-projects-v4

Bündnis Entwicklung Hilft & Ruhr University Bochum. (2021). *World Risk Index*. Retrieved from https://www.kaggle.com/datasets/tr1gg3rtrash/global-disaster-risk-index-time-series-dataset

---

### Exploratory Data Analysis

#### Figure 1: FEMA Disaster Declarations by Incident Type (1953–2024)

![Disaster Declarations Over Time](img/viz1-disaster-frequency.png)

The number of FEMA disaster declarations has increased dramatically over the past seven decades. The stacked bars reveal that severe storms, hurricanes, and floods consistently drive the bulk of declarations, while fire/wildfire declarations have grown noticeably since the 2000s. The 5-year rolling average line shows a clear upward trajectory that accelerated sharply around 2010. The massive spike around 2020 is largely attributable to COVID-19 biological declarations layered on top of an already elevated weather disaster baseline — the chart annotates this to avoid misinterpretation. Even excluding the COVID surge, the underlying weather-related trend is unmistakably upward. This directly illustrates the "growth" pressure in the Growth and Underinvestment archetype — disaster demand is increasing faster than the infrastructure built to withstand it. For the decision-maker, this means the status quo is unsustainable: whether the investment goes to prevention or response, the current level of either is insufficient for the volume of disasters now occurring.

#### Figure 2: Global Economic Damage from Weather-Related Disasters (1980–2025)

![Economic Damage Over Time](img/viz2-economic-damage.png)

Global economic losses from weather-related disasters have escalated sharply, particularly since the 1990s. The 5-year rolling average shows a clear upward trajectory, with floods and extreme weather events accounting for the largest share of damages. The annotated reference points on the chart highlight the acceleration documented in the GAR 2025: average annual costs of roughly $70 billion in the 1980s grew to approximately $180 billion by the 2000s, with the 2017 hurricane season (Harvey, Irma, Maria) driving a peak near $417 billion. Wildfire damages have also become increasingly visible in recent years. This matters for the decision because rising costs consume the budgets that could fund either infrastructure upgrades or response capacity, activating the B1 (Budget Constraint) balancing loop in the CLD. Every dollar spent on recovery is a dollar unavailable for prevention.

#### Figure 3: FEMA Disaster Declarations vs. Federal Hazard Mitigation Spending (1989–2024)

![Mitigation vs Disasters](img/viz3-mitigation-vs-disasters.png)

This dual-axis chart overlays disaster declaration counts (3-year average) against federal hazard mitigation spending (3-year average) from 1989 to 2024. The subtitle says it plainly: spending volatility does not match disaster growth. Disaster declarations have trended steadily upward, while mitigation spending has swung erratically — spiking after major events like Katrina, Sandy, and the Harvey/Irma/Maria season, then falling back. This reactive spending pattern is the core evidence for the "Underinvestment" half of the Growth and Underinvestment archetype, and it also illustrates the Shifting the Burden dynamic: mitigation funding is driven by the response cycle rather than by a sustained prevention strategy. The shaded gap between the two curves visually represents the structural mismatch between growing disaster demand and inconsistent prevention investment. For policymakers, this suggests that current mitigation investment levels are structurally insufficient to bend the disaster cost curve downward.

#### Figure 4: Disaster Exposure vs. Lack of Coping Capabilities by Country (2021)

![Vulnerability Scatter](img/viz4-vulnerability-scatter.png)

This scatter plot reveals the global inequity at the heart of the infrastructure vs. response decision. Countries in the upper-right quadrant — high exposure combined with a severe lack of coping capabilities — are disproportionately Small Island Developing States like Vanuatu, Tonga, and Antigua and Barbuda. These nations face the greatest disaster risk but have the least capacity to invest in either infrastructure or response. The labeled countries in that quadrant (including the Solomon Islands, Guyana, and Dominica) are exactly the populations SDG 11 is designed to protect. Meanwhile, countries clustered in the lower-left enjoy both lower exposure and stronger coping capabilities — typically wealthier nations that have invested in resilience over decades. This pattern directly supports the SDG 11 equity argument: the communities most in need of disaster protection are the least able to fund it. For the decision-maker, this means that investment strategies must explicitly address equity — otherwise, infrastructure investments will flow to where assets are most valuable, not where people are most vulnerable.

---

## Milestone 3: Systems Analysis (Path A)

See **[Analysis.md](Analysis.md)** for the full Milestone 3 deliverable, which includes:

- **System Archetype Identification:** Growth and Underinvestment (primary) and Shifting the Burden (secondary), mapped to the global disaster resilience system through the lens of SDG 11 and the Sendai Framework, with supporting evidence from the GAR 2025 and international disaster loss data
- **Three Scenario Narratives:** Status Quo (Sendai Framework expires without structural change), Infrastructure-First Investment (prevention priority), and Integrated Resilience (balanced portfolio with equity focus) — each tracing system evolution over 5–10 years with reference to CLD feedback loops and SDG 11 indicators
- **Leverage Point Analysis:** Risk-informed urban planning linked to financial incentives as the highest-leverage intervention, operating on the creation of new risk rather than management of existing risk
- **Implications for the Decision:** Synthesis connecting the analysis to policymakers' strategic choice, previewing the Milestone 4 recommendation

## Initial Causal Loop Diagram

![Draft CLD](img/cld-draft.png)

https://github.com/bfinucane04/ns-storm.git
