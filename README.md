# Ev-Analysis
## Overview 
This Project ecplores trends in electric vehicle (EV) adoption worldwide and across key regions (World, Norway, United Kingdom, EU27, China, and USA) from 2011 to 2023. Using historical EV sales and sales share data, we created interactive visualizations to analyze the share of new cars that are electric, including battery-electric vehicles (BEVs) and plug-in hybrid electric vehicles (PHEVs). The project also demonstrates how we created a dashboard app through deployment on Google Cloud Platform (GCP).
## Features
- **Data Analysis**: Used aggregate and analysis function in Python for EV sales data to filter among regions, years
- Used for loops and other math codes to find the toal percentage of all cars bought that were EV.
- **Interactive Visualizations**: Used Plotly and Plotly Express to create dynamic graphs, including:
    - Stacked bar graphs
    - Line graphs
    - Subplot layout for multi-region comparisons
- **Cloud Deployment**: Deployed the analysis and visualizations as an interactive dashboard with tabs using Google Cloud Platform (GCP).
## Getting Started 
Prerequisites 
To run the project locally, ensure you have the followed installed: 
- Python 3.8+
- Required python libraries:
```python
pip install pandas plotly
```
For deployment:
- A Google Clod Platform(GCP) account with billing enabled or you can use free local deployment.
## Dataset

The dataset contains the following columns:
- region: Geographic region (e.g., World, China, USA).
- parameter: Type of data (EV sales or EV sales share).
- year: Year of observation (2011–2023).
- powertrain: Type of EV (BEV, PHEV, or EV).
- value: Numeric value (percentage or total vehicles).
- unit: Unit of measurement (percent or vehicles).

Data preprocessing involves filtering and aggregating based on these columns.
## Interactive Visualizations 
**Example Graphs**
  1. Stacked Bar Grpah: Visualizes the percentage of BEVs and PHEVs as part of EV Sales share for each region.
  2. Line Graphs with Subplots: Compares EV sales share trends across regions
**Code Highlights**
The visualizations were created using **Plotly** and customized with:
- **Hover Text**: Provides detailed insights when hovering over data points.
- **Subplots**: Compares multiple regions in a single layout.
Example Snippet:
```python
from plotly.subplots import make_subplots
import plotly.graph_objects as go

# Subplot for multiple regions
fig = make_subplots(rows=2, cols=3, subplot_titles=regions_of_interest)
for i, region in enumerate(regions_of_interest):
    region_data = ev_sales_share_df[ev_sales_share_df['region'] == region]
    trace = go.Scatter(x=region_data['year'], y=region_data['value'], mode='lines', name=region)
    fig.add_trace(trace, row=(i // 3) + 1, col=(i % 3) + 1)
fig.show()
```
## Deployment on Google CLoud Platform
1. Open Google Closed Shell
   To open Cloud Shell navigate to GCP Console and click 'Activate Cloud Shell' in the top right corner next to search bar.
   This will open a terminal in the bottom part of your browser that takes you to your own personal Linux machine to use.
2. In your home directory create a virtual environment using this command:
   ```bash
   python3 -m venv myenv
   ```
3. Activate the environment
   ```bash
   source myenv/bin/activate
   ```
4. Clone this Gitlab project
   ```bash
   git clone https://github.com/hs4704/Ev-Analysis.git]
   ```
5. Navigate to the projects root folder (cd Ev-Analysis) and then run the below commands:
  - ```pip install setuptools```
  - ```pip install -r requirements.txt```
  - ```pip install dash==2.16.1 plotly-express==0.4.1```
6. After all the packages are downloaded, start the app using the command below:
  - ```python3 main.py```
- The above command starts the Dash application on your local cloud console virtual machine
-Select 'Web Preview'-> 'Preview on port 8080' on your Google Cloud Console top menu bar.
- If you have authorization to deploy, use ```glcloud app deploy```


    
