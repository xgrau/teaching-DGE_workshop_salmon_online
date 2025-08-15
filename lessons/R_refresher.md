---
title: "R refresher"
author: "Meeta Mistry, Radhika Khetani, Mary Piper, Jihe Liu"
---

Approximate time: 45 minutes

## Learning Objectives

* Describe the various data types and data structures (including tibbles) used by R
* Use functions in R and describe how to get help with arguments
* Describe how to install and use packages in R
* Use the pipe (%>%) from the dplyr package
* Describe the syntax used by ggplot2 for making plots

## Setting up

1. Let’s create a new project directory for this review:
  
    - Create a new project called `R_refresher`
    - Create a new R script called `reviewing_R.R`
    - Create the following folders in the project directory - `data`, `figures`
    - Download a counts file to the `data` folder by [right-clicking here](https://github.com/hbctraining/DGE_workshop_salmon/blob/master/data/raw_counts_mouseKO.csv?raw=true)

2. Now that we have our directory structure setup, let's load our libraries and read in our data:

    - Load the `tidyverse` library
    - Use `read.csv()` to read in the downloaded file and save it in the object/variable `counts`
      - What is the syntax for a function?
      - How do we get help for using a function?
    - What is the data structure of `counts`?
      - What main data structures are available in R?
    - What are the data types of the columns?
      - What data types are available in R?
      
## Creating vectors/factors and dataframes

3. We are performing RNA-Seq on cancer samples with genotypes of p53 wildtype (WT) and knock-down (KO). You have 8 samples total, with 4 replicates per genotype. Write the R code you would use to construct your metadata table as described below.  

     - Create the vectors/factors for each column (Hint: you can type out each vector/factor, or if you want the process go faster try exploring the `rep()` function).
     - Put them together into a dataframe called `meta`.
     - Use the `rownames()` function to assign row names to the dataframe (Hint: you can type out the row names as a vector, or if you want the process go faster try exploring the `paste0()` function).
     
    Your finished metadata table should have information for the variables `sex`, `stage`, `genotype`, and `myc` levels: 

    | |sex	| stage	| genotype	| myc |
    |:--:|:--: | :--:	| :------:	| :--: |
    |KO1 |	M	|1	|KO	|23|
    |KO2|	F	|2	|KO	|4|
    |KO3	|M	|2	|KO	|45|
    |KO4	|F	|1	|KO	|90|
    |WT1|	M	|2	|WT	|34|
    |WT2|	F|	1|	WT|	35|
    |WT3|	M|	1|	WT|	9|
    |WT4|	F|	2|	WT|	10|
  
## Exploring data

Now that we have created our metadata data frame, it's often a good idea to get some descriptive statistics about the data before performing any analyses. 

  - Summarize the contents of the `meta` object, how many data types are represented?
  - Check that the row names in the `meta` data frame are identical to the column names in `counts` (content and order).
  - Convert the existing `stage` column into a factor data type

## Extracting data

4. Using the `meta` data frame created in the previous question, perform the following exercises (questions **DO NOT** build upon each other):

     - return only the `genotype` and `sex` columns using `[]`:
     - return the `genotype` values for samples 1, 7, and 8 using `[]`:
     - use `filter()` to return all data for those samples with genotype `WT`:
     - use `filter()`/`select()`to return only the `stage` and `genotype` columns for those samples with `myc` > 50:
     - add a column called `pre_treatment` to the beginning of the dataframe with the values T, F, T, F, T, F, T, F 
        - why might this design be problematic?
     - Using `%>%` create a tibble of the `meta` object and call it `meta_tb` (make sure you don't lose the rownames!)
     - change the names of the columns to: "A", "B", "C", "D", "E":
     
## Visualizing data

5. Often it is easier to see the patterns or nature of our data when we explore it visually with a variety of graphics. Let's use ggplot2 to explore differences in the expression of the Myc gene based on genotype.

     - Plot a boxplot of the expression of Myc for the KO and WT samples using `theme_minimal()` and give the plot new axes names and a centered title.

## Preparing for downstream analysis tools

6. Many different statistical tools or analytical packages expect all data needed as input to be in the structure of a list. Let's create a list of our count and metadata in preparation for a downstream analysis.

    - Create a list called `project1` with the `meta` and `counts` objects, as well as a new vector with all the sample names extracted from one of the 2 data frames.


[Rscript with answers](https://hbctraining.github.io/Intro-to-DGE/exercises/refresher_answers.R)
