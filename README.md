# Arabic Distress Detection Chatbot

This project implements an AI-driven chatbot that classifies Arabic text messages as either **Distressed** or **Non-Distressed**. The chatbot leverages **Arabic BERT** (from Hugging Face) for generating text embeddings and machine learning classifiers for predicting emotional states based on short Arabic messages.

The goal is to provide culturally sensitive mental health support by detecting potential distress signals in user messages. The chatbot can be used in real-time through a **Gradio interface**, making it accessible and easy to use.

---

## Table of Contents
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Dataset](#dataset)
- [Model](#model)
- [Evaluation](#evaluation)
- [Ethical Considerations](#ethical-considerations)
- [Example Predictions](#example-predictions)
- [License](#license)

---

## Features
- **Text Classification:** Categorizes Arabic text messages as "Distressed" or "Non-Distressed."
- **Arabic BERT:** Uses the pre-trained `asafaya/bert-base-arabic` model for high-quality embeddings.
- **Real-Time Predictions:** Provides real-time predictions through an interactive Gradio interface.
- **Preprocessing:** Normalizes Arabic text (handles diacritics, different forms of letters, and punctuation removal) for consistency.
- **Metrics and Evaluation:** Includes classification reports and confusion matrix visualizations.

---

## Installation
To run this project locally, follow these steps:

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/arabic-distress-chatbot.git
   cd arabic-distress-chatbot
   ```

2. **Install dependencies:**
   Ensure you have Python 3.7 or higher installed. Install the required packages:
   ```bash
   pip install -r requirements.txt
   ```

3. **Download the pre-trained BERT model:**
   The script will automatically load the `asafaya/bert-base-arabic` model from Hugging Face.

4. **Run the chatbot:**
   Launch the Gradio interface:
   ```bash
   python chatbot.py
   ```

5. **Open the interface:**
   Once the script runs, it will provide a link to access the chatbot in your browser.

---

## Usage
1. After running the project, you'll see a Gradio interface.
2. Type an Arabic message into the text box.
3. The chatbot will classify the message as either **Distressed** or **Non-Distressed.**

---

## Dataset
The dataset consists of manually labeled Arabic text messages:
- **Distressed:** Messages indicating emotional distress or negative emotions (e.g., "أنا مخنوق ومش قادر أتنفس").
- **Non-Distressed:** Neutral or positive messages (e.g., "أنا كويس النهارده").

Example messages:
- **Distressed:** 
  - "حاسس بضيق شديد ومش لاقي أي أمل"
  - "مش قادر أنام من كتر التفكير"
- **Non-Distressed:**
  - "كل حاجة تمام والحمد لله"
  - "النهارده قعدت مع صحابي واتونسنا"

---

## Model
1. **Text Embedding:**
   - Arabic text is preprocessed and converted into embeddings using the `asafaya/bert-base-arabic` model.
2. **Classifier:**
   - Three classifiers were tested:
     - Logistic Regression (best performance, selected as the final model).
     - Support Vector Machine (SVM).
     - Random Forest.
3. **Final Model:**
   - Logistic Regression with hyperparameter tuning via GridSearchCV was chosen for its balance of accuracy and simplicity.

---

## Evaluation
The model was evaluated using an 80/20 train-test split. The following metrics were calculated:
- **Accuracy**
- **F1-Score**
- **Confusion Matrix**

### Example Results:
- **Accuracy:** 95%
- **F1-Score:** 94%
- **Confusion Matrix:**

|                | Predicted Distressed | Predicted Non-Distressed |
|----------------|-----------------------|--------------------------|
| **Actual Distressed**   | 10                    | 1                        |
| **Actual Non-Distressed** | 1                     | 8                        |

---

## Ethical Considerations
This project aims to assist with mental health support, but it is not a replacement for professional help. Some ethical considerations include:
- **False Negatives:** Distressed messages misclassified as non-distressed could result in missed opportunities for intervention.
- **False Positives:** Non-distressed messages misclassified as distressed may cause unnecessary concern.
- **Bias in Dataset:** The small dataset may not cover the full diversity of Arabic dialects or expressions, potentially affecting model performance.

**Recommendation:** Always involve a human moderator to review flagged messages, especially in sensitive mental health applications.

---

## Example Predictions
Here are some sample predictions from the chatbot:

| Input Text                                      | Predicted Output      |
|------------------------------------------------|-----------------------|
| "حاسس بضيق ومفيش فايدة"                         | Distressed            |
| "أنا سعيد جدًا النهارده"                        | Non-Distressed        |
| "مش عارف أنام بسبب القلق"                       | Distressed            |
| "النهارده الجو جميل ومرتاح"                    | Non-Distressed        |

---

## License
This project is licensed under the MIT License. See the LICENSE file for details.


