﻿# Bitcoin Price Prediction Using Facebook Prophet

This repository contains a Jupyter Notebook for forecasting Bitcoin prices using Facebook Prophet. The notebook guides you through the process of loading data, visualizing trends, preparing the data, training a forecasting model, and exporting predictions.

---

## Features

- **Data Import & Exploration:** Load historical Bitcoin price data and perform basic exploration.
- **Visualization:** Plot price trends and distributions using Plotly.
- **Data Preparation:** Format your data for Prophet (`Date` → `ds`, `Close` → `y`).
- **Modeling:** Train a Facebook Prophet model on the historical data.
- **Forecasting:** Predict future Bitcoin prices (default: 30 days ahead).
- **Results Visualization:** Plot the forecast and its trend/seasonality components.
- **Export:** Download the forecasted data as a CSV file.

---

## Requirements

- Python 3.6+
- Jupyter Notebook or Google Colab
- Libraries:
  - prophet
  - pandas
  - plotly

Install dependencies with:

```bash
pip install prophet pandas plotly
```

---

## Usage

1. **Open the Notebook:**  
   Use Jupyter Notebook or upload to Google Colab.

2. **Switch to GPU (Optional for Colab):**  
   `Runtime > Change runtime type > GPU`

3. **Install Prophet (if needed):**  
   ```bash
   pip install prophet
   ```

4. **Upload Data:**  
   Upload your historical Bitcoin data CSV (must include `Date` and `Close` columns).

5. **Run the Cells:**  
   - Import libraries  
   - Read and explore the data  
   - Visualize prices (area and violin plots)  
   - Prepare data for Prophet  
   - Fit the Prophet model  
   - Make future predictions (default: 30 days)  
   - Plot the forecast and its components  
   - Download the forecast as `Forecast.csv`

---

## File Structure

| File                           | Description                                |
|--------------------------------|--------------------------------------------|
| `Bitcoin_Price_prediction.ipynb` | Main Jupyter Notebook                     |
| `bitcoin_data.csv`             | Input data file (user-provided)            |
| `Forecast.csv`                 | Output: forecasted Bitcoin prices          |

---

## Methodology Overview

- **Data Preparation:**  
  Rename columns for Prophet compatibility and check for missing values.

- **Modeling:**  
  Prophet is trained on the historical closing price data.

- **Forecasting:**  
  The model predicts the next 30 days (customizable).

- **Visualization:**  
  - Price over time (area graph)  
  - Price distribution (violin plot)  
  - Forecast plot with uncertainty intervals  
  - Trend and seasonality components

- **Export:**  
  Forecasted results are saved and available for download.

---

## Example Workflow

```python
import pandas as pd
from prophet import Prophet
import plotly.express as px

# Load data
df = pd.read_csv("bitcoin_data.csv")

# Prepare data for Prophet
prophet_df = df.rename(columns={'Date': 'ds', 'Close': 'y'})

# Fit model
m = Prophet()
m.fit(prophet_df)

# Make future predictions
future = m.make_future_dataframe(periods=30)
forecast = m.predict(future)

# Export results
forecast.to_csv("Forecast.csv")
```

---

## Notes

- Input CSV must have columns `Date` and `Close`.
- The notebook is designed for educational and exploratory use.
- Modify the forecast horizon by changing the `periods` parameter.

---

*Powered by Facebook Prophet and Plotly for fast, interpretable time series forecasting.*
