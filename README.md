# 🎬 IMDb Movie Data Analysis

## 📌 Project Name

**IMDb Movie Success Analysis**

## 🧠 Project Overview

This project explores an IMDb movie dataset to uncover insights about movie performance, genres, directors, ratings, and profitability. The goal is to practice **data analysis and data science workflows** using Python while answering real-world questions like:

* Which genres perform best for debut directors?
* How are ratings and profits distributed?
* What factors influence a movie’s success?

This repository is beginner-friendly and suitable for showcasing **job-ready data analysis skills** on GitHub.

---

## 🛠️ Tools & Technologies

* Python 🐍
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Jupyter Notebook

---

## 📂 Dataset

* **movies.csv** – Contains IMDb movie data such as:

  * Movie title
  * Genre
  * Director name
  * IMDb rating
  * Profit / Gross / Budget

---

## 📁 Repository Structure

```
IMDb-Movie-Success-Analysis/
│
├── movies.csv
├── imdb_analysis.ipynb
├── README.md
```

---

## 📊 Analysis Performed

* Data cleaning & preprocessing
* Handling missing values
* Genre-wise analysis
* Director-wise analysis
* Rating & profit distribution
* Visualization using charts

---

## 📓 Notebook: `imdb_analysis.ipynb`

Below is the structure and content used in the notebook.

### 1️⃣ Import Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

---

### 2️⃣ Load Dataset

```python
df = pd.read_csv('movies.csv')
df.head()
```

---

### 3️⃣ Basic Exploration

```python
df.info()
df.describe()
```

---

### 4️⃣ Data Cleaning

```python
# Remove duplicates
df = df.drop_duplicates()

# Handle missing values
df = df.dropna(subset=['genre', 'director_name', 'imdb_score'])
```

---

### 5️⃣ Genre Analysis

```python
genre_avg_rating = (
    df.assign(genre=df['genre'].str.split('|'))
      .explode('genre')
      .groupby('genre')['imdb_score']
      .mean()
      .sort_values(ascending=False)
)

genre_avg_rating.head()
```

---

### 6️⃣ Best Genre for Debut Directors

```python
first_movies = df.sort_values('title_year').groupby('director_name').first()

best_genre = (
    first_movies.assign(genre=first_movies['genre'].str.split('|'))
               .explode('genre')
               .groupby('genre')['imdb_score']
               .mean()
               .sort_values(ascending=False)
)

best_genre.head()
```

---

### 7️⃣ Visualization Examples

#### IMDb Rating Distribution

```python
plt.hist(df['imdb_score'], bins=10, edgecolor='black')
plt.xlabel('IMDb Rating')
plt.ylabel('Number of Movies')
plt.title('Distribution of IMDb Ratings')
plt.show()
```

#### Genre-wise Average Rating

```python
genre_avg_rating.plot(kind='bar', figsize=(10,5))
plt.ylabel('Average IMDb Rating')
plt.title('Average Rating by Genre')
plt.show()
```

---

## ✅ Key Insights

* Certain genres consistently receive higher IMDb ratings
* Drama and Biography often perform well for debut directors
* Ratings tend to cluster between 6–8

---

## 🚀 How to Run This Project

1. Clone the repository

```bash
git clone https://github.com/your-username/IMDb-Movie-Success-Analysis.git
```

2. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn
```

3. Open Jupyter Notebook

```bash
jupyter notebook imdb_analysis.ipynb
```

---

## 👤 Author

**Adarsh Tripathi**
Aspiring Data Scientist | Python | SQL | Data Analysis | Power BI
