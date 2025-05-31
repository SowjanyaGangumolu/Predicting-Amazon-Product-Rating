# Predicting-Amazon-Product-Rating

# 🛍️ Predicting Amazon Product Ratings

## 📌 Introduction

This project focuses on analyzing Amazon product reviews using machine learning techniques. The goal is to predict the **rating score (1 to 5)** given by users, based on the **review text** and other features. It leverages **PySpark MLlib** for scalable processing and integrates with **AWS services** such as **S3** and **Athena**.

---

## 📂 Data Source

- **Source**: [Kaggle - Amazon Product Reviews](https://www.kaggle.com/datasets/arhamrumi/amazon-product-reviews/data)  
- **Size**: 568,454 records | 10 attributes | ~300 MB  
- **Rich Textual Content** and a **diverse range of products** make this dataset ideal for sentiment and score prediction.

### 📑 Attributes

- `Id`: Unique identifier for each review  
- `ProductId`: Identifier of the reviewed product  
- `UserId`: Identifier of the user  
- `ProfileName`: Name of the user profile  
- `HelpfulnessNumerator`: Count of users who found the review helpful  
- `HelpfulnessDenominator`: Total number of helpfulness votes  
- `Score`: User rating (1 to 5)  
- `Time`: Timestamp  
- `Summary`: Short summary/title of the review  
- `Text`: Full review content  

---

## 🔧 Data Preprocessing

1. **Read Data**: Loaded from an Amazon S3 bucket into a Spark DataFrame  
2. **Clean Data**:
   - Removed non-numeric values from numeric fields  
   - Dropped rows with missing data  
3. **Feature Engineering**:
   - Normalized text (lowercase, removed special characters)  
   - Added features like `HelpfulnessRatio` and `TextLength`

---

## ☁️ AWS Integration

- **S3**: Cleaned data saved back to Amazon S3  
- **Athena**: External table created for querying using SQL

---

## 🤖 Machine Learning Pipeline (PySpark MLlib)

The model predicts review **Score** using a pipeline of transformations:

### 🔍 Pipeline Stages

- `Tokenizer`: Splits text into individual words  
- `StopWordsRemover`: Eliminates common stop words  
- `CountVectorizer`: Converts text to term frequency vectors  
- `IDF`: Transforms term frequencies into TF-IDF representation  
- `LogisticRegression`: Classifies the review into one of 5 categories

### 📈 Model Performance

- **Training Accuracy**: 99.63%  
- **Test Accuracy**: 71.01%  
- Precision, recall, and F1-score indicate strong but imperfect classification — particularly for reviews with score 5

---

## ⚠️ Challenges

1. **High Dimensionality**  
   - Used TF-IDF to reduce irrelevant features
2. **Computation Time**  
   - Leveraged PySpark for distributed, scalable processing

---

## ⚙️ Benefits of Distributed Computing

- 🚀 **Scalability** for large datasets  
- ⚡ **Speed** via parallel processing  
- 🔄 **Flexibility** for complex ML pipelines

---

## 📊 Visualizations

- **Confusion Matrix**: High accuracy for class 5, less accurate for classes 1–2  
- **Performance Metrics**: Visual breakdown of model effectiveness

*Architecture diagrams and plots included in the full project report.*

---

## ✅ Conclusion

- Successfully processed and transformed Amazon reviews using **PySpark**
- Stored clean data in **S3**, queried via **Athena**
- Built a **logistic regression** model to predict ratings from text
- Identified class imbalance issues (1–2 ratings underperform)
- Valuable for improving customer insight and product strategy at scale

---

## 🔮 Future Work

- Try **Gradient Boosting**, **Neural Networks**, and **Deep Learning**  
- Add features: user history, product metadata, sentiment scores  
- Address class imbalance via **SMOTE** or re-sampling strategies

---

📄 **Read the full [Project Report](ProjectReport.pdf)**  
🧠 **Author**: *Your Name Here* | *Machine Learning & Cloud Enthusiast*

