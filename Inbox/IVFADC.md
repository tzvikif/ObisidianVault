

06-05-2026 11:45

Status: #in_progress

Tags:

# IVFADC

$y\approx q_{1}(y)+q_{2}(y-q_{1}(y))$

## Coarse centroids for $q_{1}$
let the DB vectors be: $y_{1},\dots y_{N}$
each vector has dimension *d*
we choose the number of *nlist*. for example *nlist*=4096
*nlist* is the number clusters.
- train 4096 centroids using [[k-means]]. usually the training set is just a subset of all the vectors.
- assign each vector to the closest centroid and store it in *IVF* list. 
centroid_1 -> v_5, v_132,...

## PQ centroids for $q_{2}$
split each residual $r=q_{2}(y-q_{1}(y)$ into parts
d = 128
m = 16 (number of splits)
subvector dimention = 8
$r=[r^{(1)},r^{(2)},\dots,r^{(16)}]$

for each subvector position(1...16) run [[k-means]] separately , with 256 clusters.
that creates *codebook* of  size 256 for the 16 positions.

| Quantizer | Training data                   | Output                |
| --------- | ------------------------------- | --------------------- |
| `q1`      | full vectors `y`                | coarse centroids      |
| `q2`      | residual subvectors `y - q1(y)` | PQ codebook centroids |

**codebook 1**
$v_{1,1},v_{1,2},\dots,v_{1,8}:id_{1,1}$
$v_{2,1},v_{2,2},\dots,v_{1,8}:id_{2,1}$
$\dots, v_{256,1},v_{256,2},\dots,v_{256,8}:id_{256,1}$
$\dots$
**codebook 16**
$v_{1,121},v_{1,122},\dots,v_{1,128}:id_{1,128}$
$v_{2,121},v_{2,122},\dots,v_{1,128}:id_{2,128}$
$\dots, v_{256,121},v_{256,122},\dots,v_{256,128}:id_{256,128}$

each vector in the DB in represented as *16* dimensional vector.
$id_{1,1},\dots,id_{N,16}$ . *N* is the number of vector in the DB.

let x be a query vector

1. $q_{1}(x)$
2. $y=x-q_{1}(x)$
3. let L be their vectors.
4. for each $l\in L$ create table of distances from x
$dist(codebook_{1}[l_{id_{1}}],y[1\dots{8}]), \dots,dist(codebook_{16}[l_{id_{16}}],y[121\dots{128}])$
 
find $l$ s.t 



## My Questions


## References

