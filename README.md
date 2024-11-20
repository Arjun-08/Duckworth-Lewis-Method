
# **Duckworth-Lewis Method**

## **Description**
This repository contains the implementation and analysis of the Duckworth-Lewis Method for ODI cricket matches using data from 1999 to 2011. The objective is to model the run production function using a mathematical formulation and optimize parameters for the model to predict runs scored based on overs remaining and wickets in hand.

The repository includes:
- Data cleaning and preprocessing.
- Implementation of the Duckworth-Lewis Method.
- Parameter optimization using custom loss functions.
- Visualization of the run production functions.

---

## **Dataset**
The dataset contains detailed information about ODI cricket matches played between 1999 and 2011, including:
- Match ID
- Innings details
- Wickets in hand
- Runs required to win
- Overs left to play

### **Cleaned Dataset**
After preprocessing, the dataset focuses on:
1. **First innings data** only.
2. **Key metrics:**
   - Wickets in hand
   - Runs to score
   - Overs left

Data cleaning ensures:
- Proper date formatting.
- Removal of invalid or erroneous data points.
- Calculation of derived metrics such as `Runs to score` and `Overs left`.

---

## **Model Overview**
The Duckworth-Lewis run production model is defined as:

\[
Z(u, w) = Z_0(w) \cdot \left[1 - e^{-\frac{L(w) \cdot u}{Z_0(w)}}\right]
\]

Where:
- \( Z(u, w) \): Predicted runs for \( u \) overs remaining and \( w \) wickets in hand.
- \( Z_0(w) \): Initial run-scoring potential with \( w \) wickets in hand.
- \( L(w) \): Rate of scoring potential decay.

---

## **Implementation Details**
### **Data Cleaning**
- The `clean_data` function processes the raw dataset to produce a cleaned and usable format for analysis.
- Key steps:
  1. Properly format date fields.
  2. Filter for first-innings data.
  3. Remove errors and anomalies.
  4. Compute derived metrics.

### **Run Production Model**
- The `run_production_model` function implements the mathematical formulation to predict runs based on \( u \), \( Z_0(w) \), and \( L(w) \).

### **Loss Function**
- A custom loss function is used to optimize the model parameters:
\[
\text{loss}(y', y) = (y' + 1) \cdot \log\left(\frac{y' + 1}{y + 1}\right) - y' + y
\]
Where \( y' \) is the predicted score, and \( y \) is the actual score.

### **Parameter Optimization**
1. **Preliminary Optimization:**
   - Parameters \( Z_0(w) \) and \( L(w) \) are optimized for each wicket category.
2. **Weighted Average Slope:**
   - A common slope \( L \) is calculated as the weighted average of \( L(w) \).
3. **Final Optimization:**
   - Refitting \( Z_0(w) \) using the common slope \( L \).

### **Visualization**
- Plots are generated to visualize the preliminary and final run production functions for all wicket categories.

---

## **Results**
### **Preliminary Parameters**
- \( Z_0(w) \): Initial scoring potential per wicket.
- \( L(w) \): Slope indicating scoring potential decay.
- Normalized loss: **6.18**

### **Final Parameters**
- \( Z_0(w) \): Refined scoring potential per wicket.
- Common slope \( L \): **10.63**
- Normalized loss: **6.19**

### **Plots**
1. **Preliminary Run Production Functions** (Figure 1): Shows \( Z(u, w) \) based on preliminary \( Z_0(w) \) and \( L(w) \).
2. **Final Run Production Functions** (Figure 2): Updated \( Z(u, w) \) using refined parameters.

---

## **Usage**
### **Dependencies**
- Python 3.x
- Required libraries: `numpy`, `pandas`, `matplotlib`, `scipy`


##Contact
If you have any questions or suggestions, please feel free to reach out to me at nvarjunmani07@gmail.com.
