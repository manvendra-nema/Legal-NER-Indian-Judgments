# Task 1: Legal Named Entities Recognition from Indian Court Judgment Text

## Description
This task focuses on recognizing and labeling key named entities in Indian court judgment texts. Named entities refer to key subjects (given as labels in the dataset) of a piece of text.

### Example
- **Text:** True, our Constitution has no 'due process' clause or the VIII Amendment; but, in this branch of law, after R.C. Cooper v. Union of India, (1970) 1 SCC 248 and Maneka Gandhi v. Union of India, (1978) 1 SCC 248, the consequence is the same.
- **Named Entities:**
  1. **Entity:** Constitution - **Label:** STATUTE
  2. **Entity:** R.C. Cooper v. Union of India, (1970) 1 SCC 248 - **Label:** PRECEDENT
  3. **Entity:** Maneka Gandhi v. Union of India, (1978) 1 SCC 248 - **Label:** PRECEDENT

## Dataset
- **Source:** [OpenNyai legal-NER dataset](https://opennayai-dataset-link)
- **Files:** Two JSON files (train and test data), each containing a list of dictionaries representing judgment cases. The `data` key contains the judgment text, and the `annotations` key contains the named entities, their spans, and corresponding labels.

## Evaluation Metrics
- Macro-F1
- Accuracy

---

## Part 1: Data Preparation 

### A) Dataset Preparation 
1. Split the training data into training and validation sets with an 85:15 ratio (randomly stratified).
2. Implement BIO (Beginning-Intermediate-Outside) chunking for the dataset. Tokenize based on space and assign BIO labels (B_label, I_label, O).
3. Save the processed data in the following format:
    ```json
    {
      "id1": {
        "text": "(See Principles of Statutory Interpretation by Justice G.P. Singh, 9th Edn., 2004 at p. 438.).",
        "labels": ["O", "O", "O", "O", "O", "O", "O", "B_JUDGE", "I_JUDGE", "O", "O", "O", "O", "O", "O", "O"]
      }
      // More cases
    }
    ```
4. Save processed data in JSON files for train, validation, and test splits.

---

## Part 2: Baseline Models Implementation 

### Models
1. **Model 1:** Vanilla RNN  
2. **Model 2:** LSTM         
3. **Model 3:** GRU          

### Pre-trained Word Embeddings
- word2vec
- GloVe
- fasttext

### Tasks
1. Train 9 models (3 models x 3 embeddings).
2. Generate the following plots for each model:
    - Training and Validation Loss vs. Epochs
    - Training and Validation Macro-F1 Score vs. Epochs
3. Load trained models, extract named entities from the test data, and report overall accuracy and macro-F1 scores.

---

## Part 3: BiLSTM-CRF Model Implementation 

### Model 4: BiLSTM-CRF 
- Implement the BiLSTM-CRF model as described in the reference paper.
- Use three different pre-trained word embeddings (word2vec, GloVe, fasttext) and train a total of three models.

### Tasks
1. Train and save the models.
2. Generate the following plots for each model:
    - Training and Validation Loss vs. Epochs
    - Training and Validation Macro-F1 Score vs. Epochs
3. Load trained models, extract named entities from the test data, and report overall accuracy and macro-F1 scores.
4. Calculate label-wise F1 scores for the best-performing model and plot a bar graph or pie chart.

---

