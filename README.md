# Flatiron Data Science Project 3: SMS Spam Detection Model

A machine learning project to detect and filter spam text messages while minimizing false positives.

## Table of Contents
- [Business Problem](#business-problem)
- [Dataset](#dataset)
- [Data Preprocessing](#data-preprocessing)
- [Models Explored](#models-explored)
- [Results](#results)
- [Modern Data Testing](#modern-data-testing)
- [Business Recommendations](#business-recommendations)
- [Future Improvements](#future-improvements)

## Business Problem
In our day-to-day lives, we are plagued by spam text messages that are not only annoying but also pose security risks to users. This project aims to build a spam detection model that will identify and block potentially harmful messages while minimizing false positives.

## Dataset
- 5,574 text messages from 2015
- Class distribution:
  - 86% non-spam (ham)
  - 14% spam
- Contains message content and classification labels

## Data Preprocessing
The text data underwent several preprocessing steps:
1. Converting all text to lowercase
2. Removing punctuation
3. Removing stopwords (common words like "and", "the", "a", etc.)
4. Lemmatization (reducing words to their root form; e.g., "running" → "run")
5. TF-IDF Vectorization to generate scores for each word based on frequency and importance

## Models Explored

### Baseline Model
- Simple Logistic Regression without data modifications
- Accuracy: 95.7%

### Logistic Regression (Improved)
Enhancements over baseline:
- SMOTE oversampling to address class imbalance
- Optimized C-value (14)
- Tuned TF-IDF Vectorizer parameters (min_df = 1)

### Multinomial Naive Bayes
Key improvements:
- Threshold adjustment (optimal value: 0.4)
- Enhanced with n-grams
- Custom regex features for detecting phone numbers and URLs
- Best overall performance: 99.0% accuracy, 93.3% recall, minimal false positives

### Random Forest
- Hyperparameter tuning
- Performance was not as strong as Naive Bayes
- Model seemed either too simple or overfitted to training data

## Results
The Multinomial Naive Bayes model with custom regex features achieved the best performance:
- Accuracy: 99.0%
- Recall: 93.3%
- False Positives: Only 1

This provides an excellent balance between catching spam messages and avoiding false flags on legitimate messages.

## Modern Data Testing
- Tested the model on a new dataset of 1,000 more recent text messages
- Accuracy dropped to 88%
- This demonstrates the need for continuous model updates as spam patterns evolve

## Business Recommendations
1. Implement the tuned Multinomial Naive Bayes model for spam detection
2. Establish a continuous learning pipeline to update the model with newer spam examples
3. Regularly evaluate and retrain the model to maintain high detection rates

## Future Improvements
- Gather and incorporate more modern spam data into the training set
- Expand to other messaging services (email, instant messaging)
- Add regex for pricing cues (e.g., "£\d+", "p/min") and short codes (e.g., "TXT to \d+")
- Explore deep learning approaches for more robust feature extraction

