---
publish: true
created: 2026-10-12T10:33:42.179Z
modified: 2026-10-20T13:29:54.536Z
---

# Some notes on Rstudio and R

2026-10-12 :

- Installed base R and Rstudio
  - R version 4.3.3 (2024-02-29) -- "Angel Food Cake"
- Changed theme to "Pastel on Dark"
- Some notes/websites on RMarkdown:
  - https://rmarkdown.rstudio.com/lesson-1.html
  - https://pkg.yihui.org/rmarkdown-book/
    - https://pkg.yihui.org/rmarkdown-book/how-to-read-this-book
    - 4 parts:
      - 1: Basics (Installation and basic Goal and what can be achieved)
      - 2: Documentation (built-in output formats)
      - 3: 10 Extensions
        - 3.1 flexdashboards
        - 3.2 tufte ([Edward Tufte](https://en.wikipedia.org/wiki/Edward_Tufte))
        - 3.3 xaringan (https://remarkjs.com/)
        - 3.4 revealjs (https://revealjs.com)
        - 3.5 R Community output formats (prettydoc)
        - 3.6 Create websites (blogdown or built-in site generator)
        - 3.7 documentation websites for R Packages (pckgdown)
        - 3.8 write and publish books (bookdown)
        - 3.9 journal articles using rticles
        - 3.10 interactive tutorials with quizes
      - 4: Advanced Topics
- Installed RMarkdown

```R
install.packages("rmarkdown")	  
```

- Installed devtools

```R
install.packages("devtools")
```

## Some notes from "RMarkdown: The Definitive Guide"

2026-10-14:

### 01 Installation

- Ran into some issues with the devtools package.
- Turns out it is easily like this
  - You want to install "tidyverse"
  - Tidyverse depends on some other package
  - that other package has a dependency that is not installed in your machine
- Solution: Trial and Error
  - Try and install "Tidyverse"
  - Run into issues (depends o package "X")
  - Try and install package "X"
  - Run into issues (X depends on some Linux dependency)
  - Install Linux dependency
  - Go back to Tidyverse
- I followed this process and successfully installed necessary packages for econometrics (list of packages are given by the EPE lectures)
- Installed rmarkdown

```R
  install.packages('rmarkdown')
```

- Installed tinytex

```R
install.packages("tinytex")
```

- installed knitr

```R
install.packages("knitr")
```

#### Why Rmarkdown

Both the R code as well as the original data and also some text can be made into an html file using Rmarkdown. This is a good idea because:

- Reproducability
- Accountability
- Tutorials
- Learning R

### 02 Basics

- Got into issues while trying to "knit" some document
- Tried installing the "Rcpp" package
- Nope the issue was
  - I had installed 4.3 and some packages came with that
  - There was an issue with the yaml package
  - After reinstallng the yaml package now it works perfect!

```R
install.packages(
    "yaml",
    lib = "/home/writwik/R/x86_64-pc-linux-gnu-library/4.6",
    repos = "https://cloud.r-project.org"
)
```

- The "Run all chunks above" is a really useful button ![[00Archive/run-al-chunks-above.png]]
- Make good use of the Headings feature to go from topic to topic while editing (You can see under the Outlines tab just besides the code editor window)
- Idea: Create a R Project and make different RMarkdown files
  - I started out with EPE under the folder LearningR

## Demo R Code

The code chunks below should be running and printed along with its output to my website!

```R
# file.choose() is an useful function!
#iris1 <- read.table(file=file.choose())
# Now let's read the csv!
iris2 <- read.csv(file="/home/writwik/data-science/datasets/iris.csv")

#summary
summary(iris2)

```

sepal.length    sepal.width     petal.length    petal.width\
Min.   :4.300   Min.   :2.000   Min.   :1.000   Min.   :0.100\
1st Qu.:5.100   1st Qu.:2.800   1st Qu.:1.600   1st Qu.:0.300\
Median :5.800   Median :3.000   Median :4.350   Median :1.300\
Mean   :5.843   Mean   :3.057   Mean   :3.758   Mean   :1.199\
3rd Qu.:6.400   3rd Qu.:3.300   3rd Qu.:5.100   3rd Qu.:1.800\
Max.   :7.900   Max.   :4.400   Max.   :6.900   Max.   :2.500\
variety\
Length   :150\
N.unique :  3\
N.blank  :  0\
Min.nchar:  6\
Max.nchar: 10

```R

#I  want to remove the headers(column names)
iris_cleaned <- read.csv("/home/writwik/data-science/datasets/iris.csv",header=FALSE, skip=1)
iris_cleaned

summary(iris_cleaned)

names(iris_cleaned) <- c("Sepal.Length","Sepal.Width","Petal.Length","Petal.Width","Species" )
names(iris_cleaned)
summary(iris_cleaned)

colnames(iris_cleaned)
rownames(iris_cleaned)
```
