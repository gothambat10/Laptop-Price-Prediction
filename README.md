# 💻 Laptop Price Predictor 🚀

![Python](https://img.shields.io/badge/Python-3.8+-blue?style=flat-square)
![Streamlit](https://img.shields.io/badge/Streamlit-1.28+-red?style=flat-square)
![XGBoost](https://img.shields.io/badge/XGBoost-Powered-orange?style=flat-square)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.3.2-yellow?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

A cutting-edge, AI-powered machine learning application that predicts laptop prices in real-time. Built with an advanced **XGBoost Regressor** model and a stunning, modern **Streamlit** user interface.

---

## 🌐 Live Demo

Try out the application live on Hugging Face Spaces:
🔗 **[Laptop Price Predictor - Hugging Face Space](https://huggingface.co/spaces/Uttam1695/Laptop-Price-Prediction)**

*(Note: The model might take a few seconds to load upon first visit.)*

---

## 🎯 Key Features

- 🚀 **Real-time Predictions:** Get instant, highly accurate laptop price estimates.
- 🤖 **Advanced ML Model:** Powered by an XGBoost Regressor with Optuna hyperparameter tuning.
- 💎 **Modern UI:** Features a sleek dark theme with neon cyan/pink gradients and smooth interactions.
- ⚡ **Fast Processing:** Experience predictions in milliseconds.
- 📊 **Comprehensive Specs:** Evaluates 11 unique laptop specifications for precise forecasting.
- 🎨 **Responsive Design:** Optimized for seamless performance on all devices (desktop and mobile).

---

## 📸 Sneak Peek

![Laptop Price Predictor UI](Screenshot%202026-06-02%20085605.png)

*(A preview of our interactive dashboard.)*

---

## 📈 Model Performance

### **Model Comparison - R² Scores**

| Model | Training R² | Testing R² | Status |
|-------|-------------|-----------|--------|
| **XGBoost** ⭐ | 0.9240 | **0.8773** | ✅ **SELECTED** |
| Random Forest | 0.9623 | 0.8685 | Good |
| Decision Tree | 0.9733 | 0.8437 | Fair |
| Linear Regression | 0.8225 | 0.8268 | Baseline |

> **Best Model:** XGBoost is selected for production due to its optimal balance between generalization and performance.

### **Final Performance Metrics**
- **Training R²:** 0.9240
- **Testing R²:** 0.8801 ✅ *(Updated and Retrained)*
- **MAE (Mean Absolute Error):** ₹ 10,059

### **Real-World Price Tests**

| Laptop Example | Specs | Predicted Price | Real Market Price | Accuracy |
|----------------|-------|-----------------|-------------------|----------|
| **Apple MacBook Air** | i5, 8GB RAM, 256GB SSD, IPS | `₹ 82,619` | `~₹ 80k - 95k` | 🔥 Spot On |
| **Lenovo Ideapad** | i3, 8GB RAM, 256GB SSD, No IPS | `₹ 45,182` | `~₹ 35k - 45k` | ✅ Very Accurate |
| **Asus ROG Gaming** | i7, 16GB RAM, 1TB SSD, Nvidia, IPS | `₹ 95,802` | `~₹ 1.1L - 1.4L` | ⚠️ Slightly Underpriced |

---

## 🧠 Dataset & Feature Engineering

### **Dataset Overview**
- **Total Samples:** 1,303 laptops
- **Training Samples:** 1,172 (90%) | **Testing Samples:** 131 (10%)
- **Target Variable:** Log-transformed Price (to handle right-skewed data)

### **Pipeline Steps**
1. **Data Cleaning:** Removed duplicates, handled missing values, and dropped index columns.
2. **Feature Extraction:**
   - Extracted numeric values from RAM (GB) and Weight (kg).
   - Extracted TouchScreen and IPS Panel indicators from ScreenResolution.
   - Calculated **PPI (Pixels Per Inch)**: `√(Width² + Height²) / Inches`.
3. **Categorization:**
   - Grouped CPUs into: Intel i3, i5, i7, Other Intel, and AMD.
   - Grouped GPUs by brand (Intel, NVIDIA, AMD).
4. **Feature Selection:** Filtered features by correlation with price (dropped redundant ones like Inches, ScreenResolution, etc.).
5. **Final Features Used:** `Company`, `TypeName`, `Ram`, `OpSys`, `IPS_Panel`, `CPU_Category`, `i3`, `i7`, `PPI`, `GPU_Brand`, `ssd`.

---

## 🛠️ Tech Stack

- **Frontend Interface:** [Streamlit](https://streamlit.io/)
- **Machine Learning Framework:** [Scikit-learn](https://scikit-learn.org/)
- **Boosting Algorithm:** [XGBoost](https://xgboost.readthedocs.io/)
- **Hyperparameter Optimization:** [Optuna](https://optuna.org/)
- **Data Processing:** [Pandas](https://pandas.pydata.org/) & [NumPy](https://numpy.org/)
- **Visualization:** [Matplotlib](https://matplotlib.org/) & Streamlit Native Charts

---

## 🚀 Quick Start (Run Locally)

### Prerequisites
Make sure you have **Python 3.8+** installed.

### Installation & Execution

1. **Clone the repository:**
   ```bash
   git clone https://github.com/vk18chiku/Laptop_Price_Prediction.git
   cd Laptop_Price_Prediction
   ```

2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the application:**
   ```bash
   streamlit run app.py
   ```

4. **Access the App:** Open your browser and go to `http://localhost:8501`.

---

## 💻 How to Use

1. **Select Specifications:** Choose your preferred laptop brand, type, RAM, storage, OS, GPU, CPU, and display characteristics.
2. **Predict:** Click on the **"🔮 PREDICT PRICE"** button.
3. **View Result:** The model will process the inputs and display an accurate price estimate in **Indian Rupees (₹)**.

---

## 📁 Project Structure

```text
Laptop_Price_Prediction/
├── app.py                 # Streamlit web application
├── predictions.py         # Backend prediction logic
├── requirements.txt       # Project dependencies
├── clean_df.pkl           # Preprocessed & cleaned dataset
├── pipe_xgb.pkl           # Trained XGBoost pipeline/model
├── laptop_data.csv        # Original raw dataset
├── file.ipynb             # Jupyter Notebook for EDA & Model Training
├── README.md              # Project documentation
└── .gitignore             # Git ignored files
```

---

## ⚠️ Limitations & Considerations

- **Market Dynamics:** Trained on historical data; current real-world market prices may fluctuate.
- **Brand Coverage:** Limited to the ~1,300 samples; newer or niche brands might not be predicted accurately.
- **Outliers:** The model performs best on mid-range laptops; extremely high-end or specialty gaming setups might experience slight deviations.

---

## 🐛 Troubleshooting

- **App doesn't load:** Try clearing your browser cache or hard refreshing the page.
- **Incorrect predictions:** Ensure that the selected specifications are realistic combinations.
- **Slow loading on spaces:** Cloud free tiers often sleep; give it 30-60 seconds on the first load.

---



---

### 📄 License
This project is licensed under the MIT License.

---

