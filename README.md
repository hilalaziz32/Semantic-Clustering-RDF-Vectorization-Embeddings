# README

## Project: Religion-Based Text Classification with RDF Ontology

### Overview

This project processes a dataset of religious subreddit posts to classify text into categories (`Islam` or `non_muslim`) using an RDF ontology. The ontology captures hierarchical relationships between words and religious categories, enabling semantic-based text classification.

---

### Key Features

1. **Data Preprocessing:**

   - Removes unnecessary subreddits and irrelevant posts.
   - Cleans the text by removing URLs, mentions, punctuation, numbers, and stopwords.
   - Lemmatizes text for better consistency.

2. **Ontology Creation:**

   - An RDF ontology is created using `rdflib`.
   - Categories (`Islam` and `non_muslim`) are represented as parent classes.
   - Subreddit-specific and text-specific concepts are added as subclasses.

3. **Text Classification:**

   - Leverages `SentenceTransformer` to embed text and RDF labels.
   - Matches input text with RDF labels using cosine similarity.
   - Classifies text based on semantic similarity and ontology hierarchy.

4. **Interactive Analysis:**

   - Outputs matching words, labels, similarity scores, and final classification.

---

### Requirements

1. **Programming Language:** Python 3.8+
2. **Libraries:**
   - `pandas`
   - `rdflib`
   - `nltk`
   - `sentence_transformers`
   - `scikit-learn`

Install dependencies with:

```bash
pip install pandas rdflib nltk sentence-transformers scikit-learn
```

3. **Dataset:**
   - The dataset should have columns `Document` (text) and `subreddit` (categories).
   - Example filename: `Text based Religion 35000.csv`

---

### Steps to Run

1. **Data Preprocessing:**

   - Load and clean the dataset using `pandas`.
   - Map similar subreddits to broader categories (e.g., `Muslim`, `Hijabis` to `islam`).
   - Drop unnecessary subreddits.

2. **RDF Ontology Creation:**

   - Run the `create_rdf_from_csv` function to generate an RDF ontology from the dataset.
   - Output: `religion_ontology.ttl` in Turtle format.

3. **Text Classification:**

   - Use `classify_text` to analyze new input text.
   - The script outputs matching words, similarity scores, and classification (`Islam` or `non_muslim`).

---

### Example Usage

```python
input_text = "Salam Ali how are you doing Insha Allah we will get good grades"
classification = classify_text(input_text)
print(f"Classification: {classification}")
```

**Output:**

```
Word: salam, Matched Label: islam, Similarity: 0.875
Word: ali, Matched Label: islam, Similarity: 0.802
Word: doing, Matched Label: non_muslim, Similarity: 0.678
...
Classification: Islam
```

---

### File Structure

- **Dataset:** `Text based Religion 35000.csv`
- **Script:**
  - Data preprocessing and cleaning
  - RDF ontology creation (`create_rdf_from_csv`)
  - Text classification (`classify_text`)
- **Ontology File:** `religion_ontology.ttl`

---

### Customization

- Update `labels_to_drop` to filter additional subreddits.
- Adjust similarity threshold in `classify_text` for stricter or looser matching.

---

### Limitations

- Classification relies on semantic embeddings and may misclassify due to ambiguous context.
- Requires adequate training data for meaningful embeddings.

---

### Future Improvements

- Expand the ontology with more subclasses for better granularity.
- Fine-tune the embedding model for religion-specific text.
- Add support for multi-class classification with additional categories.

---

