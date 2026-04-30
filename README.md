# MALL-CUSTOMER
Segmented 200 retail customers into 5 behavioral groups using K-Means clustering in Python — visualized in an interactive Power BI dashboard with income, spending &amp; demographic insights.
# 🛍️ Customer Segmentation using K-Means Clustering + Power BI

![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=flat-square&logo=python&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?style=flat-square&logo=powerbi&logoColor=black)
![Pandas](https://img.shields.io/badge/Pandas-EDA-150458?style=flat-square&logo=pandas&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat-square)

> **Unsupervised Machine Learning project** that segments 200 retail customers into 5 distinct behavioral groups using K-Means clustering — with an interactive Power BI dashboard for business insights.

---

## 📌 Project Overview

Retail businesses need to understand *who* their customers are to target them effectively. This project applies **K-Means clustering** on the Mall Customers dataset to group customers based on their **Annual Income** and **Spending Score** — then visualizes the segments in a fully interactive **Power BI dashboard**.

The goal is to answer:
- Who are the high-value customers?
- Which segments are being under-served?
- How should marketing budget be allocated across customer groups?

---

## 🎯 Key Findings

| Segment | Avg Income | Avg Spending | Business Insight |
|---|---|---|---|
| 🟣 **Premium Targets** | High | High | Top-priority — loyal, high-value buyers |
| 🔴 **Impulsive Buyers** | Low | High | Respond well to flash sales & promotions |
| 🟢 **Standard Customers** | High | Medium | Upsell opportunity with loyalty programs |
| 🟡 **Budget Conscious** | Low | Low | Engage with discounts and value offers |
| 🔵 **Careful Spenders** | High | Low | Build trust — needs convincing |

---

## 🗂️ Project Structure

```
customer-segmentation/
│
├── customer_segmentation.py     # Main Python script (full pipeline)
├── Mall_Customers.csv           # Raw dataset (from Kaggle)
├── segmented_customers.csv      # Output with cluster labels → Power BI input
│
├── outputs/
│   ├── eda_analysis.png         # EDA: distributions, heatmap, scatter
│   ├── elbow_silhouette.png     # Optimal K selection charts
│   └── cluster_visualisation.png# Final 4-panel cluster results
│
├── Customer_Segmentation.pbix   # Power BI dashboard file
└── README.md
```

---

## 🧰 Tech Stack

| Tool | Purpose |
|---|---|
| Python 3.8+ | Core programming language |
| Pandas | Data loading, cleaning, manipulation |
| NumPy | Numerical computations |
| Matplotlib & Seaborn | EDA visualizations |
| Scikit-learn | StandardScaler + KMeans + Silhouette Score |
| Power BI Desktop | Interactive business dashboard |

---

## 📊 Dataset

**Mall Customers Dataset** — publicly available on Kaggle

| Column | Description |
|---|---|
| CustomerID | Unique customer identifier |
| Genre | Gender (Male / Female) |
| Age | Customer age |
| Annual Income (k$) | Annual income in thousands |
| Spending Score (1-100) | Score assigned by mall based on spending behavior |

- **Rows:** 200 customers
- **Source:** [Kaggle — Customer Segmentation Tutorial](https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial)

---

## ⚙️ How to Run

### 1. Clone the repository
```bash
git clone https://github.com/rinkle-YADAV/customer-segmentation.git
cd customer-segmentation
```

### 2. Install dependencies
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

### 3. Download the dataset
Download `Mall_Customers.csv` from [Kaggle](https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial) and place it in the project root.

### 4. Run the Python script
```bash
python customer_segmentation.py
```

This will generate:
- `eda_analysis.png` — EDA charts
- `elbow_silhouette.png` — Optimal K charts
- `cluster_visualisation.png` — Final cluster plots
- `segmented_customers.csv` — Labeled data for Power BI

### 5. Open Power BI Dashboard
- Open `Customer_Segmentation.pbix` in **Power BI Desktop**
- Refresh the data source to point to `segmented_customers.csv`
- Explore segments using the **Segment slicer**

---

## 🔬 Methodology

### Step 1 — Exploratory Data Analysis
- Checked for null values, duplicates, data types
- Plotted distributions of Age, Income, and Spending Score
- Gender-wise boxplots to understand demographic spread
- Correlation heatmap to identify feature relationships

### Step 2 — Feature Scaling
Applied `StandardScaler` to normalize `Annual Income` and `Spending Score` before clustering — ensures no feature dominates due to scale difference.

```python
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
X_scaled = scaler.fit_transform(df[['Annual Income (k$)', 'Spending Score (1-100)']])
```

### Step 3 — Finding Optimal K
Used two methods to determine the best number of clusters:
- **Elbow Method** — plots WCSS (Within-Cluster Sum of Squares) vs K; look for the "elbow"
- **Silhouette Score** — measures how well each point fits its cluster vs others

**Result: K = 5** was selected as the optimal number of clusters.

### Step 4 — K-Means Clustering
```python
from sklearn.cluster import KMeans
km = KMeans(n_clusters=5, random_state=42, n_init=10)
df['Cluster'] = km.fit_predict(X_scaled)
```

### Step 5 — Cluster Naming
Clusters were automatically named based on each cluster's mean Income and Spending Score relative to the dataset median — giving each segment a business-friendly label.

### Step 6 — Power BI Dashboard
Imported `segmented_customers.csv` into Power BI and built:
- Segment **slicer** for filtering all visuals
- **KPI cards**: Total Customers, Avg Income, Avg Spending Score
- **Scatter chart**: Income vs Spending Score (color by Segment)
- **Bar chart**: Customer count per Segment
- **Donut chart**: Gender split per Segment
- **Summary table**: Avg Age, Income, Spending by Segment

---

## 📈 Results & Visualisations

### EDA Analysis
![EDA Analysis](outputs/eda_analysis.png)

### Optimal K Selection
![Elbow and Silhouette](outputs/elbow_silhouette.png)

### Customer Segments
![Cluster Visualisation](outputs/cluster_visualisation.png)

---

## 💡 Business Recommendations

- **Premium Targets** → Offer loyalty rewards, early access, and premium memberships
- **Impulsive Buyers** → Target with limited-time deals, flash sales, and social proof
- **Careful Spenders** → Send personalized product recommendations and detailed reviews
- **Budget Conscious** → Promote budget bundles, coupons, and clearance events
- **Standard Customers** → Upsell with cross-category offers and loyalty points

---

## 🔗 Connect

**Rinkle Yadav** — Data Analyst

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin)](https://linkedin.com/in/rinkle-yadav-402a67304)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=flat-square&logo=github)](https://github.com/rinkle-YADAV)
[![Email](https://img.shields.io/badge/Email-Contact-EA4335?style=flat-square&logo=gmail)](mailto:rinkleyadav91@gmail.com)

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
