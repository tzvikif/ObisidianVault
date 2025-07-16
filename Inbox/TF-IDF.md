

24-06-2025 11:42

Status: 

Tags:

# TF-IDF

מדד לחשיבות מילים במסמכים.
מילים יקבלו ערך גבוה עבור מסמך מסויים אם הן נמצאות מספר רב של פעמים במסמך מסויים ולא נמצאות הרבה פעמים בשאר המסמכים.

${TF-IDF}(t, d) = \text{TF}(t, d) \times \underbrace{\log\left( \frac{N}{DF(t)} \right)}_{IDF}$
$TF(t,d)$=$\frac{f_{t,d}}{\displaystyle \sum_{t'\in d}^{}f_{t',d}}$

$f_{t,d}$: number of times term $t$ appears in document $d$
denominator: total number of term occurrences in $d$

### Advantages
- **Boosts** terms that are **important in a document** but **rare across the corpus**
- **Downweights** common terms like “the”, “good”, “and” even if they appear frequently
### Usage
provides better features for:
- Classification
- Information retrieval
- Clustering
## TF
*term frequency*
$output_{i,j}=\frac{count\:of\:term\:j\:in\:document\:i}{norm\:of\:document\:i}$
$norm_{L_{2}}=\sqrt{ x_{1}^2+x_{2}^2+\cdots+x_{n}^2 }$

*TF* by itself 
- Measures local importance
- **Doesn't** consider how common t is across the corpus
### example
we have the following tokens in a document i
["apple", "banana", "apple"]
TF vector (counts): `{"apple": 2, "banana": 1}`
raw vector: $x=[2,1]$
$normL_{2}$: $\|X\|_{2}$=$\sqrt{ 2^2+1^2 }$=$\sqrt{ 5 }$
Normalized vector: $[ \frac{2}{\sqrt{ 5 }},\frac{1}{\sqrt{ 5 }}]$

## IDF
*Inverse Document Frequency*
$IDF(t)$= $\log\left( \frac{N}{DF(t)} \right)$
$N$: total number of documents
$DF(t)$: number of documents that contain term $t$
## My Questions

how does it relate to $chi^2$
## References

