# flam_research-_and-_development

The repository contains files associated with **Flam’s Research and Development recruitment assignment**.

---

##  Parametric Curve Fitting Assignment

###  Objective
Estimate the unknown parameters **θ**, **M**, and **X** in the given parametric equations of a curve using the provided dataset of 1501 points (for \(6 < t < 60\)):

\[
x = \left(t\cos\theta - e^{M|t|}\sin(0.3t)\sin\theta + X\right)
\]
\[
y = \left(42 + t\sin\theta + e^{M|t|}\sin(0.3t)\cos\theta\right)
\]

---

## ⚙️ Methodology

1. **Data Cleaning:**
   - Imported and parsed `xy_data(1).csv`.
   - Converted all x, y columns to numeric, dropping invalid entries.
   - Mapped each row index *i* to \( t_i = 6 + i \times (60-6)/(N-1) \) for uniform spacing.

2. **Model Definition:**
   - Implemented parametric equations in Python with θ (degrees), M, and X as free parameters.
   - Converted θ from degrees to radians inside model computations.

3. **Parameter Optimization:**
   - Used `scipy.optimize.least_squares()` to minimize residuals between model and observed data.
   - Applied bounded constraints:
     - \(0° < θ < 50°\)
     - \(-0.05 < M < 0.05\)
     - \(0 < X < 100\)
   - Performed multiple initial guesses to avoid local minima.
   - Used **Huber loss** for robustness against outliers.

4. **Model Evaluation:**
   - Computed **L1 Distance** = ∑(|dx| + |dy|).
   - Verified fitted curve visually using **Desmos parametric graphing**.

---

## 🧮 Fitted Parameters

| Parameter | Symbol | Value |
|------------|:-------:|------:|
| Rotation Angle | θ | 27.98763891° |
| Exponential Modulation | M | 0.021038269763 |
| Horizontal Offset | X | 54.86503946 |

---

## 🧾 Final Parametric Equations

\[
\left(
t\cos(27.987639^\circ) - e^{0.02103827|t|}\sin(0.3t)\sin(27.987639^\circ) + 54.86503946,\;
42 + t\sin(27.987639^\circ) + e^{0.02103827|t|}\sin(0.3t)\cos(27.987639^\circ)
\right)
\]

---

##  Desmos Visualization

**Desmos-ready expressions (radians form):**

**Desmos Link:** [Predicted vs Actual]https://www.desmos.com/calculator/krjecqlmc1)  
*(Import your data.csv in Desmos to visualize point alignment with the curve.)*

---
x(t) = tcos(27.987639pi/180) - exp(0.02103827abs(t))sin(0.3t)sin(27.987639pi/180) + 54.86503946
y(t) = 42 + tsin(27.987639pi/180) + exp(0.02103827abs(t))sin(0.3t)cos(27.987639pi/180)
6 ≤ t ≤ 60

## 📊 Fit Statistics

| Metric | Description | Value |
|--------:|--------------|-------:|
| L1 Error | ∑(|dx| + |dy|) | **37,865.68** |
| Least Squares Cost | ½∑(dx² + dy²) | **36,398.98** |
| Fit Quality | Smooth oscillatory curve, closely matches dataset |


---
Here’s the fitted model result:

![Fitted vs Actual Curve](https://github.com/Kavinragav/flam_research-_and-_development/blob/main/Screenshot%202025-11-07%20201116.png)

As shown above, the predicted curve (red) aligns closely with the actual data (green)...

## ⚙️ Running the Code

```bash
# Clone the repository
git clone https://github.com/<your-username>/flam_research-_and-_development.git
cd flam_research-_and-_development


# Execute fitting script
python flam_fitcurve.py

