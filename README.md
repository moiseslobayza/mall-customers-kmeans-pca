# Shopping Customer Segmentation with K-Means and PCA

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1yo3t1uVk8ncN8DQNwEM5_L_Xyy8agyUv)

---


This project applies **K-Means clustering** and **PCA** to segment shopping mall customers using the *Mall Customers* dataset.  
The goal is to identify groups of customers with similar spending behavior in order to design more targeted marketing strategies.

---

## 🧾 Dataset

- **Name:** Mall Customers  
- **Main variables:**
  - `Gender`
  - `Age`
  - `Annual Income (k$)`
  - `Spending Score (1-100)` (how much the customer spends in the mall)

The file is stored in: `data/Mall_Customers.csv`.

---

## 🔍 Methodology

1. **Data loading and preparation**
   - Load the CSV file.
   - Create the numerical variable `Gender_num` from `Gender`.
   - Build `df_model` with numeric features only:
     - `Age`, `Annual Income (k$)`, `Spending Score (1-100)`, `Gender_num`.

2. **Feature scaling**
   - Use `StandardScaler` to standardize all features  
     (mean 0, standard deviation 1) before applying PCA and K-Means.

3. **Dimensionality reduction with PCA**
   - Apply PCA with **2 principal components**.
   - The first two components explain about **60%** of the total variance.
   - Visualize the data in the 2D PC1–PC2 space.

4. **Choosing the number of clusters**
   - Train K-Means models for `k` from 2 to 10.
   - Evaluate with:
     - **Elbow method** (inertia).
     - **Silhouette score**.
   - Select **k = 4** as a good trade-off between compact and well-separated clusters.

5. **Final K-Means model**
   - Train K-Means with `k = 4` on the PCA components.
   - Assign a `cluster` label to each customer.
   - Visualize clusters in PCA space:

   ![K-Means Clusters in PCA](reports/figures/clusters_pca_k4.png)

6. **Cluster analysis**
   - Compute mean values per cluster (`Age`, `Annual Income`, `Spending Score`, `Gender_num`).
   - Interpret each group as a customer profile.

---

## 📊 Customer profiles (summary)

- **Cluster 0 – Young premium, very active**  
  Customers around 30 years old, with **high income** and **high spending score**. Mostly male.  
  → Heavy spenders who are likely to respond well to loyalty programs and exclusive offers.

- **Cluster 1 – Older, high income but low activity**  
  Around 48 years old, **high income** but **low spending score**. Mostly male.  
  → High potential segment: good purchasing power but low mall usage; good candidates for targeted campaigns to increase frequency and average ticket.

- **Cluster 2 – Lower income, low spenders**  
  About 49 years old, **lower income** and **low spending score**. Mostly female.  
  → More price-sensitive segment; discounts, coupons and budget-friendly bundles may work better here.

- **Cluster 3 – Young, medium income, high spenders**  
  The youngest group (~27 years), with **medium income** and **high spending score**. Mostly female.  
  → Very active segment, likely attracted by fashion, entertainment and experiences; key for retention and long-term loyalty.

---

## How to Run

```bash
pip install -r requirements.txt
jupyter notebook notebooks/book_sales_tree_vs_knn.ipynb
```
## 📜 License
MIT License — This project is for educational and portfolio purposes.
