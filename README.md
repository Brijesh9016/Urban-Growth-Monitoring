# Urban Growth Observatory — Monitoring Urban Growth Using Remote Sensing

A Streamlit web application for before/after satellite maps, urban expansion maps, Dynamic World land-cover comparison, NDVI/NDBI/NDWI, interactive Folium maps, charts and CSV exports.

## Windows setup (VS Code / PowerShell)

1. Install Python 3.11 or 3.12 from python.org and enable **Add Python to PATH**.
2. Extract the ZIP and open the `Urban_Growth_Monitoring` folder in VS Code.
3. Open Terminal > New Terminal, then run:

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

If PowerShell blocks activation, run `Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass` then retry activation. Alternatively use `.\.venv\Scripts\python.exe` in place of `python` and skip activation.

4. Register a Google Cloud project for Earth Engine access at https://earthengine.google.com/ and authenticate:

```powershell
earthengine authenticate
```

5. Run:

```powershell
python -m streamlit run app.py
```

6. Open http://localhost:8501, enter the **Google Cloud project ID** (not email), select Ahmedabad, years 2020 and 2025, and click **Run urban growth analysis**.

## Features

- Two side-by-side true-color Sentinel-2 satellite maps (before/after)
- Urban change overlay: new (red), stable (purple), former (blue)
- Two Dynamic World land-cover maps and a legend
- NDVI, NDBI and NDWI interactive map layers
- Built-up area metrics, change charts, and CSV exports
- Nine preset Indian city centers with adjustable circular study area

## Troubleshooting

- `Python was not found`: install Python and restart VS Code, or try `py --version`.
- `Earth Engine not initialized`: run `earthengine authenticate` and provide a registered Google Cloud project ID.
- `Permission denied`: ensure Earth Engine is enabled for the Cloud project and your Google account has access.
- `No Sentinel-2 imagery`: increase cloudiness threshold or change year.
- **Geemap errors:** This version deliberately does **not** use `geemap`; install only this ZIP's requirements into a clean `.venv`.

## Methodology and cautions

Data sources: `GOOGLE/DYNAMICWORLD/V1` and `COPERNICUS/S2_SR_HARMONIZED` via Google Earth Engine. Dynamic World annual modal labels are estimates. A circular buffer is not a municipal boundary. Changes in classification can reflect uncertainty, cloud gaps or seasonality. This is an educational remote-sensing dashboard, not a validated urban inventory. Accuracy validation and administrative boundaries should be added for a research-grade study.

The dashboard requires an internet connection and working Earth Engine authorization. It does not include pre-downloaded satellite images. Maps load live after analysis.
