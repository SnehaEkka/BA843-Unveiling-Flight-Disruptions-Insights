# Unveiling Flight Disruptions: Insights & Prediction  
#### *"Data-driven analysis of U.S. commercial flights to understand and forecast delays and cancellations"*

![](https://github.com/SnehaEkka/BA843-Unveiling-Flight-Disruptions-Insights/blob/main/flight-disruptions-analytics.png)

## About  
This project analyzes five years of U.S. flight delay and cancellation data (2018–2022) to uncover operational patterns across locations, airlines, and time. It combines large-scale exploratory data analysis (EDA) with machine learning models to predict delay durations, providing actionable insights for passengers, airlines, and airport authorities.

## Data Source  
- **Primary Dataset:** [Flight Delay Dataset 2018–2022 – Kaggle](https://www.kaggle.com/datasets/robikscube/flight-delay-dataset-20182022)  
- **Data Volume:** ~29 million flight records (~10GB), including 61 attributes covering schedule, airline, location, timing, and operational status.  
- **Source Systems:** Marketing Carrier On-Time Performance data from the U.S. DOT TranStats database.  

## Project Goals  
1. Identify trends and patterns in flight delays and cancellations, segmented by:
   - **Location**: Cities, airports, and routes  
   - **Airline**: Performance and delay/cancellation rates  
   - **Time**: Time of day, day of week, month, year, and seasonal variations  
2. Detect cancellation and delay hotspots.  
3. Build predictive ML models to classify flights into **delay-duration categories**.  
4. Provide data-backed operational recommendations to minimize disruptions.

## Analysis Overview  

### **1. Descriptive Analysis**
- **Location Insights:**  
  - Dallas–Fort Worth (DFW) is a major delay hotspot, driven largely by regional carriers.  
  - Chicago O’Hare (ORD), DFW, and Denver (DEN) lead cancellation counts.  
  - Evening & night flights show the longest average delays (~19 minutes around 7 PM).  

- **Airline Insights:**  
  - Major carriers like Southwest, American, Delta, and United manage higher volumes with lower cancellation *rates* compared to smaller/regional airlines.  
  - Regional carriers such as Peninsula Airways top cancellation *rates* (~15%).  

- **Time-based Trends:**  
  - Cancellations spike in winter/early spring due to weather, especially March–April.  
  - COVID-19 caused unprecedented cancellation peaks in March–April 2020 (~41% of flights).  
  - Summer shows the highest average delay rates, peaking in June (~38.6%).  

### **2. Machine Learning: Delay Duration Classification**  
**Objective:** Predict delay categories for delayed flights (excluding “On Time/Early” flights).  
**Delay Buckets:**
- Up to 15 mins  
- 15–30 mins  
- 30–60 mins  
- More than 1 hour  

**Algorithms Tested:** Logistic Regression, Decision Tree, Random Forest (via PySpark MLlib).  
**Key Results (Base Models):**
| Model                | Accuracy | Precision | Recall | F1 Score |
|----------------------|----------|-----------|--------|----------|
| Logistic Regression  | ~50%     | 0.526     | 0.500  | 0.377    |
| Decision Tree        | ~49.8%   | 0.323     | 0.498  | 0.364    |
| Random Forest        | ~48.4%   | 0.234     | 0.484  | 0.316    |

- **Best Performer:** Logistic Regression (baseline).  
- **Top Predictive Features:** Certain small airports (e.g., YNG, ROP) and *morning flights* for >1 hour delays.  
- **Hyperparameter tuning** on Logistic Regression did not improve performance, pointing to the need for better feature engineering.

## Key Business Impact & Insights  

- **Operational Hotspots:**  
  - Targeted improvement efforts in Dallas and major eastern hubs could yield significant delay reductions.  

- **Resource Allocation:**  
  - Regional carriers may benefit from schedule padding and better weather planning.  

- **Customer Value:**  
  - Predictive delays give passengers proactive tools to adjust itineraries, reducing stress and missed connections.  

- **Seasonal Planning:**  
  - Airlines can reassign aircraft and crews around seasonal peaks (summer delays/winter cancellations).  

## How to Run the Analysis  

**Requirements**
- Python (PySpark environment recommended)  
- Libraries: `pyspark`, `pandas`, `numpy`, `matplotlib`, `seaborn`, `folium`  

**Steps**
1. Clone the repository:  
   ```bash
   git clone https://github.com/SnehaEkka/BA843-Unveiling-Flight-Disruptions-Insights.git
   cd BA843-Unveiling-Flight-Disruptions-Insights
   ```
2. Download & place dataset in `/data` folder (or change notebook paths).  
3. Run the Jupyter Notebook:
   ```bash
   Jupyter Notebook "BA843 BA7 Unveiling Flight Disruptions Insights.ipynb"
   ```
4. Follow notebook sections in sequence:  
   - Data load & cleaning  
   - EDA by Location, Airline, Time  
   - ML model building & evaluation  

## Future Improvements  
- Add weather and air traffic control event data for richer feature sets.  
- Explore advanced ML models (XGBoost, LightGBM, Neural Networks).  
- Deploy as a web dashboard showing real-time delay predictions.  
- Investigate causal relationships between external events and disruptions.

## Coursework & Contributors
- **Coursework:** Completed as part of **BA843 – Big Data Analytics** course (Boston University MSBA program), with emphasis on large-scale data handling, EDA storytelling, and applied machine learning.
- **Contributors:**
  - Jinke Han – Data cleaning, preprocessing, visualization design
  - Mingze Wu – Data integration (PySpark), large dataset handling
  - Tanvi Sheth – EDA insights, feature engineering, ML experiments
  - YuChun Su – Visual storytelling, presentation design
  - Sneha Ekka – EDA (Location/Airline/Time), ML pipeline, model evaluation, documentation

## Additional Resources  
- 📄 Flight Disruptions Insights & Prediction: [Presentation Deck](https://www.canva.com/design/DAGD59dx0lU/WybhJvO_EDxkL69OAM0VFQ/view?utm_content=DAGD59dx0lU&utm_campaign=designshare&utm_medium=link2&utm_source=uniquelinks&utlId=hf6de60444e)  
- 📑 [Final Project Report](BA843-BA7-Unveiling-Flight-Disruptions-Insights.pdf)
