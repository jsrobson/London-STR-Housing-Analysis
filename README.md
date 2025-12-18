# Big Data Analytics – London Calling: Exploring the influence of short-term rentals on housing affordability in pre-pandemic inner London.

![Python](https://img.shields.io/badge/python-3.11-blue?logo=python)
![Notebook](https://img.shields.io/badge/notebook-Jupyter-orange)

This was a final term group project for the University of Pennsylvania's CIS5450 ("Big Data Analytics"); using Python's data science libraries, we explored the impact of short-term rentals (i.e., Airbnb, VSCO) on the housing market in pre-pandemic (2019) London, United Kingdom. 

This project was motivated by my professional interest in housing policy and the post-recession rise of technology platforms - often referred to as the ["Millennial Lifestyle Subsidy"](https://www.nytimes.com/2021/06/08/technology/farewell-millennial-lifestyle-subsidy.html) - and how they have shaped housing affordability in cities. 

The results of this work were captured in a thoroughly-documented [Medium post](https://medium.com/@jsrobson_/london-calling-exploring-the-pre-pandemic-influence-of-short-term-rentals-on-urban-property-47bc2708eb4d). Each Jupyter Notebook instance includes its own documentation on a segment-by-segment basis.

---

## Data Attribution

This project is presented as a **case study** and is intended for conceptual review rather than direct replication.

The analysis draws on multiple open datasets to explore the relationship between short-term rentals (STRs) and housing market dynamics in inner London prior to the COVID-19 pandemic. To balance analytical resolution and scope, the study focuses on the City of London and 13 Inner London boroughs, where STR activity is most concentrated. The analysis is intentionally limited to the pre-pandemic period to avoid structural distortions introduced after early 2020.

Residential property data is sourced from a [consolidated dataset](https://reshare.ukdataservice.ac.uk/854942/) produced by researchers at **University College London (UCL)**, released under the [Open Government Licence](https://en.wikipedia.org/wiki/Open_Government_Licence). The dataset integrates official UK property transaction records with domestic energy performance certification data, enabling the calculation of price per square metre alongside attributes such as sale price, property type, floor area, and borough. For feasibility and consistency, the temporal scope was limited to 2017–2019.

Short-term rental [data](https://insideairbnb.com) is sourced from **Inside Airbnb**, a data-driven advocacy organization that publishes archival Airbnb listings under a [Creative Commons Attribution licence](https://creativecommons.org/licenses/by/4.0/). Listings data through Q2 2020 was used, including both condensed and detailed feature sets describing property characteristics, pricing, availability, and geographic distribution.

Supplementary [contextual data](https://data.london.gov.uk/dataset/indices-of-deprivation-2l15g/) is drawn from the **English Indices of Deprivation (2019)**, which provide fine-grained (LSOA-level) measures across multiple domains of socioeconomic deprivation. These indicators are used to contextualize observed housing and STR patterns rather than as predictive features.

---

## Features

- **Fine-grained geographic analysis**: Modelling is performed at the LSOA (sub-borough) level, providing a more detailed view of housing and STR dynamics than conventional borough-level studies.  
- **Exploratory Data Analysis (EDA)**: Assessment of dataset quality, distribution, and statistical properties, combined with visualization of trends using geopandas, matplotlib, and seaborn. Choropleth maps illustrate STR distribution and pricing trends across inner London.  
- **Bivariate regression modelling**: Standard linear, decision tree, and random forest regressions to explore the relationship between STR density and property cost per square metre.  
- **Multivariate regression with confounders**: Incorporation of the English Indices of Deprivation 2019 as LSOA-level confounding variables, with multiple regression flavours (Linear, Lasso, Ridge, ElasticNet) to evaluate predictive performance.  
- **Supplemental STR feature review**: Investigation of how weekly cumulative pricing of STR properties is influenced by geographic, programmatic, and quality-of-life factors.  
- **Comprehensive data workflow**: Integration and cleaning of multiple datasets, including property prices, STR listings, and deprivation indices, with reproducible Python workflows documented in Jupyter notebooks.

---

## Project Structure

The project is organized across multiple Jupyter / Google Colaboratory notebooks, each capturing a distinct step in the analysis workflow:

```bash
# Archival notebook documenting data acquisition, parsing, and preliminary investigations.
CIS5450_TermProject_01_acquire_data.ipynb
# Loads raw project datasets into Dask dataframes for analysis.
CIS5450_TermProject_02_load_data.ipynb
# Cleans, collates, and composes the project dataset, integrating property data with deprivation indices.      
CIS5450_TermProject_03_compose_data.ipynb
# Generates cartographic visualizations to explore geographic trends in housing and STR markets.    
CIS5450_TermProject_04_map_data.ipynb
# Explores bivariate relationships (STR listings vs. property cost per m²) using linear, random forest, and decision tree regression.    
CIS5450_TermProject_05_Bivariate_Model.ipynb
# Introduces confounding variables (Indices of Deprivation 2019) and applies multiple regression techniques, including neural networks.
CIS5450_TermProject_06_Expanded_Variable_Model.ipynb
# Corollary investigation of STR property features and cumulative pricing, including data cleaning, analysis, and modelling.
CIS5450_TermProject_STR_Feature_Review.ipynb
```

---

## Dependencies

The project relies on the following Python libraries:

### Data Handling
- `pandas >= 2.0`
- `numpy >= 1.25`
- `dask[dataframe] >= 2025.0`
- `sqlite3` (built-in with Python)

### HTTP / APIs
- `requests >= 2.32`

### Geospatial
- `geopandas >= 1.3`
- `shapely >= 2.1`
- `contextily >= 1.2`

### Visualization
- `matplotlib >= 3.8`
- `seaborn >= 0.12`
- `IPython >= 8.20`
- `pydotplus >= 2.0`

### Machine Learning
- `scikit-learn >= 1.3`
- `statsmodels >= 1.2`

### Optional / Database
- `db-sqlite3` (only if using as a separate package)

---

## Learning

Through this project, several key lessons emerged related to data science practice, urban data analysis, and collaborative workflow management:

- **Structuring and organizing distributed workflows** - Balancing sequential data analysis pipelines with team-based task assignments highlighted the importance of clear milestones and communication when multiple contributors work on different notebooks or project stages.

- **Handling large and complex datasets** - Working with property price and STR datasets exceeding 50,000 rows reinforced the need to scale data thoughtfully, condense features for feasibility, and iteratively refine dataset scope for meaningful analysis.

- **Granularity matters** - Shifting from borough-level to LSOA-level data enabled richer modeling outcomes and more realistic statistical analysis, illustrating how geographic or hierarchical scale can dramatically affect results.

- **Incorporating confounding variables and supplemental data** - Integrating indices of deprivation and other supplemental datasets illustrated the importance of domain knowledge and contextual data in improving model interpretability and analysis depth.

- **Exploratory data analysis and model building** - Iterative exploration of bivariate relationships and regression approaches demonstrated how simplification may lead to overfitting, while introducing additional complexity can yield actionable insights.

- **Balancing ambition with feasibility** - The project reinforced the necessity of iterating on scope, balancing exploration with practical constraints, and prioritizing learning outcomes over exhaustive coverage.

- **Project management in ephemeral environments** - Using Google Colab as the primary environment exposed limitations in version control and collaborative coding, highlighting the need for clear coordination and checkpointing when using cloud notebooks.

