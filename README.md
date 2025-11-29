# Air Quality Analysis — Kraków (os. Piastów) (2016–2025)

This project is a coursework data analysis (Data Science / introductory Machine Learning) focused on daily Air Quality Index
(AQI) for Kraków — osiedle Piastów. The analysis uses daily AQI coefficients for PM2.5, PM10, O3, NO2, SO2 and CO and covers
January 2016 through November 2025.

**Main goals**

- Provide a clean, reproducible exploratory analysis of local air quality data.
- Compute a composite daily AQI (EPA-style) and investigate temporal trends, seasonality, and pollutant co-occurrence.
- Produce visualizations and simple summary statistics useful for interpretation and communication.

**Repository contents**

- `Analiza_Zaliczeniowa_Dawid_Sekunda.ipynb`: Jupyter notebook with the full analysis, code and visualizations.
- `data.csv`: (expected) CSV file with daily AQI coefficients used by the notebook. The notebook reads this file directly.

If `data.csv` is missing, place your dataset in the repository root (or adjust the path in the notebook).

**Data overview**

- Location: Kraków, os. Piastów, Małopolska, Poland
- Time range: 2016-01 to 2025-11 (daily observations)
- Pollutants (AQI coefficients): `pm25`, `pm10`, `o3`, `no2`, `so2`, `co`

**Key analysis steps (implemented in the notebook)**

- Load and inspect data (`pandas`) and convert `date` column to datetime.
- Handle missing values with linear interpolation and backfill; clip negatives to zero.
- Compute descriptive statistics and add `year` and `month` columns for aggregation.
- Plot time series for PM2.5 and the composite AQI.
- Compute correlation matrix for pollutant AQI coefficients and visualize with a heatmap.
- Build `aqi_total` as the daily maximum across pollutant AQIs (EPA approach) and evaluate how many days exceed health thresholds (e.g., AQI > 100).
- Compute monthly averages to inspect seasonality and plot smoothed trend using a 30-day rolling mean.
- Classify days into EPA categories (Good, Moderate, Unhealthy for Sensitive Groups, etc.) and show distribution.

**Main findings (from notebook conclusions)**

- Air quality is clearly seasonal: winter months (Jan, Feb, Dec) show the worst AQI values.
- PM2.5 is typically the dominant pollutant and drives many high-AQI days — likely related to residential heating and inversion episodes.
- There are a non-negligible number of days with `aqi_total > 100`, representing health risk for sensitive groups.

**Dependencies**
The notebook uses the following Python libraries:

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`

You can create a minimal `requirements.txt` containing:

```
pandas
numpy
matplotlib
seaborn
```

**How to run**

1. Install dependencies (recommended to use a virtual environment):

```powershell
python -m pip install -r requirements.txt
```

2. Open the notebook in Jupyter or VS Code and run cells, or start Jupyter:

```powershell
jupyter notebook Analiza_Zaliczeniowa_Dawid_Sekunda.ipynb
```

3. Ensure `data.csv` is present at the path used in the notebook (root by default).

**Suggested next steps / improvements**

- Add a `requirements.txt` to the repo and pin versions for reproducibility.
- Add a short `data/README.md` describing `data.csv` columns and data provenance.
- Add automated checks (simple unit tests or a notebook cell) that `data.csv` contains the expected columns and date range.
- Consider exporting key charts as PNGs and storing them under `figures/` for easy reuse in reports.
- Optionally extend the notebook with simple predictive models (seasonal decomposition or ARIMA) and robust missing-data strategies.

**Author / Contact**
Project notebook by Dawid Sekunda (student coursework). For changes or questions, open an issue or contact the repository owner.

---

This README was generated from the project notebook contents. If you want edits (shorter summary, add dataset schema, or change tone), tell me what to adjust.
