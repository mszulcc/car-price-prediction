# Car Price Prediction – Project Report

## 1. Goal
The goal of the project was to create a model that predicts car prices based on various sets of features.

---

## 2. Data
- Dataset source: [Car Sales Offers (OtomotoPL 2023)](https://www.kaggle.com/datasets/szymoncyperski/car-sales-offers-from-otomotopl-2023)
- Initial preprocessing done in **Excel**:
  - Removed unnecessary columns (original dataset had ~100).
  - Standardized values.
  - Replaced the **year of production** column with **car's age**.
  - Identified the **voivodeship** for each location (discarded 6,419 rows where this was not possible).
- Final dataset size: **201,787 records**.

### Feature sets
- **Set 1**:  
  Car age, mileage, engine size, fuel type, power, province, offer from (private/dealer), vehicle make, city fuel consumption, transmission, body type, color, condition  
  → **117,462 records** (after removing blanks)

- **Set 2**:  
  Car age, mileage, engine size, power, fuel type, vehicle make  
  → **197,321 records** (after removing blanks)

- Data split: **80% training / 20% test**

---

## 3. Models
The project compared the performance of four models:

- **Random Forest**
- **Decision Tree**
- **Linear Regression**
- **Neural Network**  
  - Architecture: 4 layers (1024, 512, 256)  
  - Activation: ReLU  
  - Dropout: 0.3  
  - Final layer: 1 neuron  
  - Optimizer: Adam  
  - Epochs: 20

---

## 4. Evaluation
Metrics used: **MAE**, **MSE**, **R²**

| Model                  | Feature Set | MAE       | MSE       | R²   |
|-------------------------|-------------|-----------|-----------|------|
| Random Forest           | Set 1       | 10,625.74 | 734,614,717.42 | 0.91 |
| Random Forest           | Set 2       | 14,416.57 | 1,529,891,959.57 | 0.87 |
| Decision Tree           | Set 1       | 14,746.01 | 1,457,229,556.51 | 0.82 |
| Decision Tree           | Set 2       | 17,823.63 | 2,505,331,803.64 | 0.79 |
| Linear Regression       | Set 1       | 25,679.59 | 2,627,346,579.71 | 0.68 |
| Linear Regression       | Set 2       | 33,322.92 | 4,028,970,676.52 | 0.66 |
| Neural Network          | Set 1       | 12,176.82 | 951,210,752     | 0.87 |
| Neural Network          | Set 2       | 16,614.37 | 1,787,761,536   | 0.83 |

---

## 5. Conclusions
- **Random Forest (Set 1)** achieved the best results with the highest R² (0.91) and the lowest MAE.  
- It also required **less training time** compared to the Neural Network.  
- **Linear Regression** performed the worst, especially with **Feature Set 2**.  
- **Feature Set 1** consistently outperformed **Feature Set 2**, indicating that additional features (e.g., fuel consumption, condition, transmission) have a significant influence on car price prediction.

---
