# Vegetation Anomaly Analysis using TSA (Time Series Anomaly) in MATLAB

This repository contains a set of MATLAB scripts and functions designed to detect, quantify, and map **vegetation time series anomalies (NDVI)** caused by severe disturbances, such as forest fires. 

The core analysis utilizes the **TSA (Time Series Anomaly)** algorithm based on standard deviation history scores combined with severity thresholds adapted from dNBR (*differenced Normalized Burn Ratio*) criteria. Additionally, it includes spatial mapping capabilities using both MATLAB's native library and the `m_map` cartographic package. 

---

## 📂 Repository Content 

The source code is structured in a modular way and performs two main tasks: single pixel analysis and comprehensive geospatial mapping. [cite: 4]

### 1. Local Functions (`Core Algorithm`) 
* **`TSA(serie, umbral)`**: Sequentially scans time vectors applying element-by-element detection. 
* **`TSA_m(test, serie, umbral)`**: Background mathematical function. It compares a test value against the normal distribution of the historical record while omitting null values (`omitnan`). It classifies the result into: 
  * `1` : Positive Anomaly (Outlier increase in vegetation vigor).
  * `-1` : Negative Anomaly (Biomass loss / Forest fire impact). 
  * `0` : Normal Behavior. 

---

## 🛠️ System Requirements 

* **MATLAB** R2022a or higher. 
* **Required Toolboxes:** 
* *Mapping Toolbox* (essential if choosing native rendering via `pcolorm` and `axesm`).
* **Optional External Libraries (Highly Recommended):** 
* **`m_map`**: For the correct visualization of stylized geographic grids (`m_proj`, `m_grid`, `m_pcolor`). You can download it from the [official m_map website](https://www.eoas.ubc.ca/~rich/map.html). 

---

## 🚀 Usage Guide 

### 1. Clone the repository and prepare the data 
Navigate to your local directory and clone the repository. Make sure to place the data `.mat` files in the same root folder. 

```bash
git clone [https://github.com/tu-usuario/tu-repositorio.git](https://github.com/tu-usuario/tu-repositorio.git)
```

---
## Configure analysis variables in the Script `tsa_per_pixel`

You can open the main code in MATLAB and modify the following key parameters according to your area of ​​study:

```matlab
%% umbral theta of sensibility 
%% recomended: 0.3, 1.53, 2.40, 3.00, 3.55 acording dNBR
theta = 2.4;

%% year of analysis. Interval (2000-2025)
year = 2022 ;

%% matix size: 722x260
%% pixel analyzed 

%%% pixel 1: affected by forest fire
% pixel described in figure 3 of article
xpixel = 167; 
ypixel = 318; 
```

## Run spatial analysis (`tsa_per_day`)

To change the map to a specific date after the fire event, modify the `id_day` index in the mapping section:
```matlab
% Before the wildfires
% 511: March 6, 2022

% After the wildfires 
% 516: May 25, 2022
% 518: June 26, 2022
% 526: November 1, 2022
% 538: May 9, 2023
% 550: November 17, 2023
% 552: December 19, 2023
% 560: April 22, 2024
% 570: September 29, 2024
% 575: December 18, 2024

id_day = 516;
```
