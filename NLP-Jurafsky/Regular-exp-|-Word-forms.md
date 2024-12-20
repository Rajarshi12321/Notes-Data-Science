## Regex and Patterns

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
<br>
<br>

## Tokenization and Vocabulary growth size

### **1. Heap’s Law and Herdan’s Law: Vocabulary Size Growth**
---

#### **Heap’s Law**  
Heap’s Law describes the relationship between the size of a text corpus and the growth of its vocabulary.  

The formula for Heap's Law is $V(n) = K \cdot n^\beta$, where:
- $V(n)$ is the vocabulary size.
- $n$ is the number of tokens.
- $K$ and $\beta$ are constants.

**Key Insight:**  
- Vocabulary grows sub-linearly with the size of the corpus, meaning the rate of encountering new words decreases as text size increases.  

---

#### **Herdan’s Law**  
Herdan’s Law is similar to Heap’s Law and states that the growth of vocabulary follows a power-law distribution. It is often used interchangeably with Heap’s Law, but the emphasis is on the mathematical foundation of vocabulary distribution in natural language.  

---

### **2. Clitics**
Clitics are morphemes (smallest meaningful units) that cannot stand alone as independent words and attach to a host word.  

**Examples:**  
- **English:**  
  - "I'm" → "I am" (clitic: "'m")  
  - "They'll" → "They will" (clitic: "'ll")  
- **French:**  
  - "l'arbre" → "le arbre" (clitic: "l'")  

**Note:**  
Clitics differ from affixes (prefixes/suffixes) because they retain some syntactic independence.

---

### **3. Subword Tokenization**
Subword tokenization breaks words into smaller units for language modeling and NLP tasks. This approach is particularly effective for handling:  
- Rare words  
- Morphologically rich languages  


#### **Techniques:**

##### **a. Byte Pair Encoding (BPE)**  
- BPE iteratively merges frequent pairs of symbols (subwords or characters).  
- Common in models like GPT and OpenAI's LLMs.  

**Steps:**  
1. Start with characters as individual units.  
2. Merge the most frequent pair of symbols.  
3. Repeat until a vocabulary limit is reached.  

**Example:**  
For "lower, lowest":  
- Initial: `l o w e r, l o w e s t`  
- Merge `l o w` → `low`  
- Merge `low e r` → `lower`  
- Merge `low e s t` → `lowest`





https://github.com/user-attachments/assets/fba56916-42a8-499a-8814-90848366c82b


[Read the BPE-Blog](https://huggingface.co/learn/nlp-course/en/chapter6/5)


---

##### **b. WordPiece**
- Similar to BPE but uses a probabilistic approach to merge subwords.  
- Common in models like BERT.  

**Key Difference from BPE:**  
- WordPiece optimizes for likelihood in a language model rather than raw frequency.  



https://github.com/user-attachments/assets/6c3a6dc0-1afd-416e-b4a0-e12a961d65de

[Read the WordPiece-Blog](https://huggingface.co/learn/nlp-course/en/chapter6/6?fw=pt)




---

##### **c. Unigram**
- A probabilistic subword segmentation method.  
- Begins with a large vocabulary and removes the least likely subwords iteratively.  

**Example (Probabilistic Assignment):**  
- "playing" → {"play", "ing"}, {"pl", "ay", "ing"}  
- Chooses segmentation with the highest probability.  



https://github.com/user-attachments/assets/727d0c8f-d6aa-497f-8c3f-58870299ac1b




[Read the Unicode-Blog](https://huggingface.co/learn/nlp-course/en/chapter6/7?fw=pt)

---

### **4. Morphene**
A **morpheme** is the smallest grammatical unit in a language that carries meaning.  

**Types of Morphemes:**  
1. **Free Morphemes:** Can stand alone (e.g., "book", "run").  
2. **Bound Morphemes:** Cannot stand alone (e.g., prefixes like "un-", suffixes like "-ing").  

**Significance:**  
- Morphological analysis is central to tokenization, especially in morphologically rich languages.

---

### **5. Recommended Resource:**  
For more on BPE, WordPiece, and Unigram Tokenization:  
- **Video:** [Byte Pair Encoding - YouTube](https://www.youtube.com/results?search_query=byte+pair+encoding)  

Let me know if you'd like more examples or a deeper dive into any of these topics!


