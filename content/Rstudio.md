---
publish: true
created: 2026-10-12T10:33:42.179Z
modified: 2026-10-26T10:15:36.199Z
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

z

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

Output:

```
     V1  V2  V3  V4         V5
1   5.1 3.5 1.4 0.2     Setosa
2   4.9 3.0 1.4 0.2     Setosa
3   4.7 3.2 1.3 0.2     Setosa
4   4.6 3.1 1.5 0.2     Setosa
5   5.0 3.6 1.4 0.2     Setosa
6   5.4 3.9 1.7 0.4     Setosa
7   4.6 3.4 1.4 0.3     Setosa
8   5.0 3.4 1.5 0.2     Setosa
9   4.4 2.9 1.4 0.2     Setosa
10  4.9 3.1 1.5 0.1     Setosa
11  5.4 3.7 1.5 0.2     Setosa
12  4.8 3.4 1.6 0.2     Setosa
13  4.8 3.0 1.4 0.1     Setosa
14  4.3 3.0 1.1 0.1     Setosa
15  5.8 4.0 1.2 0.2     Setosa
16  5.7 4.4 1.5 0.4     Setosa
17  5.4 3.9 1.3 0.4     Setosa
18  5.1 3.5 1.4 0.3     Setosa
19  5.7 3.8 1.7 0.3     Setosa
20  5.1 3.8 1.5 0.3     Setosa
21  5.4 3.4 1.7 0.2     Setosa
22  5.1 3.7 1.5 0.4     Setosa
23  4.6 3.6 1.0 0.2     Setosa
24  5.1 3.3 1.7 0.5     Setosa
25  4.8 3.4 1.9 0.2     Setosa
26  5.0 3.0 1.6 0.2     Setosa
27  5.0 3.4 1.6 0.4     Setosa
28  5.2 3.5 1.5 0.2     Setosa
29  5.2 3.4 1.4 0.2     Setosa
30  4.7 3.2 1.6 0.2     Setosa
31  4.8 3.1 1.6 0.2     Setosa
32  5.4 3.4 1.5 0.4     Setosa
33  5.2 4.1 1.5 0.1     Setosa
34  5.5 4.2 1.4 0.2     Setosa
35  4.9 3.1 1.5 0.2     Setosa
36  5.0 3.2 1.2 0.2     Setosa
37  5.5 3.5 1.3 0.2     Setosa
38  4.9 3.6 1.4 0.1     Setosa
39  4.4 3.0 1.3 0.2     Setosa
40  5.1 3.4 1.5 0.2     Setosa
41  5.0 3.5 1.3 0.3     Setosa
42  4.5 2.3 1.3 0.3     Setosa
43  4.4 3.2 1.3 0.2     Setosa
44  5.0 3.5 1.6 0.6     Setosa
45  5.1 3.8 1.9 0.4     Setosa
46  4.8 3.0 1.4 0.3     Setosa
47  5.1 3.8 1.6 0.2     Setosa
48  4.6 3.2 1.4 0.2     Setosa
49  5.3 3.7 1.5 0.2     Setosa
50  5.0 3.3 1.4 0.2     Setosa
51  7.0 3.2 4.7 1.4 Versicolor
52  6.4 3.2 4.5 1.5 Versicolor
53  6.9 3.1 4.9 1.5 Versicolor
54  5.5 2.3 4.0 1.3 Versicolor
55  6.5 2.8 4.6 1.5 Versicolor
56  5.7 2.8 4.5 1.3 Versicolor
57  6.3 3.3 4.7 1.6 Versicolor
58  4.9 2.4 3.3 1.0 Versicolor
59  6.6 2.9 4.6 1.3 Versicolor
60  5.2 2.7 3.9 1.4 Versicolor
61  5.0 2.0 3.5 1.0 Versicolor
62  5.9 3.0 4.2 1.5 Versicolor
63  6.0 2.2 4.0 1.0 Versicolor
64  6.1 2.9 4.7 1.4 Versicolor
65  5.6 2.9 3.6 1.3 Versicolor
66  6.7 3.1 4.4 1.4 Versicolor
67  5.6 3.0 4.5 1.5 Versicolor
68  5.8 2.7 4.1 1.0 Versicolor
69  6.2 2.2 4.5 1.5 Versicolor
70  5.6 2.5 3.9 1.1 Versicolor
71  5.9 3.2 4.8 1.8 Versicolor
72  6.1 2.8 4.0 1.3 Versicolor
73  6.3 2.5 4.9 1.5 Versicolor
74  6.1 2.8 4.7 1.2 Versicolor
75  6.4 2.9 4.3 1.3 Versicolor
76  6.6 3.0 4.4 1.4 Versicolor
77  6.8 2.8 4.8 1.4 Versicolor
78  6.7 3.0 5.0 1.7 Versicolor
79  6.0 2.9 4.5 1.5 Versicolor
80  5.7 2.6 3.5 1.0 Versicolor
81  5.5 2.4 3.8 1.1 Versicolor
82  5.5 2.4 3.7 1.0 Versicolor
83  5.8 2.7 3.9 1.2 Versicolor
84  6.0 2.7 5.1 1.6 Versicolor
85  5.4 3.0 4.5 1.5 Versicolor
86  6.0 3.4 4.5 1.6 Versicolor
87  6.7 3.1 4.7 1.5 Versicolor
88  6.3 2.3 4.4 1.3 Versicolor
89  5.6 3.0 4.1 1.3 Versicolor
90  5.5 2.5 4.0 1.3 Versicolor
91  5.5 2.6 4.4 1.2 Versicolor
92  6.1 3.0 4.6 1.4 Versicolor
93  5.8 2.6 4.0 1.2 Versicolor
94  5.0 2.3 3.3 1.0 Versicolor
95  5.6 2.7 4.2 1.3 Versicolor
96  5.7 3.0 4.2 1.2 Versicolor
97  5.7 2.9 4.2 1.3 Versicolor
98  6.2 2.9 4.3 1.3 Versicolor
99  5.1 2.5 3.0 1.1 Versicolor
100 5.7 2.8 4.1 1.3 Versicolor
101 6.3 3.3 6.0 2.5  Virginica
102 5.8 2.7 5.1 1.9  Virginica
103 7.1 3.0 5.9 2.1  Virginica
104 6.3 2.9 5.6 1.8  Virginica
105 6.5 3.0 5.8 2.2  Virginica
106 7.6 3.0 6.6 2.1  Virginica
107 4.9 2.5 4.5 1.7  Virginica
108 7.3 2.9 6.3 1.8  Virginica
109 6.7 2.5 5.8 1.8  Virginica
110 7.2 3.6 6.1 2.5  Virginica
111 6.5 3.2 5.1 2.0  Virginica
112 6.4 2.7 5.3 1.9  Virginica
113 6.8 3.0 5.5 2.1  Virginica
114 5.7 2.5 5.0 2.0  Virginica
115 5.8 2.8 5.1 2.4  Virginica
116 6.4 3.2 5.3 2.3  Virginica
117 6.5 3.0 5.5 1.8  Virginica
118 7.7 3.8 6.7 2.2  Virginica
119 7.7 2.6 6.9 2.3  Virginica
120 6.0 2.2 5.0 1.5  Virginica
121 6.9 3.2 5.7 2.3  Virginica
122 5.6 2.8 4.9 2.0  Virginica
123 7.7 2.8 6.7 2.0  Virginica
124 6.3 2.7 4.9 1.8  Virginica
125 6.7 3.3 5.7 2.1  Virginica
126 7.2 3.2 6.0 1.8  Virginica
127 6.2 2.8 4.8 1.8  Virginica
128 6.1 3.0 4.9 1.8  Virginica
129 6.4 2.8 5.6 2.1  Virginica
130 7.2 3.0 5.8 1.6  Virginica
131 7.4 2.8 6.1 1.9  Virginica
132 7.9 3.8 6.4 2.0  Virginica
133 6.4 2.8 5.6 2.2  Virginica
134 6.3 2.8 5.1 1.5  Virginica
135 6.1 2.6 5.6 1.4  Virginica
136 7.7 3.0 6.1 2.3  Virginica
137 6.3 3.4 5.6 2.4  Virginica
138 6.4 3.1 5.5 1.8  Virginica
139 6.0 3.0 4.8 1.8  Virginica
140 6.9 3.1 5.4 2.1  Virginica
141 6.7 3.1 5.6 2.4  Virginica
142 6.9 3.1 5.1 2.3  Virginica
143 5.8 2.7 5.1 1.9  Virginica
144 6.8 3.2 5.9 2.3  Virginica
145 6.7 3.3 5.7 2.5  Virginica
146 6.7 3.0 5.2 2.3  Virginica
147 6.3 2.5 5.0 1.9  Virginica
148 6.5 3.0 5.2 2.0  Virginica
149 6.2 3.4 5.4 2.3  Virginica
150 5.9 3.0 5.1 1.8  Virginica
       V1              V2              V3              V4       
 Min.   :4.300   Min.   :2.000   Min.   :1.000   Min.   :0.100  
 1st Qu.:5.100   1st Qu.:2.800   1st Qu.:1.600   1st Qu.:0.300  
 Median :5.800   Median :3.000   Median :4.350   Median :1.300  
 Mean   :5.843   Mean   :3.057   Mean   :3.758   Mean   :1.199  
 3rd Qu.:6.400   3rd Qu.:3.300   3rd Qu.:5.100   3rd Qu.:1.800  
 Max.   :7.900   Max.   :4.400   Max.   :6.900   Max.   :2.500  
         V5     
 Length   :150  
 N.unique :  3  
 N.blank  :  0  
 Min.nchar:  6  
 Max.nchar: 10  
                
[1] "Sepal.Length" "Sepal.Width"  "Petal.Length" "Petal.Width"  "Species"     
  Sepal.Length    Sepal.Width     Petal.Length    Petal.Width   
 Min.   :4.300   Min.   :2.000   Min.   :1.000   Min.   :0.100  
 1st Qu.:5.100   1st Qu.:2.800   1st Qu.:1.600   1st Qu.:0.300  
 Median :5.800   Median :3.000   Median :4.350   Median :1.300  
 Mean   :5.843   Mean   :3.057   Mean   :3.758   Mean   :1.199  
 3rd Qu.:6.400   3rd Qu.:3.300   3rd Qu.:5.100   3rd Qu.:1.800  
 Max.   :7.900   Max.   :4.400   Max.   :6.900   Max.   :2.500  
      Species   
 Length   :150  
 N.unique :  3  
 N.blank  :  0  
 Min.nchar:  6  
 Max.nchar: 10  
                
[1] "Sepal.Length" "Sepal.Width"  "Petal.Length" "Petal.Width"  "Species"     
  [1] "1"   "2"   "3"   "4"   "5"   "6"   "7"   "8"   "9"   "10"  "11"  "12" 
 [13] "13"  "14"  "15"  "16"  "17"  "18"  "19"  "20"  "21"  "22"  "23"  "24" 
 [25] "25"  "26"  "27"  "28"  "29"  "30"  "31"  "32"  "33"  "34"  "35"  "36" 
 [37] "37"  "38"  "39"  "40"  "41"  "42"  "43"  "44"  "45"  "46"  "47"  "48" 
 [49] "49"  "50"  "51"  "52"  "53"  "54"  "55"  "56"  "57"  "58"  "59"  "60" 
 [61] "61"  "62"  "63"  "64"  "65"  "66"  "67"  "68"  "69"  "70"  "71"  "72" 
 [73] "73"  "74"  "75"  "76"  "77"  "78"  "79"  "80"  "81"  "82"  "83"  "84" 
 [85] "85"  "86"  "87"  "88"  "89"  "90"  "91"  "92"  "93"  "94"  "95"  "96" 
 [97] "97"  "98"  "99"  "100" "101" "102" "103" "104" "105" "106" "107" "108"
[109] "109" "110" "111" "112" "113" "114" "115" "116" "117" "118" "119" "120"
[121] "121" "122" "123" "124" "125" "126" "127" "128" "129" "130" "131" "132"
[133] "133" "134" "135" "136" "137" "138" "139" "140" "141" "142" "143" "144"
[145] "145" "146" "147" "148" "149" "150"

```

2026-10-20:

- Installed quarto
  - Maybe from now on for Code-included notes ill run it in quarto!
