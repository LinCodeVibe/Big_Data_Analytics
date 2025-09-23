# 🚗 CO₂ Emissions Analysis using CLI & Spark MLlib  

## 📌 Project Objective  

**Hypothesis:** *Larger engines always produce more CO₂ emissions.*  

This project uses the **CO₂ Emissions dataset** (vehicle-level records of light-duty cars and trucks from Natural Resources Canada) to test whether **engine size** and **fuel consumption** are significant predictors of CO₂ emissions.  

**Focus Areas**:  
1. Extracting statistical correlations  
2. Employing Spark MLlib machine learning models  
3. Visualizing data-driven insights  

---

## 📊 Dataset Metadata  

- **Entries:** 7,385 rows  
- **Features:** Make, Model, Vehicle Class, Engine Size (L), Cylinders, Transmission, Fuel Type, Fuel Consumption (City/Hwy/Combined), CO₂ Emissions (g/km)  
- **Key Stats:**  
  - Average CO₂ Emissions: **250.6 g/km**  
  - Engine Size Range: **0.9 – 8.4 L** (Mean: 3.16 L)  
  - Fuel Consumption City Range: **4.2 – 30.6 L/100km** (Mean: 12.56)  
- **Top Vehicle Makes:** Ford, Chevrolet, BMW, Mercedes-Benz, Porsche  

---

## ⚙️ CLI & Spark ML Implementation  

1. **Preprocessing (CLI Tools):**  
   - Used `head`, `tail`, `wc`, `awk`, `sed`, `cut`, `sort`, `uniq` for raw CSV exploration  
   - Extracted key stats: CO₂, engine size, and city fuel consumption  

2. **Data Loading (Spark):**  
   - `spark.read.format("csv")` with schema inference → DataFrame  

3. **Feature Selection:**  
   - **Inputs:** Engine Size (L), Fuel Consumption City (L/100 km)  
   - **Target:** CO₂ Emissions (g/km)  

4. **ML Pipelines (Spark MLlib):**  
   - `VectorAssembler` → combined features  
   - `randomSplit` → 80/20 train-test  
   - Models: **DecisionTreeRegressor**, **LinearRegression**  

5. **Evaluation:**  
   - Compared **RMSE** (Root Mean Square Error)  
   - Analyzed **coefficients** (linear regression)  
   - Checked **feature importances** (decision tree)  

---

## 🔎 Findings (Nontrivial Insights)  

- **Model Accuracy:**  
  - Decision Tree RMSE: **16.91 g/km** ✅  
  - Linear Regression RMSE: **20.98 g/km**  

- **Feature Importance (Decision Tree):**  
  - Fuel Consumption City: **93.9%**  
  - Engine Size: **6.0%**  

- **Key Insights:**  
  - Bigger engines emit more CO₂, but **city fuel consumption** is a **far stronger predictor**  
  - This challenges the simple assumption *“Larger engines always produce more CO₂”*  

---

## 📈 Visualizations  

**1. Feature Importance (Decision Tree)**  
![Feature Importance](results/feature_importance.png)  

**2. Residual Plot (Linear Regression)**  
![Residual Plot](results/residual_plot.png)  

_Interpretation:_  
- Fuel consumption dominates as the most important factor.  
- Non-linear residual patterns suggest linear regression is less suitable than tree-based models.  

---

## 📂 Repository Structure  

