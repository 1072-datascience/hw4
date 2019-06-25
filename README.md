# hw4. predict protein subcellular localization

![PredictProtein](/images/img1.png)

### Name: [your name in Chinese or English]
### Student ID: [your student ID]

## Description
Perform k-fold cross-validation for protein subcellular localization problem.

### cmd
```R
Rscript hw4_studentID.R --fold k --input Archaeal_tfpssm.csv --output performance.csv
```
* Perform *k*-fold cross-validation
* % of training, % of calibration, % of testing= *k*-2, 1, 1

![cross-validation](/images/img2.png)

## Input: Archaeal_tfpssm.csv

V2: labels of proteins

* CP: Cytoplasmic
* CW: Cell Wall
* EC: Extracellular
* IM: Inner membrane

V3 ~ V5602: the gapped-dipeptide features of each protein

### Code to read data

```R
d <- read.csv(<Path to Archaeal_tfpssm.csv>, header = F)
levels(d[,2])
head(d[,5600:5603]) 
```

## Model

* Any model you want
* Predict V2 value for each protein

## Output: performance.csv

* accuracy = *P*/*N*, average of *k*-fold cross-validation

set       |accuracy
---|---
training|0.91
validation|0.85
test|0.77

## Score

* 6 testing cmds from 5-fold to 10-fold
```R
Rscript hw4_studentID.R --fold 5 --input Archaeal_tfpssm.csv --output hw4/your_ID/output1.csv
...
Rscript hw4_studentID.R --fold 10 --input Archaeal_tfpssm.csv --output hw4/your_ID/output6.csv
```
Each testing cmd gets 15 points.

## Bonus
* Round number to two decimal places: 3 points
* Without “”: 2 points
* Performance Bonus: average testing performance
  * 0.99 ~: 5 points
  * 0.95 ~ 0.99: 4 points
  * 0.90 ~ 0.95: 3 points
  * 0.80 ~ 0.90: 2 points

## References
* Chang, J.-M. M. et al. (2013) [Efficient and interpretable prediction of protein functional classes by correspondence analysis and compact set relations](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0075542). *PLoS ONE* 8, e75542.
* Chang J-M, Su EC-Y, Lo A, Chiu H-S, Sung T-Y, & Hsu W-L (2008) [PSLDoc: Protein subcellular localization prediction based on gapped-dipeptides and probabilistic latent semantic analysis](https://onlinelibrary.wiley.com/doi/full/10.1002/prot.21944). *Proteins: Structure, Function, and Bioinformatics* 72(2):693-710.
