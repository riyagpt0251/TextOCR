# 🐋 Named Entity Recognition (NER) for OCR Text using SpaCy

![Named Entity Recognition](https://media.giphy.com/media/xTiIzJSKB4l7xTouE8/giphy.gif)

## 📌 Overview
This project leverages **SpaCy's Natural Language Processing (NLP)** capabilities to extract named entities from **OCR-processed text**. The extracted entities are saved as a CSV file for further analysis.

---
## 📊 Workflow
1. **Install & Import SpaCy** 📦
2. **Load Pretrained NLP Model** 🧠
3. **Extract Named Entities (NER)** 🏷️
4. **Apply NER on OCR Text Data** 🔎
5. **Save Extracted Entities to CSV** 📁

---
## 🚀 Installation
```bash
# Install SpaCy
pip install spacy

# Download the English NLP model
python -m spacy download en_core_web_sm
```

---
## 📜 Code Explanation
### 🔹 Step 1: Import Libraries
```python
import spacy
import pandas as pd
from google.colab import files  # For downloading CSV in Colab
```

### 🔹 Step 2: Load the SpaCy NLP Model
```python
# Load English NLP model
nlp = spacy.load("en_core_web_sm")
```

### 🔹 Step 3: Define Named Entity Recognition (NER) Function
```python
def extract_entities(text):
    doc = nlp(text)
    entities = [(ent.text, ent.label_) for ent in doc.ents]
    return entities
```

### 🔹 Step 4: Apply NER on OCR Text
```python
# Assuming df_results is a DataFrame with a column named 'ocr_text'
df_results["entities"] = df_results["ocr_text"].apply(extract_entities)
```

### 🔹 Step 5: Save Results to CSV
```python
# Save extracted entities to a CSV file
df_results.to_csv("whale_test_ocr_entities.csv", index=False)
print("✅ Named Entities extracted and saved!")

# Download the file (For Google Colab users)
files.download("whale_test_ocr_entities.csv")
```

---
## 📈 Example Output
| OCR Text | Extracted Entities |
|----------|-------------------|
| "Elon Musk founded SpaceX in 2002." | [("Elon Musk", "PERSON"), ("SpaceX", "ORG"), ("2002", "DATE")] |
| "The Eiffel Tower is in Paris, France." | [("Eiffel Tower", "FAC"), ("Paris", "GPE"), ("France", "GPE")] |

---
## 📌 Named Entity Categories
| Label | Description |
|-------|------------|
| PERSON | People, fictional characters |
| ORG | Organizations, companies |
| GPE | Countries, cities, states |
| DATE | Dates or periods |
| LOC | Non-GPE locations |

For a complete list, check [SpaCy Named Entities](https://spacy.io/api/annotation#named-entities).

---
## 🏆 Benefits
✔️ **Automated Entity Extraction** 🔍  
✔️ **Works with Any OCR Text** 📃  
✔️ **Fast and Scalable** 🚀  
✔️ **Pretrained NLP Model** 🤖  
✔️ **Exports to CSV for Analysis** 📊  

---
## 🤝 Contribution
Feel free to contribute! 🛠️
```bash
# Fork the repo
git clone https://github.com/yourusername/spacy-ner-ocr.git

# Create a branch
git checkout -b feature-branch

# Commit changes
git commit -m "Your awesome feature!"

# Push changes
git push origin feature-branch
```

---
## 📄 License
[MIT License](LICENSE)

---
## ✨ Credits
- **SpaCy** for NLP processing
- **Google Colab** for testing
- **Pandas** for data handling

---
### ⭐ Star the repository if you find it useful!
🔗 [GitHub Repository](https://github.com/yourusername/spacy-ner-ocr)
