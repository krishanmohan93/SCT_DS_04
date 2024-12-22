# SCT_DS_04
It's a Forth task of my SkillKraft Internship
# Traffic Accident Data Analysis

This project focuses on analyzing traffic accident data to uncover patterns related to road conditions, weather, time of day, and accident hotspots. The insights derived from the analysis aim to inform road safety improvements and support data-driven decision-making.

## Features
- **Data Preparation:** Includes loading, cleaning, and exploring the dataset.
- **Time-of-Day Analysis:** Examines how accidents vary by time of day.
- **Weather and Road Conditions Analysis:** Investigates the impact of weather and road surface conditions on accidents.
- **Accident Hotspot Visualization:** Uses heatmaps to identify high-density accident areas.
- **Insights and Conclusions:** Summarizes actionable findings from the analysis.

## Dataset
- The dataset contains 2,000 entries with 10 attributes:
  - Accident ID, Date, Time, Road Condition, Weather, Light Condition, Severity, Latitude, Longitude, and Contributing Factors.
- No missing or duplicate data was found in the dataset.

## Steps
1. **Data Loading and Exploration:**
   - Load the dataset using Pandas.
   - Check dataset shape, columns, null values, and duplicates.
   - Analyze unique values and generate descriptive statistics.

2. **Visualization:**
   - Accidents by road condition, weather, and light condition using bar plots.
   - Heatmap to highlight accident hotspots on a map.

3. **Insights:**
   - Intersections and traffic signals are high-risk areas.
   - Wet or slippery roads and adverse weather contribute to higher accident rates.
   - Twilight and nighttime accidents are more frequent due to reduced visibility.

4. **Accident Hotspot Visualization:**
   - Interactive heatmaps generated using Folium and displayed dynamically in the notebook.

## Tools and Libraries Used
- **Data Processing:** Pandas, NumPy
- **Visualization:** Matplotlib, Seaborn
- **Mapping:** Folium, Folium.plugins.HeatMap
## Installation
1. Clone this repository:
   ```bash
   git clone https://github.com/krishanmohan93/SCT_DS_04.git
   cd traffic-accident-analysis
   
  ```bash
  pip install pandas numpy matplotlib seaborn folium


## Code Examples
### Load Dataset
```python
import pandas as pd

df = pd.read_csv('task4.csv')
print(df.head())

import folium
from folium.plugins import HeatMap

accident_map = folium.Map(location=[df['Latitude'].mean(), df['Longitude'].mean()], zoom_start=10)
HeatMap(data=df[['Latitude', 'Longitude']].values.tolist()).add_to(accident_map)
accident_map

import matplotlib.pyplot as plt

road_counts = df['Road Condition'].value_counts()
ax = road_counts.plot(kind='bar', color='blue', figsize=(8, 6))
plt.xlabel('Road Condition')
plt.ylabel('Number of Accidents')
plt.grid(True)
plt.tight_layout()
plt.show()


