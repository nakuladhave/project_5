# 🌊 Sea Level Predictor

A Python-based time-series analysis and forecasting project that models **130+ years of global sea level data (1880–2013)** to predict sea level rise through **2050** using linear regression.

---

## 📌 Project Overview

This project uses NOAA sea level measurements to build dual linear regression models — one trained on the full historical dataset (1880–2013) and one on recent data (2000 onwards) — to generate two forecast scenarios through 2050.

It demonstrates a complete end-to-end ML workflow: **data ingestion → EDA → modeling → evaluation → visualization**, and is directly applicable to **AI forecasting pipelines** and **climate data analytics**.

---

## 📊 Dataset

- **Source:** [EPA / freeCodeCamp Sea Level Dataset](https://raw.githubusercontent.com/freeCodeCamp/boilerplate-sea-level-predictor/main/epa-sea-level.csv)
- **Coverage:** 1880 – 2013 (130+ years of NOAA measurements)

| Column | Description |
|--------|-------------|
| `Year` | Year of measurement |
| `CSIRO Adjusted Sea Level` | Global mean sea level in inches (CSIRO adjusted) |

---

## 🔧 Tech Stack

| Library | Purpose |
|---------|---------|
| Python 3 | Core language |
| Pandas | Data loading and manipulation |
| Matplotlib | Scatter plot and regression line visualization |
| SciPy (`linregress`) | Linear regression modeling |

---

## 📁 Project Structure

```
sea-level-predictor/
│
├── sea_level_predictor.py   # Main script with regression and plot logic
├── sea_level_plot.png       # Output chart (scatter + dual regression lines)
└── README.md
```

---

## 🚀 How to Run

### Option A — Google Colab (Recommended)
Dataset loads directly from GitHub — no file upload needed.

### Option B — Local
```bash
# 1. Clone the repo
git clone https://github.com/nakuladhave/sea-level-predictor.git
cd sea-level-predictor

# 2. Install dependencies
pip install pandas matplotlib scipy

# 3. Run
python sea_level_predictor.py
```

---

## 🤖 Modeling Approach

### Scenario 1 — Full Historical Fit (1880–2050)
```python
slope, intercept, _, _, _ = linregress(df['Year'], df['CSIRO Adjusted Sea Level'])
years_all = pd.Series(range(int(df['Year'].min()), 2051))
plt.plot(years_all, intercept + slope * years_all, 'r', label='Fit: All Years')
```
Trained on all available data. Captures the long-term baseline trend.

### Scenario 2 — Recent Acceleration Fit (2000–2050)
```python
df_recent = df[df['Year'] >= 2000]
slope2, intercept2, _, _, _ = linregress(df_recent['Year'], df_recent['CSIRO Adjusted Sea Level'])
years_recent = pd.Series(range(2000, 2051))
plt.plot(years_recent, intercept2 + slope2 * years_recent, 'green', label='Fit: 2000 Onwards')
```
Trained only on post-2000 data to capture the **accelerating rate** of sea level rise observed in recent decades.

---

## 📈 Output Chart

The final visualization includes:
- 🔵 **Scatter plot** — raw NOAA sea level measurements (1880–2013)
- 🔴 **Red line** — regression fit on full dataset, projected to 2050
- 🟢 **Green line** — regression fit on 2000+ data, projected to 2050 (steeper slope = higher projected rise)

The divergence between the two lines illustrates the **acceleration in sea level rise** in recent decades.

---

## 🔍 Key Findings

- Sea level has risen consistently since 1880, with a measurable long-term upward trend
- The post-2000 regression line has a **steeper slope** than the full-dataset line, indicating accelerating rise
- Dual-scenario projection gives a low-estimate and high-estimate forecast for 2050
- Results are consistent with published NOAA and IPCC sea level rise projections

---

## 🎯 Skills Demonstrated

- Time-series data analysis on real-world climate datasets
- `scipy.stats.linregress` for statistical regression modeling
- Dual-scenario forecasting — full-history vs recent-trend models
- Multi-series Matplotlib visualization (scatter + multiple regression lines)
- Reproducible Jupyter/Colab-ready analytical workflow

---

## 📜 Certification Context

Completed as part of the **freeCodeCamp Data Analysis with Python** certification — one of 5 required industry-standard projects.

🔗 [freeCodeCamp Certification](https://www.freecodecamp.org/certification/nakuladhave/data-analysis-with-python-v7)

---

## 👤 Author

**Nakul Adhave**
📧 nakuladhave@gmail.com
🔗 [LinkedIn](https://linkedin.com/in/nakul-adhave-a82294330)
💻 [GitHub](https://github.com/nakuladhave)

---

## 📄 License

This project is open source under the [MIT License](LICENSE).
