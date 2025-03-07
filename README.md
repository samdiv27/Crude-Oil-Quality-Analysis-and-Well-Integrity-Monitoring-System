Crude Oil Quality Analysis and Well Integrity Monitoring System

Project Description:
This project is a Python-based tool designed to analyze crude oil quality parameters (e.g., API gravity, viscosity, sulfur content) and simulate well integrity monitoring using sensor data. The tool processes real-time or historical data, generates reports, and visualizes trends to help oilfield technicians and engineers make informed decisions.

Key Features:
Crude Oil Quality Analysis:

Calculate API gravity, viscosity, and sulfur content from input data.

Classify crude oil into categories (e.g., light, medium, heavy) based on API gravity.

Well Integrity Monitoring:

Simulate gas migration and pressure data from wells.

Detect anomalies in well integrity using threshold-based rules.

Data Visualization:

Generate graphs and charts for trends in crude oil quality and well integrity parameters.

Report Generation:

Export analysis results into a PDF or CSV report for easy sharing.

Technologies Used:
Programming Language: Python

Libraries: Pandas, NumPy, Matplotlib, Seaborn, ReportLab (for PDF generation)

Data Source: Simulated sensor data or CSV files

GitHub Repository Structure:
Copy
Crude-Oil-Analysis/
├── README.md                   # Project overview and instructions
├── requirements.txt            # List of Python libraries required
├── crude_oil_analysis.py       # Main script for crude oil analysis
├── well_integrity_monitoring.py # Script for well integrity monitoring
├── data/                       # Folder containing sample data
│   ├── crude_oil_data.csv      # Sample crude oil data
│   ├── well_sensor_data.csv    # Sample well sensor data
├── reports/                    # Folder for generated reports
├── visuals/                    # Folder for saved graphs and charts
Sample Code:
1. Crude Oil Analysis Script (crude_oil_analysis.py)
python
Copy
import pandas as pd
import matplotlib.pyplot as plt

def calculate_api_gravity(density):
    """Calculate API gravity from crude oil density."""
    return (141.5 / density) - 131.5

def classify_crude_oil(api_gravity):
    """Classify crude oil based on API gravity."""
    if api_gravity > 31.1:
        return "Light"
    elif 22.3 <= api_gravity <= 31.1:
        return "Medium"
    else:
        return "Heavy"

# Load sample data
data = pd.read_csv("data/crude_oil_data.csv")

# Calculate API gravity and classify crude oil
data['API Gravity'] = data['Density'].apply(calculate_api_gravity)
data['Classification'] = data['API Gravity'].apply(classify_crude_oil)

# Save results to a CSV file
data.to_csv("reports/crude_oil_analysis_report.csv", index=False)

# Visualize API gravity distribution
plt.hist(data['API Gravity'], bins=10, edgecolor='black')
plt.title("API Gravity Distribution")
plt.xlabel("API Gravity")
plt.ylabel("Frequency")
plt.savefig("visuals/api_gravity_distribution.png")
plt.show()
2. Well Integrity Monitoring Script (well_integrity_monitoring.py)
python
Copy
import pandas as pd
import matplotlib.pyplot as plt

def detect_anomalies(pressure_data, threshold):
    """Detect anomalies in well pressure data."""
    anomalies = pressure_data[pressure_data > threshold]
    return anomalies

# Load sample sensor data
sensor_data = pd.read_csv("data/well_sensor_data.csv")

# Detect anomalies in pressure data
threshold = 5000  # Example threshold (in psi)
anomalies = detect_anomalies(sensor_data['Pressure'], threshold)

# Save anomalies to a CSV file
anomalies.to_csv("reports/well_anomalies_report.csv", index=False)

# Visualize pressure data and anomalies
plt.plot(sensor_data['Time'], sensor_data['Pressure'], label="Pressure")
plt.scatter(anomalies.index, anomalies, color='red', label="Anomalies")
plt.title("Well Pressure Monitoring")
plt.xlabel("Time")
plt.ylabel("Pressure (psi)")
plt.legend()
plt.savefig("visuals/well_pressure_monitoring.png")
plt.show()
How to Use the Project:
Clone the repository:

bash
Copy
git clone https://github.com/sumitkumar-oilfield/Crude-Oil-Analysis.git
Install the required libraries:

bash
Copy
pip install -r requirements.txt
Run the scripts:

bash
Copy
python crude_oil_analysis.py
python well_integrity_monitoring.py
Check the reports/ and visuals/ folders for outputs.

GitHub README.md Example:
markdown
Copy
# Crude Oil Quality Analysis and Well Integrity Monitoring System

This project is a Python-based tool for analyzing crude oil quality and monitoring well integrity using sensor data.

## Features
- Crude oil quality analysis (API gravity, viscosity, sulfur content).
- Well integrity monitoring with anomaly detection.
- Data visualization and report generation.

## Technologies Used
- Python, Pandas, NumPy, Matplotlib, Seaborn, ReportLab.

## How to Use
1. Clone the repository.
2. Install dependencies: `pip install -r requirements.txt`.
3. Run the scripts: `python crude_oil_analysis.py` and `python well_integrity_monitoring.py`.

## Sample Data
Sample data files are provided in the `data/` folder.

## License
This project is licensed under the MIT License.
