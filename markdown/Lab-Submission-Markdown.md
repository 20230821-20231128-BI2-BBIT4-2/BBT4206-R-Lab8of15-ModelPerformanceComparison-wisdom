Business Intelligence Project
================
wisdom
06/11/23

- [Student Details](#student-details)
  - [R Markdown](#r-markdown)
  - [STEP 1. Install and Load the Required Packages
    —-](#step-1-install-and-load-the-required-packages--)
    - [STEP 2. Load the Dataset —-](#step-2-load-the-dataset--)
    - [STEP 4. Display the Results —-](#step-4-display-the-results--)
  - [5. Pairwise xyPlots —-](#5-pairwise-xyplots--)
  - [6. Statistical Significance Tests
    —-](#6-statistical-significance-tests--)
- [This is used to calculate the significance of the differences between
  the](#this-is-used-to-calculate-the-significance-of-the-differences-between-the)
- [metric distributions of the various
  models.](#metric-distributions-of-the-various-models)
  - [Upper Diagonal —-](#upper-diagonal--)
- [The upper diagonal of the table shows the estimated difference
  between
  the](#the-upper-diagonal-of-the-table-shows-the-estimated-difference-between-the)
- [distributions. If we think that LDA is the most accurate model from
  looking](#distributions-if-we-think-that-lda-is-the-most-accurate-model-from-looking)
- [at the previous graphs, we can get an estimate of how much better it
  is
  than](#at-the-previous-graphs-we-can-get-an-estimate-of-how-much-better-it-is-than)
- [specific other models in terms of absolute
  accuracy.](#specific-other-models-in-terms-of-absolute-accuracy)
  - [Lower Diagonal —-](#lower-diagonal--)
- [The lower diagonal contains p-values of the null
  hypothesis.](#the-lower-diagonal-contains-p-values-of-the-null-hypothesis)
- [The null hypothesis is a claim that “the distributions are the
  same”.](#the-null-hypothesis-is-a-claim-that-the-distributions-are-the-same)
- [A lower p-value is better (more
  significant).](#a-lower-p-value-is-better-more-significant)

# Student Details

|                                              |        |
|----------------------------------------------|--------|
| **Student ID Number**                        | …      |
| **Datasets Used**                            | Iris   |
| **BBIT 4.2 Group**                           | .A..   |
| **BI Project Group Name/ID (if applicable)** | WISDOM |

## R Markdown

This is an R Markdown document. Markdown is a simple formatting syntax
for authoring HTML, PDF, and MS Word documents. For more details on
using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that
includes both content as well as the output of any embedded R code
chunks within the document. You can embed an R code chunk like this:

``` r
.libPaths()
```

    ## [1] "C:/Users/25479/AppData/Local/R/win-library/4.3"
    ## [2] "C:/Program Files/R/R-4.3.1/library"

``` r
lapply(.libPaths(), list.files)
```

    ## [[1]]
    ##   [1] "abind"           "Amelia"          "arules"          "arulesViz"      
    ##   [5] "askpass"         "backports"       "base64enc"       "BayesFactor"    
    ##   [9] "bit"             "bit64"           "blob"            "brew"           
    ##  [13] "brio"            "broom"           "bslib"           "ca"             
    ##  [17] "cachem"          "Cairo"           "callr"           "car"            
    ##  [21] "carData"         "caret"           "cellranger"      "circlize"       
    ##  [25] "classInt"        "cli"             "clipr"           "clock"          
    ##  [29] "coda"            "collections"     "colorspace"      "colourpicker"   
    ##  [33] "combinat"        "commonmark"      "conflicted"      "contfrac"       
    ##  [37] "corrplot"        "covr"            "cowplot"         "cpp11"          
    ##  [41] "crayon"          "crosstalk"       "curl"            "cyclocomp"      
    ##  [45] "data.table"      "DBI"             "dbplyr"          "dendextend"     
    ##  [49] "desc"            "deSolve"         "diagram"         "diffobj"        
    ##  [53] "digest"          "dplyr"           "DT"              "dtplyr"         
    ##  [57] "e1071"           "ellipse"         "ellipsis"        "elliptic"       
    ##  [61] "emmeans"         "estimability"    "evaluate"        "factoextra"     
    ##  [65] "FactoMineR"      "fansi"           "farver"          "fastICA"        
    ##  [69] "fastmap"         "flashClust"      "fontawesome"     "forcats"        
    ##  [73] "foreach"         "formatR"         "formattable"     "fs"             
    ##  [77] "future"          "future.apply"    "gargle"          "gclus"          
    ##  [81] "generics"        "ggcorrplot"      "ggforce"         "ggplot2"        
    ##  [85] "ggpubr"          "ggraph"          "ggrepel"         "ggsci"          
    ##  [89] "ggsignif"        "glmnet"          "GlobalOptions"   "globals"        
    ##  [93] "glue"            "googledrive"     "googlesheets4"   "gower"          
    ##  [97] "graphlayouts"    "gridExtra"       "gtable"          "hardhat"        
    ## [101] "haven"           "highr"           "hms"             "htmltools"      
    ## [105] "htmlwidgets"     "httpuv"          "httr"            "hypergeo"       
    ## [109] "ids"             "igraph"          "ipred"           "isoband"        
    ## [113] "iterators"       "janeaustenr"     "jomo"            "jpeg"           
    ## [117] "jquerylib"       "jsonlite"        "kableExtra"      "kernlab"        
    ## [121] "klaR"            "knitr"           "labeling"        "labelled"       
    ## [125] "languageserver"  "later"           "lava"            "lazyeval"       
    ## [129] "leaps"           "LiblineaR"       "lifecycle"       "lintr"          
    ## [133] "listenv"         "lme4"            "lmtest"          "lubridate"      
    ## [137] "magick"          "magrittr"        "markdown"        "Matrix"         
    ## [141] "MatrixModels"    "memery"          "memoise"         "mice"           
    ## [145] "mime"            "miniUI"          "minqa"           "mitml"          
    ## [149] "mlbench"         "mockery"         "ModelMetrics"    "modelr"         
    ## [153] "multcompView"    "munsell"         "mvtnorm"         "naivebayes"     
    ## [157] "naniar"          "NHANES"          "nloptr"          "norm"           
    ## [161] "numDeriv"        "openssl"         "ordinal"         "pacman"         
    ## [165] "pan"             "parallelly"      "pbapply"         "pbkrtest"       
    ## [169] "permute"         "pillar"          "pkgbuild"        "pkgconfig"      
    ## [173] "pkgload"         "plotly"          "plumber"         "plyr"           
    ## [177] "png"             "polyclip"        "polynom"         "praise"         
    ## [181] "prettyunits"     "pROC"            "processx"        "prodlim"        
    ## [185] "progress"        "progressr"       "promises"        "proxy"          
    ## [189] "ps"              "purrr"           "qap"             "quantreg"       
    ## [193] "questionr"       "R.cache"         "R.methodsS3"     "R.oo"           
    ## [197] "R.utils"         "R6"              "radarchart"      "ragg"           
    ## [201] "randomForest"    "rappdirs"        "RColorBrewer"    "Rcpp"           
    ## [205] "RcppArmadillo"   "RcppEigen"       "readr"           "readxl"         
    ## [209] "recipes"         "registry"        "rematch"         "rematch2"       
    ## [213] "remotes"         "reprex"          "reshape2"        "rex"            
    ## [217] "rlang"           "rmarkdown"       "roxygen2"        "rprojroot"      
    ## [221] "RRF"             "rstatix"         "rstudioapi"      "rvest"          
    ## [225] "sass"            "scales"          "scatterplot3d"   "selectr"        
    ## [229] "seriation"       "shape"           "shiny"           "shinyBS"        
    ## [233] "shinycssloaders" "shinyjs"         "showtext"        "showtextdb"     
    ## [237] "SnowballC"       "sodium"          "sourcetools"     "SparseM"        
    ## [241] "SQUAREM"         "stringi"         "stringr"         "styler"         
    ## [245] "svglite"         "swagger"         "sys"             "sysfonts"       
    ## [249] "systemfonts"     "testthat"        "textshaping"     "tibble"         
    ## [253] "tidygraph"       "tidyr"           "tidyselect"      "tidytext"       
    ## [257] "tidyverse"       "timechange"      "timeDate"        "tinytex"        
    ## [261] "tokenizers"      "TSP"             "tweenr"          "tzdb"           
    ## [265] "ucminf"          "UpSetR"          "utf8"            "uuid"           
    ## [269] "vcd"             "vctrs"           "vegan"           "viridis"        
    ## [273] "viridisLite"     "visdat"          "visNetwork"      "vroom"          
    ## [277] "waldo"           "webshot"         "webutils"        "widyr"          
    ## [281] "withr"           "wordcloud2"      "xfun"            "xml2"           
    ## [285] "xmlparsedata"    "xtable"          "yaml"            "yarrr"          
    ## [289] "zoo"            
    ## 
    ## [[2]]
    ##  [1] "base"         "boot"         "class"        "cluster"      "codetools"   
    ##  [6] "compiler"     "datasets"     "foreign"      "graphics"     "grDevices"   
    ## [11] "grid"         "KernSmooth"   "lattice"      "MASS"         "Matrix"      
    ## [16] "methods"      "mgcv"         "nlme"         "nnet"         "parallel"    
    ## [21] "rpart"        "spatial"      "splines"      "stats"        "stats4"      
    ## [26] "survival"     "tcltk"        "tools"        "translations" "utils"

``` r
if (require("languageserver")) {
  require("languageserver")
} else {
  install.packages("languageserver", dependencies = TRUE,
                   repos = "https://cloud.r-project.org")
}
```

    ## Loading required package: languageserver

## STEP 1. Install and Load the Required Packages —-

### STEP 2. Load the Dataset —-

``` r
data("iris")
train_control <- trainControl(method = "repeatedcv", number = 10, repeats = 3)

### LDA ----
set.seed(7)
Species_model_lda <- train(Species ~ ., data = iris,
                            method = "lda", trControl = train_control)

### CART ----
set.seed(7)
Species_model_cart <- train(Species ~ ., data = iris,
                             method = "rpart", trControl = train_control)

### KNN ----
set.seed(7)
Species_model_knn <- train(Species ~ ., data = iris,
                            method = "knn", trControl = train_control)

### SVM ----
set.seed(7)
Species_model_svm <- train(Species ~ ., data = iris,
                            method = "svmRadial", trControl = train_control)

### Random Forest ----
set.seed(7)
Species_model_rf <- train(Species ~ ., data = iris,
                           method = "rf", trControl = train_control)
## 3.b. Call the `resamples` Function ----
results <- resamples(list(LDA = Species_model_lda, CART = Species_model_cart,
                          KNN = Species_model_knn, SVM = Species_model_svm,
                          RF = Species_model_rf))
```

### STEP 4. Display the Results —-

## 5. Pairwise xyPlots —-

## 6. Statistical Significance Tests —-

# This is used to calculate the significance of the differences between the

# metric distributions of the various models.

## Upper Diagonal —-

# The upper diagonal of the table shows the estimated difference between the

# distributions. If we think that LDA is the most accurate model from looking

# at the previous graphs, we can get an estimate of how much better it is than

# specific other models in terms of absolute accuracy.

## Lower Diagonal —-

# The lower diagonal contains p-values of the null hypothesis.

# The null hypothesis is a claim that “the distributions are the same”.

# A lower p-value is better (more significant).

``` r
summary(results)
```

    ## 
    ## Call:
    ## summary.resamples(object = results)
    ## 
    ## Models: LDA, CART, KNN, SVM, RF 
    ## Number of resamples: 30 
    ## 
    ## Accuracy 
    ##           Min.   1st Qu.    Median      Mean 3rd Qu. Max. NA's
    ## LDA  0.8666667 0.9500000 1.0000000 0.9800000       1    1    0
    ## CART 0.8000000 0.9333333 0.9333333 0.9333333       1    1    0
    ## KNN  0.8666667 0.9333333 1.0000000 0.9666667       1    1    0
    ## SVM  0.8000000 0.9333333 0.9666667 0.9511111       1    1    0
    ## RF   0.8666667 0.9333333 0.9333333 0.9600000       1    1    0
    ## 
    ## Kappa 
    ##      Min. 1st Qu. Median      Mean 3rd Qu. Max. NA's
    ## LDA   0.8   0.925   1.00 0.9700000       1    1    0
    ## CART  0.7   0.900   0.90 0.9000000       1    1    0
    ## KNN   0.8   0.900   1.00 0.9500000       1    1    0
    ## SVM   0.7   0.900   0.95 0.9266667       1    1    0
    ## RF    0.8   0.900   0.90 0.9400000       1    1    0

``` r
## 2. Box and Whisker Plot ----
# This is useful for visually observing the spread of the estimated accuracies
# for different algorithms and how they relate.

scales <- list(x = list(relation = "free"), y = list(relation = "free"))
bwplot(results, scales = scales)
```

![](Lab-Submission-Markdown_files/figure-gfm/Table%20Summary-1.png)<!-- -->

``` r
## 3. Dot Plots ----
# They show both the mean estimated accuracy as well as the 95% confidence
# interval (e.g. the range in which 95% of observed scores fell).

scales <- list(x = list(relation = "free"), y = list(relation = "free"))
dotplot(results, scales = scales)
```

![](Lab-Submission-Markdown_files/figure-gfm/Table%20Summary-2.png)<!-- -->

``` r
## 4. Scatter Plot Matrix ----
# This is useful when considering whether the predictions from two
# different algorithms are correlated. If weakly correlated, then they are good
# candidates for being combined in an ensemble prediction.

splom(results)
```

![](Lab-Submission-Markdown_files/figure-gfm/Table%20Summary-3.png)<!-- -->

``` r
## 5. Pairwise xyPlots ----
# You can zoom in on one pairwise comparison of the accuracy of trial-folds for
# two models using an xyplot.

# xyplot plots to compare models
xyplot(results, models = c("LDA", "SVM"))
```

![](Lab-Submission-Markdown_files/figure-gfm/Table%20Summary-4.png)<!-- -->

``` r
# or
# xyplot plots to compare models
xyplot(results, models = c("SVM", "CART"))
```

![](Lab-Submission-Markdown_files/figure-gfm/Table%20Summary-5.png)<!-- -->

``` r
## 6. Statistical Significance Tests ----

diffs <- diff(results)

summary(diffs)
```

    ## 
    ## Call:
    ## summary.diff.resamples(object = diffs)
    ## 
    ## p-value adjustment: bonferroni 
    ## Upper diagonal: estimates of the difference
    ## Lower diagonal: p-value for H0: difference = 0
    ## 
    ## Accuracy 
    ##      LDA      CART      KNN       SVM       RF       
    ## LDA            0.046667  0.013333  0.028889  0.020000
    ## CART 0.001444           -0.033333 -0.017778 -0.026667
    ## KNN  1.000000 0.003853             0.015556  0.006667
    ## SVM  0.097915 0.433974  0.698427            -0.008889
    ## RF   0.173724 0.014258  1.000000  1.000000           
    ## 
    ## Kappa 
    ##      LDA      CART     KNN      SVM      RF      
    ## LDA            0.07000  0.02000  0.04333  0.03000
    ## CART 0.001444          -0.05000 -0.02667 -0.04000
    ## KNN  1.000000 0.003853           0.02333  0.01000
    ## SVM  0.097915 0.433974 0.698427          -0.01333
    ## RF   0.173724 0.014258 1.000000 1.000000

Note that the `echo = FALSE` parameter was added to the code chunk to
prevent printing of the R code that generated the plot.
