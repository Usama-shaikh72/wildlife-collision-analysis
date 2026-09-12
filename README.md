# Global Roadkill — A Data Story

A data analytics project exploring global wildlife-vehicle collision records to uncover patterns in **scale, species, season, geography, and conservation risk**. Built as a Colab notebook using Python, Pandas, and Plotly, with an interactive Kepler.gl hotspot map.

> **Note on scope:** This dataset captures *recorded* roadkill incidents, not the total number of roadkill events worldwide. Geographic and survey coverage is uneven across regions, so all insights below should be read as patterns within the recorded dataset — not universal claims about wildlife mortality on roads globally.

---

##  Project Overview

This project was built as part of our **CIA (Continuous Internal Assessment) project**, applying the full data analytics workflow — data cleaning, exploratory analysis, visualization, and storytelling — to a real-world dataset on global roadkill incidents.

The goal was to move beyond simple charts and build a **documentary-style data narrative**: a coherent story arc that takes a viewer from the broad scale of the problem down to its most urgent conservation implications.

**Project arc:** Scale → Species → Season → Geography → Conservation Risk

---

##  Objectives (Assignment Requirements)

- Clean and prepare a real-world, messy dataset for analysis
- Derive meaningful, non-trivial insights using Python (Pandas/NumPy)
- Visualize findings using professional, publication-quality charts (Plotly)
- Include at least one **geospatial/interactive visualization** (Kepler.gl)
- Present a cohesive **data story**, not a list of disconnected charts
- Translate technical insights into a narrative suitable for a general audience (video/documentary presentation)

---

##  Dataset

- **Source file:** `Global Roadkill data.csv`
- **Key fields used:** `occurrenceID`, `country`, `continent`, `locality`, `decimalLatitude`, `decimalLongitude`, `class`, `order`, `family`, `scientificName`, `vernacularName`, `iucnStatus`, `numberOfRoadkill`, `year`, `month`, `day`, `roadType`, `roadLength`, `surveyType`

**Cleaning steps performed:**
- Dropped records missing species name or coordinates
- Coerced `numberOfRoadkill` to numeric, handled negatives/nulls (defaulted to 1)
- Filled missing common names with scientific names
- Standardized missing IUCN status to `NE` (Not Evaluated)
- Filled missing road type as `Unknown`
- Removed duplicate records by `occurrenceID`
- Exported cleaned dataset to `global_roadkill_clean.csv` for reuse

---

##  Tech Stack

| Tool | Purpose |
|---|---|
| Python (Pandas, NumPy) | Data cleaning and aggregation |
| Plotly (`plotly.express`, `plotly.graph_objects`) | Static/interactive charts |
| Kepler.gl | Geospatial hotspot mapping |
| Google Colab | Notebook environment |

---

##  Insights & Key Findings

### 1. What kinds of animals are being hit?
Mammals dominate recorded roadkill at **57.9%**, followed by amphibians (26.3%), reptiles (8.8%), and birds (7%) — establishing the overall scale of the problem.

### 2. Who are the most common victims?
The **European Roe Deer** leads all species with **44,565** recorded incidents — nearly 3× the next-highest, the Pool Frog (15,785). Other top species include the Coypu, Common Fallow Deer, and Reeves' Muntjac.

### 3. When does roadkill peak?
Roadkill peaks in **August**, with 24,907 recorded incidents — about **1.51×** the monthly average — though this reflects patterns in the recorded data rather than a universal seasonal claim, given uneven survey coverage across hemispheres.

### 4. Does the pattern hold across continents?
No — the leading species changes by region (deer dominate in Europe; amphibians and rodents like the Coypu are more prominent in South America), showing this is a structural issue tied to local roads and habitats, not one global "victim species."

### 5. Where is recorded roadkill geographically concentrated?
An interactive **Kepler.gl hexbin map** visualizes where recorded incidents cluster most densely worldwide, weighted by `numberOfRoadkill`.

### 6. Where do threatened species make up the largest share?
As a percentage of each continent's own roadkill total, **Asia** has the highest share of threatened-species roadkill (6.47%), followed by South America (4.91%) and Europe (1.94%) — even though Europe has the highest raw count overall.

### 7. How much of all recorded roadkill involves threatened species?
Of **208,570** total recorded incidents, **5,242** (**~2.5%**) involve species classified as Vulnerable, Endangered, or Critically Endangered.

### 8. Which threatened species are hit hardest?
The **Common Fire Salamander** (Vulnerable) leads with 1,565 incidents, followed by the **Giant Anteater** (Vulnerable, 1,237) and the **European Rabbit** (Endangered, 443). Others include the Lowland Tapir, Manabi Hognose Pitviper, Lataste's Viper, and Long-tailed Macaque.

### 9. Where are threatened species most at risk from roads?
A second **Kepler.gl hexbin map**, filtered to only Vulnerable/Endangered/Critically Endangered species, highlights the specific locations where roads most threaten already-vulnerable populations.

---

##  How to Run

1. Open the notebook in **Google Colab**.
2. Run the **Setup & Data Preparation** cell first — it will prompt you to upload `Global Roadkill data.csv` if it isn't already present.
3. Run each **Insight** section in order (Insights 1–9).
4. For Insights 5 and 9, install `keplergl` (already included as a cell: `!pip install -q keplergl==0.4.0rc4`), then set the layer type to **Hexbin** and the weighting field to **`numberOfRoadkill`**.

---

##  Deliverables

- `roadkill_final_colab.ipynb` — full analysis notebook
- Data storytelling video script (documentary style, narrated across the 9 insights)
- This README, summarizing methodology and findings

---

##  Limitations

- The dataset reflects **recorded** roadkill only — not total wildlife mortality on roads globally.
- Survey effort and reporting infrastructure vary significantly by country and continent, which can bias raw counts toward better-surveyed regions.
- Seasonal patterns (e.g., the August peak) may partly reflect survey timing rather than a universal biological pattern.

---

##  Team

| Member | Contribution |
|---|---|
| *Ian Almeada* | Insights 1–3 — Scale (animal class), Species (top species), Season (monthly pattern) |
| *Kripa Joshi* | Insights 4–6 — Geography (continent tour), Hotspot Map, Threatened Share by Continent |
| *Usama Shaikh* | Insights 7–9 — Threatened Species Total, Top Threatened Species, Threatened Hotspot Map |



---
