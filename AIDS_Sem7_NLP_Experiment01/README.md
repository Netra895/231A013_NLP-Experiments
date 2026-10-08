# CampusVoice
## NLP-Based Student Feedback Intelligence System

> **Every student voice deserves to be understood.**

---

## 1. Aim

The aim of **CampusVoice** is to develop an NLP-based Student Feedback Intelligence System that automatically analyzes unstructured student feedback and converts it into meaningful and structured insights.

The system uses **Natural Language Processing (NLP)** and **Machine Learning** to perform:

- Sentiment Analysis
- Academic Category Classification
- Negation Detection
- Confidence-based Prediction
- Feedback Exploration
- Dashboard Visualization
- Insight Generation

The primary objective is to reduce the effort required to manually analyze large amounts of student feedback.

---

## 2. Problem Statement

Educational institutions collect large amounts of student feedback in the form of natural-language comments. Since this feedback is mostly unstructured text, manually reading and analyzing every response is time-consuming.

It is difficult to quickly determine:

- Whether students are satisfied or dissatisfied
- Which academic areas receive negative feedback
- Which areas require attention
- What patterns exist in student feedback
- How confidently a particular feedback statement has been classified

Therefore, **CampusVoice** applies NLP and Machine Learning techniques to automatically process student feedback and generate structured insights.

---

## 3. Brief Theory

### 3.1 Natural Language Processing

Natural Language Processing (NLP) is a branch of Artificial Intelligence that enables computers to process and analyze human language.

In CampusVoice, NLP is used to transform raw student feedback into numerical representations that can be processed by Machine Learning algorithms.

The overall NLP pipeline is:

text
Student Feedback -> Text Preprocessing -> Negation Handling -> TF-IDF Feature Extraction -> Machine Learning -> Sentiment + Category -> Confidence Score -> Insights

### 3.2 Text Preprocessing
Raw student feedback can contain variations in capitalization, spacing, punctuation, and wording.
The preprocessing stage cleans and normalizes the feedback before it is passed to the Machine Learning models.
This prepares the text for feature extraction and classification.

### 3.3 TF-IDF
TF-IDF (Term Frequency–Inverse Document Frequency) converts text into numerical features based on the importance of terms within the dataset.
CampusVoice uses two types of TF-IDF features:
- Word-level TF-IDF
- Character-level TF-IDF
Word TF-IDF
Word features capture meaningful words and phrases.

### 3.4 Sentiment Analysis

Sentiment Analysis determines the emotional polarity of a piece of text.

CampusVoice classifies feedback into three sentiment classes:
Positive
Neutral
Negative

Examples: "The teacher explains concepts very clearly."
→ Positive

### 3.5 Negation Handling

Negation is important in sentiment analysis because words such as not and never can change the meaning of a sentence.

For example: "The laboratory facilities are not good."
Although the word good is normally positive, the complete sentence expresses a negative opinion.
CampusVoice therefore includes negation detection to improve sentiment interpretation.

### 3.6 Logistic Regression

CampusVoice uses Logistic Regression as the primary Machine Learning algorithm.

Logistic Regression was selected because:
- It performs well with high-dimensional text features
- It is computationally efficient
- It works effectively with TF-IDF representations
- It is suitable for classification problems
- It provides probability-based prediction confidence
  
Logistic Regression is used for:
1. Sentiment Classification
2. Academic Category Classification

### 3.7 VADER
VADER (Valence Aware Dictionary and sEntiment Reasoner) is a lexicon and rule-based sentiment analysis tool.
CampusVoice uses VADER as an additional sentiment signal.


# 4. Implementation Explanation

### 4.1 Dataset
The system uses a dataset containing: Total Feedback Records: 726
The dataset contains natural-language student feedback that is processed using the NLP pipeline.

### 4.2 NLP Processing Pipeline

The complete processing pipeline is:
Raw Student Feedback
        ↓
Text Preprocessing
        ↓
Negation Detection
        ↓
Word TF-IDF + Character TF-IDF
        ↓
Logistic Regression
        ↓
Sentiment / Category Prediction
        ↓
Confidence Calculation
        ↓
Final Result

### 4.3 Sentiment Classification

The sentiment classification process begins with raw feedback.
The text is first preprocessed and converted into numerical features using Word and Character TF-IDF.
The features are then passed to the Logistic Regression model.
Raw Feedback
      ↓
Preprocessing
      ↓
Word TF-IDF + Character TF-IDF
      ↓
Logistic Regression
      ↓
Initial Sentiment

The system then enhances the prediction using:
VADER
+
Domain-specific Rules
+
Negation Detection

The final output contains:
- Sentiment
- Confidence
- Prediction method
- Negation detection result

### 4.4 Hybrid Sentiment Engine
The hybrid sentiment engine is one of the important parts of CampusVoice.

                    ┌─────────────────────┐
                    │   Logistic Regression│
                    └──────────┬──────────┘
                               │
                               ↓
Student Feedback → NLP Processing → Initial Prediction
                               │
              ┌────────────────┼────────────────┐
              ↓                ↓                ↓
            VADER        Domain Rules      Negation
              └────────────────┼────────────────┘
                               ↓
                    Final Sentiment
                               ↓
                         Confidence

The purpose of this approach is to avoid depending completely on a single sentiment technique.
The Machine Learning model learns patterns from the dataset, while VADER and domain-specific rules provide additional sentiment signals.

### 4.5 Category Classification
CampusVoice also determines the academic category related to the feedback.

The system supports six categories:
1. Teaching
2. Course Content
3. Examination
4. Lab Work
5. Library Facilities
6. Extracurricular Activities

### 4.6 Confidence-Based Prediction
The system provides confidence scores along with predictions.

The confidence score indicates how strongly the model supports a prediction.

This is useful because some feedback may be ambiguous or may relate to multiple categories.

Low-confidence predictions can therefore be considered for further review.

### 4.7 Backend Implementation
The backend is developed using FastAPI.

The backend is responsible for:
- Receiving feedback from the frontend
- Preprocessing the text
- Loading trained Machine Learning models
- Performing sentiment analysis
- Performing category classification
- Calculating confidence
- Returning prediction results through APIs

### 4.8 Frontend Implementation

The frontend is developed using React.
The application provides:

Dashboard
Displays:
- Total feedback
- Positive percentage
- Neutral percentage
- Negative percentage
- Category-level analysis


Analyze Feedback
Allows the user to enter feedback and obtain:
- Sentiment
- Category
- Confidence
- Negation information


Feedback Explorer
Allows users to search and explore individual feedback records.
Insights
Provides summarized information about:
- Most positive categories
- Most negative categories
- Most discussed categories
- Areas requiring attention

# 5. Technologies Used

-Python: NLP, Machine Learning and backend development
-Pandas: Dataset processing
-NumPy: Numerical operations
-Scikit-learn: Machine Learning and TF-IDF
-Logistic Regression: Sentiment and category classification
-VADER: Additional sentiment analysis
-NLTK: NLP utilities
-Joblib: Saving and loading trained models
-FastAPI: Backend API
-React: Frontend development
-Recharts: Data visualization
-JavaScript: Frontend functionality 

# 6. Results
The final CampusVoice system was evaluated using the available student feedback dataset.

Dataset Result: 
Metric: Total Feedback Records
Result: 726

Sentiment Classification Results:
Accuracy: 84.14%
F1 Score: ≈ 0.8435

Category Classification Results:
Accuracy: ≈ 66.44%

# 7. Conclusion
CampusVoice demonstrates how Natural Language Processing and Machine Learning can be used to transform unstructured student feedback into meaningful and structured information.

# 8. Future Scope
The system can be further enhanced with:
- Larger and more diverse datasets
- Multilingual sentiment analysis
- Aspect-Based Sentiment Analysis
- BERT and Transformer-based NLP models
- Semester-wise sentiment trends
- Automatic recurring-issue detection
- Institution-specific model fine-tuning
- Human-in-the-loop correction for low-confidence predictions
- Real-time feedback monitoring

# 9. References
1. Jurafsky, D., & Martin, J. H.
   Speech and Language Processing.
2. Manning, C. D., Raghavan, P., & Schütze, H.
   Introduction to Information Retrieval. Cambridge University Press.
3. Pedregosa, F., et al.
   "Scikit-learn: Machine Learning in Python."
   Journal of Machine Learning Research, 2011.
4. Hutto, C. J., & Gilbert, E.
   "VADER: A Parsimonious Rule-based Model for Sentiment Analysis of Social Media Text."
   Proceedings of the International AAAI Conference on Web and Social Media.
5. Bird, S., Klein, E., & Loper, E.
   Natural Language Processing with Python. O'Reilly Media.
6. FastAPI Documentation.
7. React Documentation.

# 10. Project Structure
CampusVoice/
│
├── backend/
│   ├── main.py
│   ├── requirements.txt
│   │
│   ├── nlp/
│   │   ├── preprocessing.py
│   │   ├── sentiment_engine.py
│   │   ├── prediction_engine.py
│   │   └── ...
│   │
│   ├── models/
│   │   ├── sentiment_model.joblib
│   │   ├── sentiment_word_tfidf.joblib
│   │   ├── sentiment_char_tfidf.joblib
│   │   ├── category_model.joblib
│   │   ├── category_word_tfidf.joblib
│   │   └── category_char_tfidf.joblib
│   │
│   └── ...
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── services/
│   │   ├── App.jsx
│   │   └── index.css
│   │
│   ├── package.json
│   └── ...
│
└── README.md
