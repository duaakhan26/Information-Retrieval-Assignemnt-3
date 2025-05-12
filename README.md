---

## Yelp Review Star Prediction — Assignment 3

### Course Project: CS Assignment 3

**Author:** *Duaa Khan*
**Dataset:** Yelp Academic Dataset
**Models Used:** Multilayer Perceptron (MLP), BERT
**Evaluation Metric:** Accuracy, F1-score, Confusion Matrix

---

### Project Description

The objective of this project is to evaluate two different machine learning models — **MLP** and **BERT** — on the task of **review star rating prediction** using the Yelp Academic Dataset. This assignment is based on the methodologies surveyed in the provided research paper.

The core task is to predict the **star rating (1 to 5)** of a review based on:

* Review **text**
* User and business **metadata** (e.g., review count, average rating, etc.)

Due to size constraints in Colab, I sampled a subset of the dataset and processed it efficiently using TF-IDF and tokenization techniques.

---

### Models

| Model                           | Description                                                                                       |
| ------------------------------- | ------------------------------------------------------------------------------------------------- |
| **Multilayer Perceptron (MLP)** | Uses TF-IDF + business/user metadata as input to a simple feedforward neural network.             |
| **BERT (base)**                 | Pretrained transformer model fine-tuned on review text for multiclass classification (5 classes). |

---

### Dataset Files Used

* `yelp_academic_dataset_review.json`
* `yelp_academic_dataset_user.json`
* `yelp_academic_dataset_business.json`

Only the first chunk of each large dataset was used, and a subset of 5,000 records was sampled for processing.

---

### Results

#### **MLP (TF-IDF + Metadata)**

| Metric   | Value                                                                               |
| -------- | ----------------------------------------------------------------------------------- |
| Accuracy | **53%**                                                                             |
| Macro F1 | 0.39                                                                                |
| Notes    | Performs better on 4/5-star reviews, struggles with 2–3 stars due to class overlap. |

Confusion Matrix:

```
Predicted →
True ↓     1   2   3   4   5
          16   1   3  21   5
           3   3   1  23  19
           3   3  16  56  27
           4   5  13 122  67
           3   2   6  49 195
```

#### **BERT (Fine-tuned on review text)**

| Metric   | Value                                                                                  |
| -------- | -------------------------------------------------------------------------------------- |
| Accuracy | **63%**                                                                                |
| Loss     | 0.905                                                                                  |
| Notes    | Much stronger semantic understanding, improved classification across all star classes. |

---

### How to Run

1. Upload the Yelp `.json` files to a folder in Google Drive.
2. Mount Drive in Colab and follow the notebook steps.
3. Train and evaluate both models using the provided code.
4. Optional: visualize confusion matrices and export results.

---

### ✅ Conclusion

* **BERT significantly outperforms MLP**, especially in understanding subtle differences between review sentiments.
* MLP is limited by bag-of-words features and performs poorly on mid-range star ratings.
* Future work could include trying hybrid models like DeepCoNN or C-DSSM, or incorporating review tips/check-ins.

---
