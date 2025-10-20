# 🔍 ERP Project Effort Overrun Predictor — ML + Dashboard 

An interactive data science project to **predict project effort overruns** in ERP implementations using machine learning and visualize the predictions via an interactive Plotly dashboard. This prototype is built entirely in **Google Colab**, making it easy to share, extend, and deploy.

---

## 📌 Objective

ERP implementations often suffer from inaccurate effort estimations, leading to cost/time overruns. This project aims to:

- **Predict the effort overrun ratio** of an ERP project using project metadata
- **Identify key drivers** that contribute to overruns
- Provide an **interactive dashboard** to simulate project scenarios and visualize risk
- Serve as a foundation for internal tools, project planning, or client advisory

---

## 📊 Dataset Overview

The dataset was compiled from internal project performance records, particularly focused on:

- Estimated vs Actual Effort (from COCOMO II and Expert Judgment)
- Multiple dimensions of effort complexity:
  - Report Points
  - Form Points
  - POS Points
  - Integration Points
  - Workflow Points
  - Data Entity Points
- Complexity indicators (Simple / Complex)
- Reuse and Rework percentages

🧮 **Target Variable**:  
Effort Overrun Ratio = `Actual Effort / Estimated Effort`

🗂 **Number of Records**: 21 projects  
🧾 **File Type**: Excel Workbook (`.xlsx`)

---

## 🛠️ Tools & Libraries Used

- **Google Colab**
- **Python (3.10+)**
- **Pandas, NumPy** — data processing
- **Matplotlib, Seaborn, Plotly** — visualization
- **scikit-learn** — ML models (Random Forest, Linear Regression)
- **SHAP** — feature importance and explainability
- **ipywidgets** — dashboard interactivity

---

## 🤖 Models Used

| Model              | MAE    | RMSE   | R² Score   | Remarks |
|-------------------|--------|--------|------------|---------|
| Random Forest      | 0.88   | 1.03   | -2.15      | Most usable, but unstable due to data size |
| Linear Regression  | 11.30  | 17.45  | -900.82    | Failed — data too complex and sparse for linear fit |

📌 *Despite poor R² values due to small dataset size, the Random Forest model provided usable overrun predictions and supported the dashboard logic.*

---

## 📈 Interactive Dashboard (in Colab)

The project includes an **interactive calculator/dashboard** using `Plotly` and `ipywidgets`:

- Adjust key project parameters (Report/Form/Integration/Workflow Points)
- Choose between **Random Forest** or **Linear Regression**
- Get **instant prediction of overrun ratio**
- Visual gauge indicating project risk (green/yellow/red)

🔧 Built-in to the Colab Notebook — no external app needed!

---

## 📊 SHAP Analysis (Model Explainability)

Using SHAP values, we examined which project features had the greatest influence on predicted overruns. Key drivers included:

- `Equivalent Report Points`
- `Integration Points`
- `BB Reuse Percentage`
- `WB Rework Percentage`

📌 *These insights can guide project estimation and identify high-risk projects early.*

---

## 📌 Key Takeaways

- The current model is a **prototype** trained on a very small dataset (21 projects)
- Even with limited data, it demonstrates a working concept of **effort risk scoring**
- The dashboard can support **internal planning**, **client advisory**, or **pre-sales analysis**

---

## 📍 Interpretation of Model Results

### 🔷 Random Forest
- Average error ≈ 88% of actual effort
- Better fit for nonlinear, sparse data
- Usable in dashboard context

### 🔶 Linear Regression
- Failed due to multicollinearity and dataset size
- Errors were extreme and unpredictable

---

## 🔮 Future Scope

- 🔄 **Collect more data** to improve model performance and generalizability
- 📉 Convert to **classification** (e.g., “low / medium / high overrun risk”)
- 📊 Deploy as a **Streamlit** or **Dash** web app
- 📥 Accept user-uploaded project plans and return predicted risk
- 📘 Add PDF/HTML export functionality for reports
- 💬 Integrate NLP for extracting features from project descriptions

---

