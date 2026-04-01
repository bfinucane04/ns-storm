# Wrangling.md

## Dataset 1: FEMA Disaster Declarations Summaries

**File:** `DisasterDeclarationsSummaries.csv` (~69,770 rows)

### What I Found
- The raw data has one row per county affected by each disaster, so a single hurricane shows up as dozens of rows. I needed counts of actual disaster events per year, not county-level records.
- The dataset has 28 columns, most of which I didn't need (FIPS codes, internal IDs, hash values, etc.).
- Dates were already available as a fiscal year integer (`fyDeclared`), so no date parsing was needed.

### What I Did
- Built a pivot table counting unique `disasterNumber` values per year (`fyDeclared`), broken down by `incidentType` (Severe Storm, Hurricane, Flood, Fire, etc.).
- Added a 5-year moving average column to smooth out the year-to-year noise and show the long-term trend more clearly.
- Kept the full 1953–2024 range.

### Decisions
- Counted each disaster once per year regardless of how many counties it affected. This gives the number of distinct disaster events, which better represents how often disasters are happening.
- Kept all incident types in the breakdown so I could compare categories.

---

## Dataset 2: Global Economic Damage (EM-DAT / Our World in Data)

**File:** `economic-damage-from-natural-disasters.csv` (~1,161 rows)

### What I Found
- The `entity` column mixes individual disaster types (like "Flood") with summary rows (like "All disasters") that would double-count damages if included.
- Some disaster types (Earthquake, Volcanic activity, Fog) aren't relevant to my storm infrastructure vs. emergency response question.
- Damage values were in raw dollars (e.g., 32,000,000,000), which is hard to read.
- Data before 1960 is sparse and unreliable.

### What I Did
- Removed all summary rows and irrelevant types. Kept only: **Flood, Extreme weather, Drought, Wildfire, and Extreme temperature**.
- Divided all damage values by 1 billion for readability.
- Filtered to 1960 onward.

### Decisions
- Damages are in nominal US dollars (not inflation-adjusted), which means some of the upward trend reflects inflation and more assets at risk, not just worse disasters. I note this limitation in my analysis.
- The five types I kept cover the main weather-related hazards relevant to infrastructure and response policy.

---

## Dataset 3: FEMA Hazard Mitigation Assistance Projects

**File:** `HazardMitigationAssistanceProjects.csv` (~63,118 rows)

### What I Found
- Each row is a single mitigation project. I needed yearly totals to compare against disaster trends.
- The `federalShareObligated` column (how much federal money went to each project) had missing values for projects that were still pending.

### What I Did
- Built a pivot table by `programFy` (fiscal year) that counts the number of projects per year and sums the `federalShareObligated` per year.
- Missing funding values were naturally excluded from the sum.

### Decisions
- Used `programFy` as the year, which is when the project was initiated — not necessarily when the money was spent.
- Included all project statuses (pending, obligated, closed) in the project count to show the full picture of mitigation activity.
- Used federal share obligated (not total project cost) as the investment measure since it represents direct federal spending on prevention.

---

## Dataset 4: World Risk Index

**File:** `world_risk_index.csv` (~1,917 rows)

### What I Found
- The dataset has yearly scores for each country from 2011 to 2021. I only needed one year for the scatter plot.
- One column name had a leading space, but it didn't cause issues in Excel.
- The numeric and categorical columns were already clean.

### What I Did
- Filtered to 2021 only (most recent year available).
- No other cleaning was needed — the data was already in good shape.

### Decisions
- Used 2021 as it gives the most current snapshot of global risk.
- Labeled the top 10 highest-risk countries in the scatter plot. Most of these turned out to be Small Island Developing States, which connects directly to the SDG 11 equity argument in my project.
