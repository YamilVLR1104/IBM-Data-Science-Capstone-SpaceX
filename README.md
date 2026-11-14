# SpaceX Falcon 9 First Stage Landing Prediction
**IBM Data Science Professional Certificate — Applied Data Science Capstone**

- **Author:** Yamil Edward Villarreal Vidaurre
- **Repository URL:** https://github.com/YamilVLR1104/IBM-Data-Science-Capstone-SpaceX

---

## Project Overview
SpaceX advertises Falcon 9 rocket launches on its website at a cost of **$62 million**, whereas other providers charge upwards of **$165 million** each. Much of the savings is possible because SpaceX reuses the first stage of the rocket. By predicting whether the first stage will land successfully, we can determine the true cost of a launch and help competing aerospace organizations bid competitively against SpaceX.

## Methodology & Repository Structure

| Step | Notebook / Script | Description |
| :--- | :--- | :--- |
| **1. Data Collection (API)** | `01_jupyter-labs-spacex-data-collection-api.ipynb` | Requests past launch records from the SpaceX REST API v4, normalizes JSON, filters Falcon 9 single-core/single-payload launches (`90` records), and identifies `26` missing values in `LandingPad`. |
| **2. Web Scraping** | `02_jupyter-labs-webscraping.ipynb` | Scrapes historical Falcon 9 and Falcon Heavy launch tables from Wikipedia using `requests` and `BeautifulSoup`. |
| **3. Data Wrangling** | `03_labs-jupyter-spacex-Data-wrangling.ipynb` | Performs exploratory distributions by site (`CCAFS SLC 40`: 55, `KSC LC 39A`: 22, `VAFB SLC 4E`: 13), orbit (`GEO`: 1, `GTO`: 27), and landing outcome (`True ASDS`: 41), encoding the binary target `Class` (66.67% success rate). |
| **4. EDA with SQL** | `04_jupyter-labs-eda-sql-coursera_sqllite.ipynb` | Executes SQL queries on `SPACEXTBL` covering unique launch sites, NASA CRS total payload mass (`45,596 kg`), `F9 v1.1` average mass (`2,928.4 kg`), first ground landing (`2015-12-22`), and mission outcome rankings. |
| **5. EDA with Visualization** | `05_jupyter-labs-eda-dataviz.ipynb` | Visualizes flight number, payload mass, orbit success rates, and yearly trends using `seaborn` and `matplotlib`, and generates an 80-column feature matrix via One-Hot Encoding. |
| **6. Interactive Maps (Folium)** | `06_lab_jupyter_launch_site_location.ipynb` | Maps launch sites, `MarkerCluster` outcome markers, and `PolyLine` proximity distances to coastlines, railways, highways, and cities. |
| **7. Interactive Dashboard** | `07_spacex_dash_app.py` | Plotly Dash web application with `dcc.Dropdown` site selector, `dcc.RangeSlider` payload filter, success pie chart, and payload-vs-outcome scatter plot. |
| **8. Predictive Analysis** | `08_SpaceX_Machine_Learning_Prediction_Part_5.ipynb` | Trains and tunes Logistic Regression, SVM (`sigmoid` kernel), Decision Tree, and KNN classifiers using `GridSearchCV` (`cv=10`), achieving **83.33%** test accuracy (`15/18` test records). |

## Key Findings
- **Historical Success Rate:** 60 out of 90 Falcon 9 launches successfully landed their first stage (**66.67%**).
- **Site Performance:** `KSC LC-39A` achieved the highest landing success rate (~77%), contributing 41.7% of all successful landings.
- **Temporal Trend:** Landing reliability improved steadily from 2013 onward, surpassing 80% in 2019–2020 with Block 5 boosters.
- **Model Performance:** All four tuned classification algorithms reached **83.33%** accuracy on the 18-sample test set, with Decision Tree and SVM (`sigmoid`) leading cross-validation accuracy (~84.8%–88.9%).
