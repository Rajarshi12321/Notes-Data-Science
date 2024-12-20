
### **1. Regex Rules:**
**Regex** (Regular Expressions) is used for pattern matching in text.  
Here are some basic and common patterns:  

| **Pattern**       | **Explanation**                               | **Example**                           |
|--------------------|-----------------------------------------------|---------------------------------------|
| `\d+`             | Matches one or more digits                   | "123" matches; "abc" does not         |
| `[a-z]+`          | Matches one or more lowercase letters        | "abc" matches; "ABC" does not         |
| `[A-Za-z]+`       | Matches one or more letters (any case)       | "Hello" matches; "123" does not       |
| `\bword\b`        | Matches whole word "word"                    | "word" matches; "sword" does not      |
| `\w+`             | Matches one or more word characters          | "word1" matches; "%&" does not        |
| `[^a-zA-Z]`       | Matches non-alphabetical characters          | "123" matches; "abc" does not         |
| `(abc|def)`       | Matches "abc" or "def"                       | "abc" matches; "ghi" does not         |

---

### **2. Regex Substitution:**
- Substitution replaces matched patterns with specified replacements.  
  Example (Python):  
  ```python
  import re
  text = "I love cats and dogs."
  result = re.sub(r'cats|dogs', 'animals', text)
  print(result)  # Output: "I love animals and animals."
  ```

---

### **3. Lemmatization (Lemma):**
**Definition:**  
Lemmatization reduces a word to its base form (lemma) using vocabulary and grammar rules.  

**Example:**  
| **Word Form** | **Lemma** |
|---------------|-----------|
| "running"     | "run"     |
| "better"      | "good"    |
| "studies"     | "study"   |

- **Small Note:** Lemmatization considers context (e.g., part of speech).

---

### **4. Stemming (Stem):**
**Definition:**  
Stemming reduces a word to its root form by chopping off affixes. It is rule-based and may not produce valid words.  

**Example:**  
| **Word Form** | **Stem** |
|---------------|----------|
| "running"     | "run"    |
| "studies"     | "studi"  |
| "happiness"   | "happi"  |

---

### **5. Porter Stemmer:**
- The **Porter Stemming Algorithm** is one of the most common stemming techniques.
- Developed by Martin Porter in 1980.
- Operates in five phases, applying rules like:
  - Removing plurals: `caresses` → `caress`
  - Removing suffixes: `running` → `run`

**Python Example:**  
```python
from nltk.stem import PorterStemmer
ps = PorterStemmer()
print(ps.stem("running"))  # Output: "run"
```

---

### **6. Word Forms (Small Notes):**
- Word forms include variations of a base word:
  - **Inflections:** Plural/singular, tense (e.g., "dog", "dogs"; "run", "ran").
  - **Derivatives:** Formed by adding prefixes or suffixes (e.g., "happiness" → "happy").
- Understanding word forms is critical for NLP tasks like text normalization.

--- 
