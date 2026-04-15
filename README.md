# Electric Motor PM Temperature Predictor

## Project Overview

This repository contains a Flask web application that predicts the permanent magnet (PM) temperature of an electric motor using a trained machine learning model. The application accepts motor electrical and thermal input values through a web form, sends them to a prediction endpoint, and displays the predicted PM temperature.

## Project Structure

```
Final EMTP/
├── app.py
├── EMTP.ipynb
├── measures_v2.csv
├── pm_temp_random_forest_model.pkl
├── pm_temp_scaler.pkl
├── README.md
└── templates/
    └── index.html
```

## Files Description

- `app.py`
  - Flask backend application
  - Serves the web UI
  - Loads the trained model and scaler
  - Exposes `/predict` endpoint for model inference

- `templates/index.html`
  - Web page for data entry and prediction display
  - Includes client-side validation and AJAX request to `/predict`

- `EMTP.ipynb`
  - Jupyter notebook for analysis, exploration, and model development

- `measures_v2.csv`
  - Data source used for training and experimentation

- `pm_temp_random_forest_model.pkl`
  - Saved machine learning model for temperature prediction

- `pm_temp_scaler.pkl`
  - Saved scaler used to preprocess inputs before prediction

## Requirements

- Python 3.8+
- Flask
- joblib
- numpy

## Recommended Setup

1. Open PowerShell in the project folder:

```powershell
cd "d:\BCA Study\Final EMTP"
```

2. Create a new virtual environment:

```powershell
python -m venv venv
```

3. Activate the virtual environment:

```powershell
.\venv\Scripts\Activate.ps1
```

4. Install the required packages:

```powershell
pip install Flask joblib numpy
```

> Optionally, create a `requirements.txt` file to pin dependencies.

## Running the Application

1. Ensure the model files `pm_temp_random_forest_model.pkl` and `pm_temp_scaler.pkl` are present in the project root.
2. Run the Flask app:

```powershell
python app.py
```

3. Open your browser and visit:

```text
http://127.0.0.1:5000/
```

4. Enter the required values and click **Predict Temperature!**

## Input Features

The application expects the following numeric values:

- `u_q` (V)
- `u_d` (V)
- `i_q` (A)
- `i_d` (A)
- `motor_speed` (RPM)
- `torque` (Nm)
- `coolant` (°C)
- `ambient` (°C)
- `stator_winding` (°C)
- `stator_yoke` (°C)
- `stator_tooth` (°C)

## How It Works

1. The web UI sends a JSON POST request to `/predict`.
2. `app.py` validates inputs and converts them to floating-point values.
3. Inputs are scaled using the saved scaler.
4. The trained model predicts the PM temperature.
5. The prediction is returned to the browser and displayed on the page.

## Notes

- The app currently runs in development mode with `debug=True`.
- For production use, set `debug=False` or deploy with a WSGI server.
- If the model files are missing, you need to retrain the model using `EMTP.ipynb` or another training pipeline.

## Contact

This project was built by Hemen, Marmik & Jay.
