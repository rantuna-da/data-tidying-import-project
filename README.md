---

---

# data-tidying-import-project

# Project instructions

> [!IMPORTANT]
>
> ### 

> This is the final project for course 2: data tidying and importing.
> This will not be graded, and is intended to provide you with the
> opportunity to test the skills you’ve acquired throughout the course
> in a less structured environment. This project is also structured for
> you to host on a webpage and link as proof of work on your resume or
> CV.
>
> Hints to answer the research questions can be found Hints section. You
> are challanged not to use these hints unless needed.
>
> A short self rubric can be found at the end of the README in the
> Rubric section to help the self-assessment of your project. Do not
> expand the rubric items until you have finished a draft of your
> project.
>
> ## Before you start

Please complete the following steps before getting started if you have
not downloaded and configured Git. If you have already completed these
steps from course 1, please clone this repo and skip to the Instructions
section.

### Download Git

Note, if you are on Windows or Linux, you will need to install Git. If
you do not have git installed, please do so:

Windows -\> <https://git-scm.com/download/win>

Linux -\> <https://git-scm.com/download/linux>

### Configure git with RStudio

In the console, run the following:

``` r
install.packages("usethis")

usethis::use_git_config(
  user.name = "Your name", 
  user.email = "Email associated with your GitHub account"
 )
```

Please make sure that you replace "YourName" with your actual name, and
"Email associated with your GitHub account" with your email used for
your GitHub account.

### Create and authenticate your personal access token

In the console, run the following to geneate your personal access token
(PAT)

``` r
usethis::create_github_token()
```

Next, run the following and paste your PAT in:

``` r
gitcreds::gitcreds_set()
```

### Getting started

Once you restart R, you will be able to clone this project repository
and get working! To clone this project: - Click the green code button on
the repo - Copy the HTTPS - Open a new project in RStudio - Click
version control and then Git - Paste the copied HTTPS in the Repository
URL box. - Name the project directory - Browse and select where this
project will be saved - Click create project!

## Instructions

This final project consists of an exploratory data analysis and write up
of results you discover. The data sets you will be working with can be
found in the data folder. Your write up, in index.qmd, will explore (at
least) two questions.

## Description

**Inflation in the US**

<img src="images/inflation.png" align="right" width="300" height="180"/>

The Organisation for Economic Co-operation and Development defines
inflation as follows:

> Inflation is a rise in the general level of prices of goods and
> services that households acquire for the purpose of consumption in an
> economy over a period of time.
>
> The main measure of inflation is the annual inflation rate which is
> the movement of the Consumer Price Index (CPI) from one month/period
> to the same month/period of the previous year expressed as percentage
> over time.
>
> Source: [OECD CPI
> FAQ](https://www.oecd.org/sdd/prices-ppp/consumerpriceindices-frequentlyaskedquestionsfaqs.htm#1)

CPI is broken down into 12 divisions such as food, housing, health, etc.

The data you will need to explore US inflation are spread across two
files:

-   `us-inflation.csv`: Annual inflation rate for the US for 12 CPI
    divisions. Each division is identified by an ID number.
-   `cpi-divisions.xlsx`: A "lookup table" of CPI division ID numbers
    and their descriptions.

A data table for each dataset can be seen below:

`us-inflation`

| variable | description |
|-----------------|-------------------------------------------------------|
| `country` | location data; all values "United States" |
| `cpi_division_id` | numerical value to represent cpi division |
| `2011` | annual inflation percentage for the year 2011 by cpi division |
| `2012` | annual inflation percentage for the year 2012 by cpi division |
| `...` | ... |
| `2021` | annual inflation percentage for the year 2021 by cpi division |

`cpi-divisions.xlsx`

| variable      | description                               |
|---------------|-------------------------------------------|
| `id`          | numerical value to represent cpi division |
| `description` | description of the cpi value              |

## Research Questions

You are tasked to use these data to produce the following:

1)  Calculate the minimum and maximum annuel inflation percentage for
    each cpi division.

2)  Recreate a plot of annual inflation vs. year for these divisions.
    Then, in a few sentences, describe the patterns you observe in the
    plot, particularly focusing on anything you find surprising or not
    surprising, based on your knowledge (or lack thereof) of inflation
    rates in the US over the last decade.

    <img src="images/final-plot.png" align="center"/>

> [!IMPORTANT]
>
> ### 
>
> <img src="images/github.png" data-fig-align="left" width="25" height="25"/> -
> **Version control with GitHub** <br> This project also provides you
> with the opportunity to practice using version control, often expected
> to be used in a real-world context. We challenge you to **Render**;
> **Commit**; and **Push** after each visualization or summary
> statistics you create. If you are working on a project with more than
> one contributor, make sure that you **Pull** before making any
> progress to ensure your project matches up with the project
> repository.

## Displaying code

Depending on the purpose of the project, it may be advantageous to
either show or hide all of your code in your rendered document. To hide
all of your code, set `echo: false` in your YAML. If you want to display
your code, set `echo: true`.

## Citations

When working on your project, you may want to include outside sources.
When doing so, we need to make sure these sources are properly cited. In
order to do so, we need to create a .bib file and specify it in your
index.qmd's YAML heading. Your project files include a references.bib
txt file. This is where you will put bibtex entries. An example of an
entry to be referenced can be seen below:

```         
@article{Cetinkaya2020,
    title        = {A Fresh Look at Introductory Data Science},
    author       = {Cetinkaya, Mine and Ellison, Victoria},
    year         = 2020,
    month        = {08},
    journal      = {Journal of Statistics Education},
    volume       = 29,
    pages        = {1--27},
    doi          = {10.1080/10691898.2020.1804497}
}
```

In this entry above, `Cetinkaya2020` is the citation identifier. The
default way to cite an entry in your text is with this syntax:
[@citation-identifier].

To automatically generate a references section with your entries, the
path to the .bib file needs to be specified in your YAML with
bibliography: references.bib. This has been done for you.

## Hints

<details>

<summary>RQ1 Hint (Calculation)</summary>

The way the data are currently set up, it is very difficult to operate
row wise and answer the research question. We can use what we've learned
about pivoting data to get these data in a more workable format!

</details>

<details>

<summary>RQ2 Hint (Reading in data)</summary>

The top of the cpi-divisions dataset has a note from the researcher. We
don't want to include this in the data set. See
<https://readxl.tidyverse.org/reference/read_excel.html> for how to skip
lines when reading in data from excel. Skip the first line.

</details>

<details>

<summary>RQ2 Hint (Joining)</summary>

Start by using your new dataset from question 1 and joining it with the
cpi-divisions dataset. Think critically about what variable is the same
across both datasets, and use this as the "key".

</details>

<details>

<summary>RQ2 Hint (Subset CPIs)</summary>

To filter the joined dataset by only the IDs of CPI divisions in the
final plot, create a vector using `c`. Then filter your joined data set
by using the `filter()` function and the `%in%` operator.

</details>

<details>

<summary>RQ2 Hint (Legend)</summary>

If your legend has labels that are too long, you can try moving the
legend to the bottom and stack the labels vertically. Hint: The
legend.position and legend.direction arguments of the theme() functions
will be useful.

```         
ggplot(...) +
  ... +
  theme(
    legend.position = "bottom", 
    legend.direction = "vertical"
  )
```

</details>

## Rubric

<details>

<summary>Self rubric</summary>

-   Check your calculations: For id 1, minimum annual inflation is equal
    to -1.32; max is equal to 4.80 For id 2, minimum annual inflation is
    equal to 1.68; max is equal to 4.46 etc.

-   Self assess the graph you made compared to the graph you are trying
    to recreate. Take note of details such as: Title and subtitle Axes
    labels Legend position Color scheme Categories of cpi division

    </details>

## Challenge

Using these data, come up with a third research question, add it to your
written report, and investigate!
