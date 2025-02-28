# customer_segmentation
Customer segmentation using RFM analysis, UMAP, and clustering
# Online Gift Store Customers Segmentation

## 📌 Project Overview

This project focuses on **customer segmentation** for an online gift store using **RFM analysis** and clustering techniques. The goal is to identify distinct customer groups based on purchasing behavior to enhance targeted marketing strategies and improve customer relationship management.

## 📂 Dataset

The dataset is sourced from **The UCI Machine Learning Repository** and contains **transactional records from an online gift store** operating between **01/12/2010 and 09/12/2011**. The company sells unique gifts, with many of its customers being wholesalers.

### **Features:**

- **InvoiceNo** – Unique transaction ID (prefix 'C' indicates a canceled transaction).
- **StockCode** – Unique product ID.
- **Description** – Product name.
- **Quantity** – Number of units purchased.
- **InvoiceDate** – Date and time of transaction.
- **UnitPrice** – Price per unit in GBP (£).
- **CustomerID** – Unique customer identifier.
- **Country** – Customer's country.

## 🔧 Data Preprocessing

1. **Handling Missing Values**
   - Removed transactions with missing `CustomerID` and `Description`.
2. **Duplicate Removal**
   - Identified and removed duplicate entries.
3. **Processing Returns & Special Transactions**
   - Created `QuantityCancelled` to track returned items.
   - Removed transactions containing special product codes (e.g., postage fees, bank charges).
4. **Filtering Outliers**
   - Removed transactions with zero or negative unit prices.
5. **Feature Engineering**
   - Calculated **TotalPrice** (`UnitPrice * (Quantity - QuantityCancelled)`).
   - Extracted **Purchase Time Features** (`Month`, `Weekday`, `Hour`).
   - Created a `IsWholesale` indicator (bulk orders).
   - Created **Unique Items Per Order** feature.

## 📊 Exploratory Data Analysis (EDA)

Key insights extracted:

- **Top buying countries** (most orders and revenue contributors).
- **Seasonality in sales** (peak months, days, and hours of transactions).
- **Most valuable customers** based on spending.
- **Frequent return patterns** and affected products.
- **Average Order Value (AOV) distribution.**

## 🔍 Customer Segmentation (RFM Analysis)

To cluster customers, we calculated the **Recency, Frequency, and Monetary (RFM) scores**:

- **Recency** – Days since last purchase.
- **Frequency** – Total number of unique purchases.
- **Monetary** – Total spending amount.

## 🧠 Clustering Methods & Model Selection

### **Dimensionality Reduction:**

- **PCA** – Used to reduce high-dimensional data to 2D space.
- **t-SNE** – Used to reduce high-dimensional data to 2D space.

* **UMAP** – Used to reduce high-dimensional data to **2D space** (showed the best results).

### **Clustering Algorithms Tested:**

- **K-Means** (Best Model: K-Means with 5 Clusters, Silhouette Score: **0.6029**)
- **Agglomerative Clustering (Silhouette Score: 0.5897)**
- **DBSCAN** (Density-Based Clustering)
- **Gaussian Mixture Model (GMM)** 

### **Handling Outliers:**

- Used **Isolation Forest** to remove extreme outliers before clustering.

### **Visualizations:**

- **Top 10 Countries by Revenue** [View Chart] (https://wsiqz.github.io/customer_segmentation/top_10_countries_by_revenue.html)

- **Monthly Revenue** (see Project)

- **Daily Orders over Time** (see Project)

- **Sales Trend by Day of the Week** [View Chart] (https://wsiqz.github.io/customer_segmentation/sales_trend_by_day_of_the_week.html)

- **Orders by Hour** (see Project)

- **Top 10 Customers by Total Spending** [View Chart] (https://wsiqz.github.io/customer_segmentation/top_10_customers_by_total_spending.html)

- **Distribution of AOV** [View Chart] (https://wsiqz.github.io/customer_segmentation/distribution_of_average_order_value.html)

- **Top 10 Returned Products** [View Chart] (https://wsiqz.github.io/customer_segmentation/top_10_returned_products.html)

- **RFM Boxplots** [View Chart] (https://wsiqz.github.io/customer_segmentation/rfm_boxplots.html)
 (https://wsiqz.github.io/customer_segmentation/rfm_boxplots_filtered.html)

- **2D RFM Scatter Plot** 
[View Chart] (https://wsiqz.github.io/customer_segmentation/rfm_scatter_plot.html)

- **2D RFM PCA Scatter Plot** [View Chart] (https://wsiqz.github.io/customer_segmentation/rfm_pca_scatter_plot.html)

- **2D RFM t-SNE Scatter Plot** [View Chart] (https://wsiqz.github.io/customer_segmentation/rfm_tsne_scatter_plot.html)

- **2D RFM t-SNE Clusters Scatter Plot** [View Chart] (https://wsiqz.github.io/customer_segmentation/rfm_tsne_clusters.html)

- **2D RFM UMAP Scatter Plot** [View Chart] (https://wsiqz.github.io/customer_segmentation/rfm_umap_scatter_plot.html)

- **2D RFM UMAP Clusters Scatter Plot** [View Chart] (https://wsiqz.github.io/customer_segmentation/rfm_umap_clusters.html)

- **2D RFM UMAP (no outliers) Clusters Scatter Plot** [View Chart] (https://wsiqz.github.io/customer_segmentation/rfm_umap_clusters_clean.html)

- **3D Final Clusters Scatter Plot** [View Chart] (https://wsiqz.github.io/customer_segmentation/rfm_3d_clusters_clean.html)

- **Cluster Profile Radar Chart** [View Chart] (https://wsiqz.github.io/customer_segmentation/cluster_profile.html)

## 🔍 Key Findings (Customer Segments)

1. **Loyal High-Spenders** – Frequently purchase and spend large amounts.
2. **Occasional Buyers** – Infrequent orders but moderate spending.
3. **New Customers** – Recently made first purchases.
4. **High-Value Inactive Customers** – Previously spent a lot but stopped buying.
5. **Discount Hunters** – Small but frequent purchases, possibly during sales.
6. **Churned Customers** – Haven’t purchased in a long time with low spending history.

## 🚀 How to Run the Project

1. Clone the repository:
   ```bash
   git clone https://github.com/wsiqz/customer_segmentation.git
   cd customer_segmentation
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the Jupyter Notebook:
   ```bash
   jupyter notebook PROJECT-6._Online_gift_store_customers_segmentation.ipynb
   ```

## 🛠 Technologies Used

- **Python** (Pandas, NumPy, Scikit-learn, Plotly, UMAP)
- **Machine Learning** (Clustering, Outlier Detection, Dimensionality Reduction)
- **Jupyter Notebook** (For interactive analysis)

## 📁 Repository Structure

```
📂 customers_segmentation
│-- 📄 PROJECT-6._Online_gift_store_customers_segmentation.ipynb
│-- 📄 README.md
│-- 📄 requirements.txt
│-- 📂 data/ (Cleaned transactions dataset, Original dataset)
|-- 📂 images/ (Plots(png))
|-- 📂 docs/ (Plots(html))
```

## 🎯 Future Improvements

- Implement **Deep Learning-based clustering** for better accuracy.
- Apply **time-series forecasting** for predicting future customer behavior.
- Develop **automated dashboards** for real-time insights.

## 📜 License

This project is open-source and available under the **MIT License**.

---

**Developed by Mariya Kostyrya** – Customer Segmentation Using Machine Learning 📊🚀

