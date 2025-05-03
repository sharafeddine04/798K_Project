# COVID-19 Modeling Project

This project explores the spread of COVID-19 using three different modeling approaches:

1. Long Short-Term Memory (LSTM) neural networks  
2. A mechanistic SIRDH differential equations model  
3. Sparse Identification of Nonlinear Dynamics (SINDy)

We focus on how hospitalization impacts outbreak dynamics. Models are trained and evaluated on time-series data from the [Google COVID-19 Open Data Repository](https://health.google.com/covid-19/open-data/raw-data).

---

## 🔍 Notebooks Overview

### 1. `Project_LSTM.ipynb`

- Trains an LSTM model on COVID-19 data to forecast:
  - New confirmed cases  
  - Recoveries (estimated)
  - Deaths  
  - Hospitalizations  
  - ICU patients  

- Uses a rolling window approach with:
  - 30-day input  
  - 7-day prediction window  

- Outputs include forecast plots and mean squared error scores.

### 2. `Project_SINDY_SIRDH.ipynb`

- Downloads COVID-19 time-series data  
- Processes the data into compartmental form: Susceptible, Infected, Hospitalized, Recovered, Deceased  
- Fits the extended SIRDH model to a selected time window using nonlinear least squares  
- Attempts to recover governing equations using SINDy (not fully successful due to noise and instability)  
- Includes visualization of model predictions vs. actual data  

---

## 🌐 Changing the Country

The notebooks use U.S. data by default from this URL: https://storage.googleapis.com/covid19-open-data/v3/location/US.csv


To analyze data for another country:
- Replace `US` in the URL with the corresponding country code:
  - `GB` for Great Britain  
  - `FR` for France  
  - etc.

This can be modified in the `read_csv` line inside the data loading cell in all the notebooks.

---


## 🛠 Requirements

You can install all dependencies using the provided `requirements.txt`.

### `requirements.txt`

```
pandas
numpy
matplotlib
scikit-learn
tensorflow
pysindy
scipy
```

To install:

```bash
pip install -r requirements.txt
```

---

## 📁 File Structure

```
├── Project_LSTM.ipynb
├── Project_SINDY_SIRDH.ipynb
├── requirements.txt
└── README.md
```

---

## 📌 Notes

- Recovery values are estimated using a 14-day delay due to missing direct reports.
- SINDy performance is highly sensitive to noise; future improvements could involve filtering or constrained libraries.
