# 📊 **Meta Kaggle Dataset Project: From Relational Modeling to Pattern Mining**

## 📝 **Overview**
Meta Kaggle Insights is a data exploration project using the **Meta Kaggle dataset** to analyze the Kaggle community, including users, competitions, datasets, and notebooks. The project leverages **relational (PostgreSQL)** and **document-oriented (MongoDB)** databases to model and analyze the data, explore functional dependencies, and perform itemset mining and association rule analysis.

This project is divided into three phases:
⚙️ Phase 1: Relational Database Construction
  Used PostgreSQL to construct a normalized schema.
  
  Loaded cleaned Kaggle data covering users, competitions, datasets, tags, submissions, teams, etc.
  
  Maintained referential integrity using primary and foreign keys.
  
  Created ER diagrams and relational schema models.
  
  Cleaned data using scripts (clean_files.py, analyze_data.py).

🛠 Tools: Python, PostgreSQL, SQL, pandas

Phase 2: Document Database with MongoDB
  Modeled the same dataset using MongoDB, embedding nested entities like:
  
  Users → Organizations, Followers, Achievements
  
  Teams → Submissions
  
  Competitions & Datasets → Tags
  
  Compared performance between relational and document models on complex analytical queries.
  
  Added indexing to speed up relational queries by over 95% in most cases.

📌 Key Findings:

  PostgreSQL is better for data integrity and complex joins.
  
  MongoDB offers flexibility but struggles with constraints and query speed.

🔧 Tools: MongoDB, PyMongo, SQL indexing, query tuning

📈 Phase 3: Pattern Mining & Association Rules
  Applied Apriori algorithm to perform itemset mining:
  
  🏁 Competition Tags: Found that beginner competitions are highly associated with "tabular-data" (confidence = 1.0).
  
  📦 Dataset Tags: "business" often co-occurs with "finance" (lift = 18.56).
  
  🧑‍💼 User-Organization: IIT KHARAGPUR ↔ SPARK4AI (perfect lift = 39.73).
  
  Mined both frequent itemsets and association rules.
  
  Mapped high-engagement topics and user contribution patterns.

🧠 Tools: Python, pandas, set operations, custom Apriori

🧹 Data Cleaning Highlights
    Dropped invalid references, corrected data types (e.g., float → int), and filled missing values when sensible.

Ensured:

  ✅ Validity (primary/foreign keys)
  
  ✅ Accuracy (type casting, length checks)
  
  ✅ Completeness (e.g., filling DisplayName with UserName)

Final cleaned dataset had 126M+ records (only 1% data loss from raw input).

⚡ Performance Insights
  Indexed SQL queries saw:
  
  98% speedup on tag-medal aggregation queries
  
  96% speedup on follower-achievement lookups
  
  Document model loading took ~215 mins vs. ~90 mins for relational load
  

---

## ✨ **Key Features**
  - **Relational Database (PostgreSQL)**: Efficient handling of structured data with complex joins and constraints.
  - **Document Database (MongoDB)**: Flexible schema for hierarchical data modeling.
  - **Data Cleaning**: Comprehensive filtering and validation to ensure data accuracy, validity, and completeness.
  - **Itemset Mining**: Frequent pattern discovery and association rule generation using the Apriori algorithm.
  - **Performance Benchmarking**: Query performance evaluation between relational and document databases.

---

[//]: # (## 📂 **Project Structure**)

[//]: # (The project is structured as follows:)

[//]: # ( ├── meta_kaggle_insights)

[//]: # ( │   ├── Phase1)

[//]: # ( │   │   ├── analyze_data.py)

[//]: # ( │   │   ├── clean_files.py)

[//]: # ( │   │   ├── app.py )

[//]: # ( │   │   ├── create_schema.sql)

[//]: # ( │   │   ├── test1.py)

[//]: # ( │   │   ├── test2.py)

[//]: # ( │   │   ├── funcs)

[//]: # ( │   │   │   ├── db_methods.py)

[//]: # ( │   │   │   ├── db_funcs.py)

[//]: # ( │   │   │   ├── globals.py)

[//]: # ( │   │   │   └──queries.py)

[//]: # ( │   │   ├── requirements.txt)

[//]: # ( │   ├── Phase2)

[//]: # ( │   │   ├── clean_files.py)

[//]: # ( │   │   ├── execute_drop_index.py )

[//]: # ( │   │   ├── execute_index.sql)

[//]: # ( │   │   ├── execute_queries.py)

[//]: # ( │   │   ├── generate_fds.py)

[//]: # ( │   │   ├── globals.py)

[//]: # ( │   │   ├── mongo_app.py)

[//]: # ( │   │   ├── mongo_rem_keys.py)

[//]: # ( │   │   ├── mongo)

[//]: # ( │   │   │   ├── __init__.py)

[//]: # ( │   │   │   └── db_methods.py)

[//]: # ( │   │   ├── sql)

[//]: # ( │   │   │   ├── db_methods.py)

[//]: # ( │   │   │   ├── db_funcs.py)

[//]: # ( │   │   │   ├── globals.py)

[//]: # ( │   │   │   └── queries.py)

[//]: # ( │   │   ├── all_tables_fds.txt)

[//]: # ( │   │   ├── doc_model.txt)

[//]: # ( │   │   ├── requirements.txt)

[//]: # ( │   ├── Phase3)

[//]: # ( │   │   ├── analyze_data.py)

[//]: # ( │   │   ├── filter_data.py)

[//]: # ( │   │   ├── app.py )

[//]: # ( │   │   ├── create_schema.sql)

[//]: # ( │   │   ├── insert_data_clean.py)

[//]: # ( │   │   ├── itemset_mining.py)

[//]: # ( │   │   ├── sql)

[//]: # ( │   │   │   ├── db_methods.py)

[//]: # ( │   │   │   ├── db_funcs.py)

[//]: # ( │   │   │   ├── globals.py)

[//]: # ( │   │   │   └── queries.py)

[//]: # ( │   │   ├── requirements.txt)

[//]: # ( │   ├── PPT)

[//]: # ( │   │   ├── Meta Kaggle Insights.pptx)

[//]: # ( │   ├── README.md)

[//]: # ( │   └── file_info.txt)

[//]: # ( └── README.md)

[//]: # ()
[//]: # ( )

## 📊 **Dataset**
The [Meta Kaggle dataset](https://www.kaggle.com/datasets/kaggle/meta-kaggle) provides metadata on the Kaggle platform, capturing:
    - **Users**: User demographics, rankings, and activity levels.
    - **Competitions**: Details about hosted competitions, deadlines, rewards, and evaluations.
    - **Datasets**: Usage statistics for uploaded datasets.
    - **Tags**: Categorization of competitions and datasets.
    - **Submissions**: User submissions to competitions and their scores.

**Subset Stats**:
    - 127 million+ records
    - Comprehensive coverage of Kaggle entities like users, competitions, and datasets.

---

## 🛠️ **Getting Started**

### **Prerequisites**
- **🐍 Python 3.8 or above**
- **PostgreSQL**
- **MongoDB**

### **Setup**
1. Clone the repository:
  ```bash
  git clone https://github.com/GokulNaveen2708/meta_kaggle_insights.git
  cd meta_kaggle_insights
  ```
2. Install the dependencies:
  ```bash
  pip install -r requirements.txt
  ```

4. Load document model:
```bash
python monog_app.py
```

5. Excute Pattern mining:
```bash
python itemset_mining.py
```
