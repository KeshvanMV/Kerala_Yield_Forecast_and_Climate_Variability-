# Kerala’s Agricultural Future: Climate Variability, Yield Trends, and Forecasting

## Overview
This project provides a data-driven analysis of the vulnerability of Kerala’s agricultural sector to climate change, focusing on the historical relationship between crop yields and key climatic variables. The state of Kerala, heavily reliant on monsoon-driven agriculture, serves as a critical case study for assessing climate resilience in tropical agro-ecosystems.

The primary objective is to quantify how shifts in climate factors (monsoon behavior, temperature, humidity, and root-zone soil moisture) have influenced major crop productivity over time. The findings establish a crucial evidence base to support strategic policy recommendations for climate action and adaptive measures, directly informing the accompanying report *Agricultural Resilience and Climate Action in Kerala: A Policy Report*.

## Data Sources

| Source | Variables | Coverage |
|--------|-----------|----------|
| **IMD** | Rainfall | 1990–2025 |
| **NASA POWER** | Temperature, Humidity, Soil Moisture | 1984–2025 |
| **UPAg** | Historical Yield (13 crops) | 1961–2023 |

### Preprocessing and Cleaning
- **Missing Data Handling**: Interpolation applied to fill gaps, especially in early records.  
- **Normalization and Scaling**: Applied to ensure comparability across variables.  
- **Anomaly Computation**: Climate anomalies calculated as deviations from long-term averages to capture stress events such as dry spells, excessive rainfall, and heat waves.  

## Methodology
The analytical workflow moves from exploratory analysis to forecasting and sensitivity diagnostics.

- **Exploratory Data Analysis (EDA)**: Identification of decadal yield trends and seasonal climate patterns.  
- **Feature Preparation**: Computation of climate anomalies as stress indicators.  
- **Correlation Analysis**: Quantification of immediate and lagged relationships between yields and climate anomalies.  
- **Crop Sensitivity to Climate Profiling**: Measurement of how different crops respond to rainfall, temperature, humidity, and soil moisture variability.  
- **Threshold Detection**: Identification of climate thresholds (e.g., rainfall deficits, heat extremes) beyond which yield losses accelerate.  
- **Tech vs Climate**: Comparative analysis of yield improvements from technological adoption versus climate-driven pressures.  
- **Can Technology Keep Pace with Warming?**: Scenario framing to test whether technological gains are sufficient to offset projected climate stress.  
- **Time Series Forecasting**: ARIMA models used to estimate missing values and establish baseline forecasts.  
- **Yield Sensitivity Analysis**: Structural break-year thresholds tested to assess potential volatility and regime shifts.  

### Model Details
- **Time-Series Forecasting**
  - ARIMA (Autoregressive Integrated Moving Average) for baseline yield forecasts and missing value estimation.
- **Regression and Machine Learning**
  - Linear Regression, Decision Tree Regressor, Random Forest Regressor for comparative modeling and scenario checks.
- **Anomaly Detection**
  - Isolation Forest for identifying outlier years in yield–climate relationships.
- **Statistical Analysis**
  - Pearson correlation for climate–yield sensitivity.
  - Statsmodels OLS and formula API for regression diagnostics.
- **Preprocessing**
  - MinMaxScaler, StandardScaler, PolynomialFeatures for feature scaling and engineering.
- **Evaluation Metrics**
  - Mean Absolute Error (MAE), Mean Squared Error (MSE), R² score.

## Results and Insights
- **Quantified Volatility**: Strong correlations between yield failures and anomalies such as prolonged dry spells, excessive rainfall, and heat stress.  
- **Baseline Trajectory**: ARIMA forecasts suggest marginal improvements without intervention, reflecting historical stagnation.  
- **System Fragility**: Combined methods highlight the fragility of Kerala’s agricultural system and the amplifying role of climate change.  

## Figures and Artifacts
- **Decadal Trend Plots**: Long-term yield stagnation and volatility across major crops.  
- **Anomaly Time Series**: Deviations in rainfall, temperature, and soil moisture relative to historical baselines.  
- **Correlation Heatmaps**: Immediate and lagged climate–yield relationships, highlighting crop-specific sensitivities.  
- **ARIMA Forecast vs. Sensitivity Plots**: Baseline forecasts compared with structural break and volatility scenarios.  
- **Crop Sensitivity Profiles**: Visualizations of how different crops respond to rainfall, temperature, and humidity anomalies.  
- **Threshold Detection Charts**: Identification of climate thresholds (e.g., rainfall deficits, heat extremes) beyond which yield losses accelerate.  
- **Technology vs. Climate Stress Plots**: Comparative trajectories showing yield gains from technology adoption versus climate-driven pressures.  
- **Technology Gap Scenarios**: “Can Technology Keep Pace with Warming?” plots illustrating whether innovation offsets projected climate stress.  
- **Anomaly Distribution Histograms**: Frequency and intensity of rainfall and temperature anomalies over time.  
- **Residual and Diagnostic Plots**: Model fit checks, error distributions, and convergence diagnostics from ARIMA and regression models.  


## Repository Structure
```
├── README.md 
├── Kerala’s Agricultural Future: Climate Variability, Yield Trends, and Forecasting.ipynb 
├── Data/ 
│ ├── raw/ 
│ └── processed/
└── reports/ 
```

## How to Run

1. **Prepare the Data Folder**  
   - Create a directory named `Data/` in the project root.  
   - All CSV files used in the analysis should be placed inside this folder.

2. **Running on Google Colab**  
   - Use the provided upload code block to select and upload CSV files from your local machine:  
     ```python
     from google.colab import files
     uploaded = files.upload()
     import shutil
     for fname in uploaded.keys():
         shutil.move(fname, f"./Data/{fname}")
     ```  
   - This will move the uploaded files into the `Data/` folder for use in the notebook.

3. **Running Locally (VS Code, Jupyter Notebook, or other platforms)**  
   - Place the required CSV files manually into the `Data/` folder.  
   - Load them directly in the notebook using pandas, for example:  
     ```python
     import pandas as pd
     df = pd.read_csv("./Data/your_file.csv")
     ```  
   - No upload step is required since the files are already available on your machine.

4. **Optional: Auto-create the Data Folder**  
   - To ensure the `Data/` folder exists before saving files, you can add:  
     ```python
     import os
     os.makedirs("Data", exist_ok=True)
     ```

After the data is in place, open and execute all cells in the notebook sequentially to reproduce the analysis and results.

## Limitations
 - Data Gaps: Incomplete records, especially before the 1980s.
 - Model Assumptions: ARIMA assumes future patterns follow historical inertia.
 - Exclusion of Drivers: Socio-political and technological factors not modeled.

## License
- License details are not present in the notebook. Recommended: MIT License.

## Acknowledgments
- **Policy Context**: This analysis is structured to inform and align with the *Kerala State Action Plan on Climate Change 2.0 (2023–2030)*, ensuring that the findings directly support state-level adaptation strategies and policy framing.
- **Statistical reference**: Agricultural Statistics 2023 (Compendium of Agricultural Statistics: Kerala 2023) was used as an authoritative baseline to validate yield figures and contextualize trends.
- **Libraries**: The project relies on widely used Python libraries for data analysis, visualization, and modeling (e.g., pandas, NumPy, matplotlib, seaborn, scikit-learn, statsmodels, scipy). Standard utilities such as `warnings` were also used to manage runtime alerts and suppress non-critical convergence warnings during statistical modeling.
