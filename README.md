# Prasiskom2-Project-Prediksi-Harga-Rumah
# 🏡 **House Price Prediction – Machine Learning Project**

> *Final Project – Praktikum Sistem Telekomunikasi II (Prasiskom 2)*
> Kelompok 6 | Kelas 4A
> Universitas Pendidikan Indonesia, Kampus Purwakarta
> Tahun 2025

---

## 👥 **Team Members**

| Nama                    | NIM     |
| ----------------------- | ------- |
| Arif Assidiq            | 2312055 |
| Aprian Maulana Suryawan | 2304298 |
| M. Rislan Tristansyah   | 2307874 |

---

## 🎯 **Project Overview**

Proyek ini bertujuan untuk **mengembangkan model prediktif** yang mampu memperkirakan harga rumah (`SalePrice`) berdasarkan berbagai fitur seperti luas tanah, jumlah kamar, kualitas bangunan, dan lokasi.

Dataset yang digunakan adalah **House Prices: Advanced Regression Techniques** (Kaggle).
Data terdiri dari:

* **train.csv** → digunakan untuk melatih model
* **test.csv** → digunakan untuk menguji model

Pendekatan utama melibatkan **eksplorasi data (EDA)**, **pra-pemrosesan**, dan **pemodelan regresi machine learning** untuk menghasilkan model prediksi dengan akurasi tinggi.

---

## ⚙️ **Workflow & Methodology**

### 1. **Data Understanding**

Dataset berisi 81 fitur dan 1 kolom target (`SalePrice`) dengan 1460 baris data latih dan 1459 baris data uji.
Langkah awal meliputi:

* Pemeriksaan struktur (`info()`, `describe()`)
* Identifikasi missing values
* Analisis distribusi dan korelasi antar fitur

---

### 2. **Data Preprocessing**

Beberapa langkah utama:

* 🔹 **Penghapusan kolom tidak relevan:** `Alley`, `PoolQC`, `Fence`, `MiscFeature`, dll.
* 🔹 **Penanganan missing values:**

  * Numerik → diisi dengan *mean*
  * Kategorikal → diisi dengan *mode*
* 🔹 **Normalisasi:** menggunakan *Min-Max Scaling*
* 🔹 **Encoding:**

  * *Label Encoding* → fitur ordinal
  * *One-Hot Encoding* → fitur nominal

Hasil akhirnya berupa dataset numerik yang siap digunakan oleh model machine learning.

---

### 3. **Exploratory Data Analysis (EDA)**

EDA dilakukan untuk memahami hubungan antar fitur, termasuk:

* Analisis distribusi `SalePrice`, `GrLivArea`, `GarageCars`, `YearBuilt`, dll.
* Scatter plot dan box plot untuk melihat korelasi terhadap `SalePrice`.

Temuan utama:

* Fitur dengan korelasi tinggi terhadap harga rumah:
  `GrLivArea`, `OverallQual`, `TotalBsmtSF`, `GarageCars`, `YearBuilt`
* Harga rumah cenderung meningkat seiring kualitas dan ukuran bangunan.

---

### 4. **Modeling**

Beberapa model diuji untuk menentukan performa terbaik:

| Model              | RMSE       | R²         |
| ------------------ | ---------- | ---------- |
| CatBoost Regressor | **0.0366** | **0.9093** |
| Gradient Boosting  | 0.0393     | 0.8955     |
| LightGBM           | 0.0395     | 0.8944     |
| Random Forest      | 0.0404     | 0.8894     |
| XGBoost            | 0.0412     | 0.8854     |
| Linear Regression  | 0.0461     | 0.8564     |
| Elastic Net        | 0.1217     | -0.0009    |

Model terbaik: 🥇 **CatBoost Regressor**

---

### 5. **Hyperparameter Tuning**

Dilakukan dengan `RandomizedSearchCV` untuk mencari kombinasi terbaik:

* `iterations`: [500, 1000]
* `learning_rate`: [0.01, 0.1]
* `depth`: [4, 6, 8]

Setelah tuning, model mencapai performa luar biasa dengan:

* **RMSE = 0.0092**
* **R² = 0.9930**

Namun nilai ini diperoleh dari data latih, sehingga kemungkinan overfitting perlu diwaspadai.

---

### 6. **Evaluation**

* **Model sangat akurat** dalam memprediksi harga rumah bernilai rendah–menengah.
* **Kurang akurat** pada properti dengan harga ekstrem (outlier).
* Model menunjukkan distribusi hasil yang *positively skewed* seperti data aslinya.

---

## 📈 **Key Insights**

* Kualitas dan ukuran rumah merupakan faktor paling berpengaruh terhadap harga.
* Model berbasis **ensemble boosting** (CatBoost, LightGBM, XGBoost) unggul dibanding model klasik.
* **Normalisasi dan encoding yang tepat** sangat berpengaruh terhadap performa model.

---

## 💡 **Future Improvements**

* Gunakan **transformasi logaritma** pada `SalePrice` untuk mengurangi skewness.
* Terapkan **KNN Imputer** atau metode imputasi berbasis model.
* Tambahkan fitur baru seperti `TotalSF` atau `OverallGrade`.
* Lakukan **cross-validation** dan **GridSearch** untuk meningkatkan generalisasi.
* Gunakan interpretabilitas model (SHAP/LIME).
* Buat **dashboard interaktif** dengan Streamlit atau Plotly untuk visualisasi hasil.

---

## 🧰 **Tech Stack**

| Category         | Tools & Libraries                         |
| ---------------- | ----------------------------------------- |
| Language         | Python                                    |
| Data Processing  | Pandas, NumPy                             |
| Visualization    | Matplotlib, Seaborn                       |
| Machine Learning | Scikit-learn, CatBoost, XGBoost, LightGBM |
| Optimization     | RandomizedSearchCV                        |
| Environment      | Jupyter Notebook / Google Colab           |

---

## 📂 **Repository Structure**

```
📁 House-Price-Prediction
├── Project_UAS_Kel_6_4A_Prasiskom2.ipynb   # Main Notebook
├── train.csv                               # Training Data
├── test.csv                                # Test Data
├── README.md                               # Project Documentation
└── laporan_akhir_prasiskom2_kelompok6.pdf  # Final Report
```

---

## 🏁 **Conclusion**

Model CatBoost yang dikembangkan oleh Kelompok 6 berhasil memberikan prediksi harga rumah dengan tingkat akurasi yang sangat tinggi. Melalui tahapan EDA, preprocessing, dan tuning yang sistematis, proyek ini berhasil menunjukkan **penerapan nyata machine learning dalam sektor properti**.

> “Good data preparation leads to great predictions.”

---
