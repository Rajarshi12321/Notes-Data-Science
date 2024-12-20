# Minimum Edit Distance (Levenshtein Distance)

The **Levenshtein distance** is a metric for measuring the difference between two sequences (often strings) by counting the minimum number of operations required to transform one sequence into the other. The allowed operations are:

- **Insertion**: Adding a character to the string.
- **Deletion**: Removing a character from the string.
- **Substitution**: Replacing one character with another.

### Formula

The Levenshtein distance between two strings $a$ and $b$ is defined as the minimum number of edit operations required to transform string $a$ into string $b$. This can be computed recursively with the following recurrence relation:

$$
D(i, j) = 
\begin{cases}
  i & \text{if } j = 0 \\
  j & \text{if } i = 0 \\
  D(i-1, j-1) & \text{if } a[i] = b[j] \\
  1 + \min(D(i-1, j), D(i, j-1), D(i-1, j-1)) & \text{if } a[i] \neq b[j]
\end{cases}
$$

Where:
- $D(i, j)$ represents the distance between the first $i$ characters of $a$ and the first $j$ characters of $b$.

### Backtrace Algorithm (Dynamic Programming)

The **Backtrace algorithm** is used to compute the **minimum edit distance** using dynamic programming. It starts by filling out a matrix $D$, where each entry $D(i, j)$ holds the minimum number of edit operations needed to transform the substring $a[1..i]$ into $b[1..j]$.

The algorithm constructs the matrix based on the recurrence relation and then performs a **backtracking** step to determine the actual edit operations required. The backtracking starts from $D(m, n)$ and traces back to $D(0, 0)$.

- **Time Complexity**: The time complexity is $O(m \times n)$, where $m$ and $n$ are the lengths of the two input strings.

For a visual explanation, you can check out the video:  
- [Computing Minimum Edit Distance - YouTube](https://www.youtube.com/watch?v=5tO2KYYUvDk) (Time: 2:02 - 2:54)

---

# Weighted Edit Distance

The **weighted edit distance** is an extension of the Levenshtein distance, where each edit operation (insertion, deletion, substitution) can have a different cost. This is useful when different types of operations have different costs, for example, substituting one letter might be cheaper than inserting a new one.

### Formula for Weighted Edit Distance

The weighted edit distance can be computed as:

$$
D(i, j) = 
\begin{cases}
  i \times w_{\text{del}} & \text{if } j = 0 \\
  j \times w_{\text{ins}} & \text{if } i = 0 \\
  D(i-1, j-1) + \text{cost}(a[i], b[j]) & \text{if } a[i] \neq b[j] \\
  \min(D(i-1, j) + w_{\text{del}}, D(i, j-1) + w_{\text{ins}}) & \text{otherwise}
\end{cases}
$$

Where $w_{\text{del}}$ and $w_{\text{ins}}$ are the weights for deletions and insertions, respectively, and the cost for substitution depends on the difference between $a[i]$ and $b[j]$.

For more details, you can view this video:  
- [Weighted Minimum Edit Distance - YouTube](https://www.youtube.com/watch?v=2tt5WtH9lmI) (Time: 2:02 - 2:47)

---

# Computational Biology – Similarity

In computational biology, **sequence similarity** is crucial for comparing biological sequences, such as DNA, RNA, or proteins. This involves aligning sequences to identify regions of similarity that may indicate functional, structural, or evolutionary relationships between the sequences.

### Applications of Sequence Similarity:
- **Genomic alignment**: Aligning DNA sequences to find regions of similarity and differences.
- **Protein structure prediction**: Comparing amino acid sequences to predict the structure and function of proteins.
- **Phylogenetic analysis**: Understanding evolutionary relationships between species.

---

### Needleman-Wunsch Algorithm

The **Needleman-Wunsch algorithm** is a dynamic programming algorithm used for **global sequence alignment**, which aligns two sequences across their entire length. It attempts to find the optimal alignment by maximizing the total similarity between the two sequences.

#### Steps in Needleman-Wunsch Algorithm:
1. **Initialization**: Create a scoring matrix and initialize the first row and column with gap penalties.
2. **Matrix Filling**: Fill the matrix using a recurrence relation that calculates the maximum possible score considering matches, mismatches, and gaps.
3. **Backtracking**: Start from the bottom-right of the matrix and trace back to the top-left to determine the optimal alignment.

### Scoring:
- **Match**: +1 (or a positive value).
- **Mismatch**: -1 (or a negative value).
- **Gap penalty**: -2 (or a negative value).

For a detailed explanation, watch:  
- [Minimum Edit Distance in Computational Biology - YouTube](https://www.youtube.com/watch?v=9XzVq4PRAoE) (Time: 2:05 - 9:29)

---

### Overlap Detection Variant

In some cases, when aligning sequences, there may be overlapping subsequences that need to be detected and aligned separately. This is important for tasks like DNA fragment assembly, where overlapping DNA fragments need to be aligned correctly to form the full sequence.

---

## Local Alignment Problem – Smith-Waterman Algorithm

The **Smith-Waterman algorithm** is a dynamic programming algorithm used for **local sequence alignment**, which finds the optimal alignment of subsequences within two sequences. This algorithm is particularly useful when aligning sequences of different lengths or when the sequences contain regions of high similarity interspersed with regions of low similarity.

### Steps in Smith-Waterman Algorithm:
1. **Initialization**: Set the first row and column to zero, since no alignment of subsequences is possible with an empty sequence.
2. **Matrix Filling**: Use a recurrence relation to calculate the score for each cell, considering matches, mismatches, and gaps. The value in each cell represents the best score for aligning the subsequences up to that point.
3. **Backtracking**: Perform backtracking to find the optimal local alignment. The algorithm terminates when a cell with zero score is reached, indicating no further alignment is possible.

### Applications:
- **DNA sequence comparison**: Identifying conserved regions between two DNA sequences.
- **Protein structure alignment**: Aligning protein sequences to detect similar functional domains.

This algorithm can be used in cases where the goal is to find the most similar segment of two sequences, rather than aligning the entire sequence.

---

### Summary:

1. **Levenshtein Distance** is used to calculate the minimum edit distance between two strings.
2. **Backtrace Algorithm** uses dynamic programming to find the optimal set of operations for transforming one string into another.
3. **Weighted Edit Distance** introduces different costs for different types of edit operations.
4. **Needleman-Wunsch Algorithm** is used for global sequence alignment, essential in bioinformatics for aligning entire sequences.
5. **Smith-Waterman Algorithm** solves the local alignment problem, aligning the most similar parts of two sequences.

These algorithms play a key role in computational biology, especially in sequence comparison, genetic analysis, and protein structure prediction.
