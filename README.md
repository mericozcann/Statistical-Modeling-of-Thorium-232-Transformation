# Thorium-232 Decay — Statistical Modeling  
### Educational Data Science Project

This project represents the **Th-232 → Pa-233 → U-233** decay chain using **only statistical and data-science techniques** for the purpose of **education and research**.

No real nuclear production, transformation, or experimental operations are involved.  
All data are **synthetically generated**.

## Project Goal

The aim of this work is to model the temporal behavior of a radioactive decay chain using Poisson processes, Monte Carlo simulation, and machine-learning–based anomaly detection.

The project also seeks to teach how statistical modeling, data visualization, uncertainty analysis, and ethical awareness can be integrated into nuclear-style data analysis in an educational context.

## Project Contents & File Structure

📦 Thorium-Education-Project
│
├── data/
│   ├── synthetic_counts.csv                # Main synthetic dataset
│   ├── synthetic_with_anomalies.csv        # Dataset labeled with anomalies
│   ├── monte_carlo_counts.csv              # Data generated via Monte Carlo simulation
│
├── plots/
│   ├── plot_timeseries.png                 # Time series plot
│   ├── plot_bootstrap.png                  # Bootstrap confidence interval plot
│   ├── plot_anomalies.png                  # Anomaly detection plot
│   ├── plot_timeseries.html                # Plotly interactive version
│
├── models/
│   ├── poisson_summary.txt                 # Poisson GLM model summary
│   ├── neg_binomial_summary.txt            # Negative Binomial model summary
│   ├── model_scores.json                   # AIC/BIC comparison results
│
├── reports/
│   ├── summary_report.md                   # Auto-generated project summary
│   ├── correlation_matrix.csv              # Correlation matrix output
│
├── tutorial_education.py                   # Simple educational script (example EDA)
├── thorium_education_analysis.py           # Main analysis script (intermediate)
├── thorium_education_analysis_full.py      # Full version (Monte Carlo, GLM, Bootstrap, Anomaly)
├── thorium_education_analysis.ipynb        # Jupyter Notebook version (Turkish commentary)
├── make_interactive_plots.py               # Plotly interactive plot generator
└── README.md                               # This file

## Core Methods Used

| Area | Methods & Techniques |
|------|----------------------|
| Statistical Modeling | Poisson and Negative Binomial GLMs |
| Simulation | Monte Carlo simulation (abstract A→B→C chain) |
| Machine Learning | Isolation Forest, Z-score anomaly detection |
| Bootstrap Analysis | Median confidence intervals (2,000 resamples) |
| Correlation Analysis | Pearson correlation, overdispersion checks |
| Visualization | Matplotlib, Seaborn, Plotly (interactive HTML) |

## Analysis Workflow (Summary)

1. Data generation: `synthetic_counts.csv` is generated via Poisson processes.  
2. Modeling: Compare Poisson and Negative Binomial GLMs.  
3. Monte Carlo: Simulate event counts corresponding to the abstract A→B→C chain.  
4. Bootstrap: Compute 95% confidence intervals for the median counts.  
5. Anomaly detection: Apply IsolationForest + Z-score detection.  
6. Reporting: Auto-generate a markdown summary report (`summary_report.md`).

## Visual Outputs

| File | Description |
|------|-------------|
| plot_timeseries.png | Time series and signal components |
| plot_bootstrap.png  | Bootstrap median distribution |
| plot_anomalies.png  | Visual comparison of anomaly detections |
| plot_timeseries.html | Plotly interactive version (zoom/pan enabled) |

## Run Instructions

# Required libraries
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels plotly kaleido

# Run the full automated analysis (complete version)
python thorium_education_analysis_full.py

# Generate interactive HTML plots only
python make_interactive_plots.py --png

# Open the notebook (Colab or Jupyter)
jupyter notebook thorium_education_analysis.ipynb

## Usage & Sharing Terms

This project is shared under an Educational Use & Open Access intent. The following conditions apply:

- The work may be used only for educational, research, and statistical modeling purposes.  
- It does not include any real nuclear production, experimental procedures, or operational applications.  
- All data used in the project are synthetic.  
- Code and report outputs may be shared and extended within ethical boundaries.

This permission type preserves the open-source spirit while supporting reuse only for scientific, instructional, and research purposes.

## Contributors

- Meriç Özcan: [LinkedIn](https://www.linkedin.com/in/meri%C3%A7-%C3%B6zcan/)  
- Yusuf Erim Yaşar: [Instagram](https://www.instagram.com/yusuferimysr/)

© 2025 – Educational & Research Simulation  
Statistical modeling of the Thorium-232 → Protactinium-233 → Uranium-233 chain
