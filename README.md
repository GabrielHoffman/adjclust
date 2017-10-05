# adjclust: Adjacency-constrained clustering of a block-diagonal similarity matrix

`adjclust` is a package that provides methods to perform adjacency-constrained hierarchical agglomerative clustering. Adjacency-constrained hierarchical agglomerative clustering is hierarchical agglomerative clustering (HAC) in which each observation is associated to a position, and the clustering is constrained so as only adjacent clusters are merged. It is a common method used widely in various application fields including ecology (Quaternary data) and bioinformatics (e.g. Genome Wide Association Studies or Hi-C data analysis).

`adjclust` provides three user level functions: `adjClust`, `snpClust` and `hicClust`:

- `adjClust` performs adjacency-constrained HAC for standard and sparse, similarity and dissimilarity matrices and dist objects. Matrix::dgCMatrix and Matrix::dsCMatrix are the supported sparse matrix classes. Let's look at a basic example

```r
library("adjclust")

sim <- matrix(c(1,0.1,0.2,0.3,0.1,1,0.4,0.5,0.2,0.4,1,0.6,0.3,0.5,0.6,1), nrow=4)
h <- 3
fit <- adjClust(sim, "similarity", h, 1, FALSE)
plot(fit)
```

The result is of class `chac`. It can be plotted as a dendogram (as shown above). Successive merge and heights of clustering can be obtained by `fit$merge` and `fit$height` respectively.

- `snpClust` performs adjacency-constrained HAC for specific application of Genome Wide Association Studies (GWAS). See [GWAS Vignette](vignettes/snpClust.Rmd) for details.

- `hicClust`function performs adjacency-constrained HAC for specific application of Hi-C data analysis. See [Hi-C Vignette](vignettes/hicClust.Rmd) for details.


*Version 0.4.0 of this package was completed by Shubham Chaturvedi as a part of the [Google Summer of Code 2017](https://summerofcode.withgoogle.com/projects/#4961904920363008) program*

