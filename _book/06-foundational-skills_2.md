
# Foundational Skills {#c06}

## Chapter Overview

This chapter is designed to give you the skills and knowledge necessary to *get started* in any of the walk through chapters. 
Our goal is to get you working with R using the RStudio *I*ntegrated *D*evelopment *E*nvironment (IDE) through a series of applied examples. 
If you have not yet installed R and/or RStudio, please go through the steps outlined in Chapter 05 before beginning this chapter.

Please note that this chapter is not intended to be a full and complete introduction to programming with R, nor for using R for data science. 
There are many excellent resources available which provide this kind of instruction, and we've listed them for you in Chapter 17, [Additional Resources].

## Foundational Skills Framework

No two data science projects are the same, and rather than be overly prescriptive, this chapter errs on the side of creating a general framework for you to use as a home base as you work through this text. 
The four basic concepts we will use to build our framework are:

  - **Projects**
  - **Packages**
  - **Functions**
  - **Data**

### Projects

Within RStudio we set up a **Project**. 
This is the home for all of the files, images, reports, and code that we'll create for a single project. 

We use Projects because they create a self-contained folder for a given analysis
in R. 
This means that if you want to share your Project with a colleague they will not have to reset file paths (or even know anything about file paths!) in order to re-run your analysis.

And even if the only person you ever collaborate with is a future version of yourself, using a Project for each of your analyses will mean that you can move the Project folder around on your computer, or even move it to a new computer, and remain confident that the analysis will run in the future (at least in terms of file path structures).
#### Setting up your Project

**How do I create a Project?**  
Creating a Project is one of the first steps in working on an R-based data science project in RStudio. 
To create a Project you will need to be in RStudio.

From within RStudio, follow these steps:

1.  Click on File
2.  Select New Project
3.  Choose New Directory
4.  Click on New Project
5.  Enter your Project's name in the box that says "Directory name." We
    recommend choosing a Project name that helps you to remember that this is a
    project that involves data science in education. Avoid using spaces in your
    Project name, and instead separate words with hyphens or underscore
    characters.
6.  Choose where to save your Project by clicking on "Browse" next to the box
    labeled "Create project as a subdirectory of: " If you are just using this
    to learn and to test out creating a Project, consider placing it in your
    downloads or another temporary directory so that you remember to remove it
    later.
7.  Click "Create Project"

We should point out that it is not *necessary* to create a Project for your work, although we _strongly_ recommend it, as when it is coupled with the {here} package, will set you up with an easy to use workflow. 
However if you do not create a Project, you can always check where your working directory is by running `getwd()`. 
You can then change your working directory manually, by running `setwd()` and providing your file path name as an argument.

### The {here} package
_We don't use the {here} package, do we?_

We've talked about what Projects are and why you should use them, but what really makes Projects in RStudio shine is the use of the `here()` function from the {here} package.
What `here()` does is eliminate the need for you to do what's called "hard-coding" your file path. 
For example, if we had loaded the data using the file path on one of our individual computers, it would be difficult for someone to open our folders on _their_ computer and re-run the analysis because they do not have the same file structure.
What `here()` does is tell R that the file structure starts at the Project-level, and so every subsequent call starts at the Project-level, and allows you to navigate throughout each of the folders and files within a given Project.

### Packages
<!-- IMPROVE THIS --> 
"Packages" are shareable collections of R code that provide functions (i.e., a command to perform a specific task), data, and documentation. 
Packages increase the functionality of R by providing access to additional functions to suit a variety of needs, thereby expanding on base R.

If an R user feels that their package would be of benefit to a broad audience, they may choose to submit their package to [CRAN](https://cran.r-project.org/), the **C**omprehensive **R** **A**rchive **N**etwork.
Most of the packages we'll be working with in this book are available on CRAN, which means that we can install them using the `install.packages()` function, as we did above.  

The process of submitting a package and having it published through CRAN is beyond the scope of this book, and it's important to point out that you - yes, you! - can create a package that you use all for yourself, share with colleagues, or submit to CRAN. 
Packages do not need to be submit to CRAN to be used by the public, and many packages are available directly from their respective developers via GitHub.  

**The tidyverse, a package of packages**
The {tidyverse} is a single package that contains additional packages, and within each of those individual packages are a set of functions. 
The {tidyverse} is an excellent tool that has a cohesive syntax across all functions, and the packages allow you do to the bulk of an analytical workflow. 
As of this writing, the {tidyverse} is the only known package of packages.  

## Installing and Loading a package

*Installing a package*

If you read Chapter 05, you might have noticed at the very end that we both installed and loaded packages, but didn't talk too much about what we were doing. 
We'll get into more detail on installing and loading packages now!

While it is entirely possible to do all of your work in R without ever using a package, we do not recommend that approach due to the wealth of packages available that help reduce both the learning curve associated with R, as well as the amount of time spent on any given analytical project.  

In order to access the functions within a package, you must first install the package on your computer. 
If the package is on CRAN we can install it by running the following code:  


```r
# template for installing a package
install.packages("package_name")

# example of installing a package
install.packages("dplyr")
```

You can also navigate to the Packages pane, click "Install", and then search for and Install one or more packages. 

!["Image of the Packages pane, which is found in the bottom right corder of the RStudio IDE, along with the Files, Plots, Help, and Viewer panes"](man/figures/packages_pane.png)

*Loading a package*

Once a package is installed on your computer you do not have to re-install it in order to use the functions in the package, however you need to give R instructions telling it where to look for the functions in order to access the functions in the package.

If you know that you'll be using a package's functions multiple times in an R script (a file ending in `.R`), you can load the package into your R environment using `library()`.
Loading a package into our R enviroment signals to R that we would like to use any of the functions available to us in that package.

We load a package, like the {dplyr} package [@R-dplyr] below, using the following code:  


```r
# template for loading a package
library(package_name)  

# example of loading a package
library(dplyr)
```

We only have to install a package once, but to use it, we have to load it each time we start a new R session.

> A package is a like a book, a library is like a library; you use library() to check a package out of the library.
> - Hadley Wickham, Chief Scientist, RStudio

Sometimes you'll see `require()` instead of `library()`. 
We strongly advocate for the use of `library()`, as it forces R to load the package, and if the package is not installed or there are issues with the package, will give you an error message. 
`require()` on the other hand will not give an error if the package is not available or if there are issues with the package. 
Using `library()` will help to eliminate sources of confusion later on.  

### How to Find a Package

As you begin your R learning journey, the bulk of the packages that you will need to use are either already included when you install R, or available on CRAN. 
[CRAN TaskViews]("https://cran.r-project.org/web/views/") is one of the best resources for seeing what packages are available and might be relevant to your work.
Other great resources to learn about various R packages are through Twitter (following the #rstats hashtag) as well as through Google searches.
As R has grown in popularity, Google has gotten significantly better at returning R-related results.

### How to Learn More About a Package

Sometimes when you look up a package, you're able to pull the function that you need and continue on your way.
Other times you may need (or want!) to learn more about a specific package. 
Packages on CRAN all come with something called a "vignette," which is a worked example using various functions from within the package. 
You can access a package's vignette(s) on CRAN TaskViews:

Package authors may also publish vignettes or blog posts about their package, and other R users may _also_ publish tutorials about a specific package.
You may also find yourself on GitHub looking at information for a package - more often than not the README file will have good information for getting started with a package.



### Functions

**Recognizing a Function**

Functions in R can be spotted by a word followed by a set of parentheses, like so: `word()`

The word (or set of words) represent the name of the function, and the parentheses are where we can provide arguments to a function, if arguments are needed for the function to run. 
Many functions in R packages do not _require_ arguments, and will use a set of default arguments unless you provide something different from the default.

### The Relationship Between Packages and Functions
**From the outside in**  
Packages are a collection of functions, and most packages are designed for: a specific data set, a specific field, and/or a specific set of tasks. 
Functions are individual components within a package, and functions are what we use to interact with our data.  

**From the inside out**  
To put it another way, an R user might write a series of functions that they find themselves needing to use repeatedly in a variety of projects. 
Instead of re-writing (or copying and pasting) the functions each time they need to use them, an R user can collect all of these individual functions inside a package. 
The R user can then load the package any time that they want to use the functions, using a single line of code instead of tens to tens of thousands of lines of code for each function.  

### Verb-Based Functions
Another pattern you may have picked up on is that every function is a verb.
That is, the name of the function is telling us what the function is going to do!
This is common both within the Tidyverse as well as in other packages.

### When Functions Need Arguments and When They Don't
You also may have noticed that some of our functions needed arguments, that is, some kind of additional information provided inside the parentheses.
There are not any hard and fast rules about when a function needs an argument (or series of arguments), however if you are having trouble running your code, first check for typos, then check the help documentation to see if you can provide arguments to more clearly direct R as to what to do.

### Functions within Functions
One of the (many!) cool things about R is that we can nest our functions.
When we nest our functions, R will read the functions from the innermost function to the outermost.
We saw this both in the section of code above that used `arrange(desc(n))`, as well as when we imported data using `read_csv(here())`. 



### Writing Your Own Functions
As you work in R more and more, you may find yourself copying and pasting the same lines of code, and then making small modifications. 
This is perfectly fine while you're learning, but eventually you're going to come across a large enough dataset that's going to take you a couple hours to type out by hand (and increase the opportunity to introduce errors!).
This is when you _know_ you need to write a function.
_(We could argue that you need functions **much** sooner! For example, a general premise in programming is DRY, or **D**on't **R**epeat **Y**ourself._
_What this translates to is the idea that once you find yourself copying and pasting code for the third time, it's time to write a function!)_

Functions are reusable pieces of code that you can write and use over and over again. 
You might write a function for a specific script, or you might find yourself using a function across multiple scripts (at which point you might want to consider creating a package!) 

We'll cover the very basics of writing a function, but would strongly suggest you check out [RESOURCE ONE](link) and [RESOURCE TWO](link) for more information and practice. 

The template for writing a function is: 


```r
name_of_function <- function(argument_1, argument_2, argument_n){
    code_that_does_something
    code_that_does_something_else
}
```

Functions can be as simple or as complex as you would like.
For example, if we wanted to create a function that adds two numbers together, we would write: 


```r
# writing our function
# we've named the function "addition"
# and asked for two arguments, "number_1" and "number_2"
addition <- function(number_1, number_2) {
    number_1 + number_2
}

# using our function
# note that we provide each argument separated by commas
addition(number_1 = 3, number_2 = 1)
```

```
#> [1] 4
```

```r
addition(0.921, 12.01)
```

```
#> [1] 12.9
```

```r
addition(62, 34)
```

```
#> [1] 96
```

What happens if we only provide one argument?
What happens if we provide more than two arguments?

You'll encounter several (more advanced) functions that we'll write together in various walkthroughs in this book!


### Data

We have **data** that we bring into a Project within RStudio. 
RStudio is the interface that we use to access and manipulate R. 
Sometimes you'll hear RStudio referred to as an "eye-dee-eee", "IDE", or "Interactive Development Environment." 
We use an IDE - in this case RStudio, although you could use others - because it adds features that make our analytical lives a little (and sometimes a lot!) easier.
You're likely using this text because you have some data that you'd like to do something with, and you'd like to try doing said thing using R. 
The framework we'll use pulls data directly from the {dataedu} package, however there are a multitude of file types that data can be stored in. 
We've provided additional resources for loading data from Excel, SAV, and Google Sheets in the [Technical Appendix A] at the end of this chapter.

While it is possible to connect directly to a database from within R, we do not cover those skills in this text. 
For those curious as to how to accomplish this, we recommend starting with the [Databases using R](https://db.rstudio.com/) resource from RStudio.

### Data Types

There are different types of data within R. 
When you loaded the Massachusetts Public Schools data from 2017, you likely saw a series of messages like this:

[IMG of import message]

This message is telling you how R decided to "code" each column, as you can only have one data type per column in R.
We can see that the default is to code everything as a double (a number) where it says `.default = col_double().
Where columns were coded as something _other_ than double, we see `col_character()` (text that has at least one non-numeric character), `col_number()` (for our purposes a number, and analogous to `col_double()`), and `col_logical()` (TRUE or FALSE). 

When `read_csv()` reads through the first 1,000 rows of data, it uses what it encounters to make a best guess as to what type of data is in the column.
If R sees 990 rows of numbers, but 10 rows of numbers mixed with letters, R will _coerce_ the data in the column into character data. 
This means that `193` and `192A` are both seen as _text_.
One of the (many) implications of this is that you can no longer do mathematical operations on `193` when it's been coerced into a character string. 

Not all is lost! 
There are methods for safely coercing your data into the correct format, and we'll cover a handful throughout this text. 
If you're looking for more in-depth information on data types and coercion rules, we recommend both [Hands-On Programming with R](https://rstudio-education.github.io/hopr/) @hopr and [Advanced R](https://adv-r.hadley.nz/) @wickham2019advr.


## Introduction to Help Documentation

Very few - if any - people in the world know everything there is to know about R. 
This means that we all need to look things up, sometimes every few minutes!
Thankfully there are some excellent built-in resources that we can leverage as we use R.

From within RStudio we can access the `Help` documentation by using `?` or `??` in the console. 
For example, if I wanted to look up information on the `data()` function, I can type `?data` or `?data()` next to the carat `>` in the Console and hit `Enter`. 
Try this now, and you should see the `Help` panel on the bottom right side of your RStudio environment populate with documentation on the `data()` function.

This works because the `data()` function is part of something called **base R** - that is, all of the functions included with R when you first install it. 
R also comes with packages pre-installed, however as you use R throughout this book, we'll be asking you to install additional packages. 
These additional packages extend the functionality of base R and its pre-installed packages by providing us with access to new functions. 
This means that instead of writing a function to do a common data analysis task, such as creating a new variable out of existing variables, someone has written that function and made it available for you to use (almost always at no charge! Don't worry - all of the packages
we'll be using in this text are considered **O**pen **S**ource **S**oftware, and
you will not have to purchase anything to complete any of the exercises or
walkthroughs in this text.)

One of the functions that can accomplish the task of creating a new variable out of existing variables is called `mutate()`. 
What happens when you type `?mutate` (or `?mutate()`) into the Console and hit `Enter`?

We've gotten one of our first error messages!

!["Error message when running ?mutate reads: No documentation for 'mutate' in specified packages and libraries: you could try '??mutate'"](man/figures/mutate_error.png)

This is a fantastic error message because not only has it told us that something is wrong (there is no documentation for `mutate`), it tells us what we should try to do to solve the error. 
Let's see what happens when we follow the error
message instructions by typing `??mutate` (or `??mutate()`) into the Console and hitting `Enter`. 
What do you see?

## Steps for working through new and unfamiliar content

A sure sign of a great educator is the ability to ask questions. 
Asking the right questions at the right time of the learners in your classroom can facilitate understanding, uncover misconceptions, and indicate whether or not learners have mastered the material.

However, when you’re learning on your own you have to simultaneously fill the roles of both learner and educator, and not only know both how and when to ask yourself questions, but also answer your questions, evaluate your answers, and redirect your learning path as you progress.

This section is intended to give you a series of steps you can use as you encounter new and unfamiliar content both in reading this book as well as in your broader data science learning endeavors.
For this section we'll use the example of encountering a function for the first time, but you can use these steps with any new piece of information that you encounter!
We'll cover functions in greater depth in subsequent chapters, but for now all you need to know about a function is that it's a reusable piece of code that allows us to consistently repeat a programming task. 

**Activate prior knowledge**
You've been reading through a tutorial and have come across the `coalesce()` function in the vignette for the [{janitor} function]("https://github.com/sfirke/janitor):


```r
library(tidyverse)
library(janitor)

roster <- roster_raw %>% 
    clean_names() %>% 
    remove_empty(c("rows", "cols")) %>% 
    mutate(hire_date = excel_numeric_to_date(hire_date),
           cert = coalesce(certification, certification_1)) %>% 
    select(-certification, -certification_1)
```

_Note: you aren't expected to know what the chunk of code that you've just read does, but by the time you've finished this book you'll be able to run and understand everything in the code example!_

Take a moment to think through the following questions:

* What does the word "coalesce" mean?
* Have you ever seen the `coalesce()` function before? If so, in what context?

**Look for context clues**

* Read a couple of lines of code both above and below where the `coalesce()` function appears - are there any clues as to what this function might do?

**Check the docs**

* What information is available in the Help documentation?
* Are there any examples from the Help documentation that seem similar to what you're trying to accomplish? For example, this seems somewhat related to what we're trying to do:

![Example from the `coalesce()` Help documentation](images/coalesce_help_doc.png)

**Find the limits**
Work through examples in the Help documentation (or examples that you've found online) and test the limits.
Testing the limits is a way of understanding the code by seeing how it handles different situations.
Ultimately what you're doing is recognizing a pattern, developing a hypothesis, and testing whether or not that hypothesis is true.
Some methods for testing the limits include:

* Substituting obviously larger (or smaller values)
* Substituting different data types
* What happens if you introduce `NA` values?
* Is the order of values important?

**Test (and refine) your understanding**
Take a moment to think through whether or not you could explain what you've just learned to someone else.
Imagine the questions that they might ask of you, and try to answer them.
If you can't answer them, dig deeper into the documentation, online forums, or even in testing your own knowledge, until you feel like you can! 

You won't necessarily have the time (or interest!) in doing this for each new or unfamiliar piece of content that you come across, but we hope that this provides you with a starting framework for furthering your understanding when you _do_ come across content that you want to explore a bit more in-depth! 


## CODE WALKTHROUGH
Pay attention to when asking you to run code in your `.R` script vs. the console. 
Won't break anything if make a mistake, but if you get lost or confused, check this first. 
- Set up a Project in RStudio
- Create a new `.R` script and save it as "chapter_06_walkthrough"


You can see what the available arguments are for a given function by using the help documentation.

What are the arguments for `library()`?

### Run This Code

Take a few minutes to type out and run each of the following lines of code in an `.R` script, one by one, and notice what you see happening in the Console after you run each line.  


```r
# Installing packages
install.packages("tidyverse")
install.packages("janitor")
install.packages("skimr")
```


```r
# Setting up your environment
library(tidyverse)
library(janitor)
library(skimr)
```

Based on what we've covered so far in this chapter, what did running the above lines of code accomplish?
How do you know?

### Function Conflicts between Packages

In your Console you may have noticed the following message: 

!["List of attached packages and associated conflicts when loading the Tidyverse"](man/figures/tv_conflicts.png) 

This isn't error, but rather some important information that we need to consider!
When we first open R (via RStudio) we are working with base R -- that is, everything that comes with R along with a (relative) handful of pre-installed packages. 
These are packages and functions that exist in R that we have access to without needing to first load the package using `library()`. 

If you would like to see what functions are available to you in base R, you can run `library(help = "base")` in the Console.

If you would like to see the packages that came pre-installed with R, you can run `installed.packages()[ installed.packages()[,"Priority"] %in% "base", c("Package", "Priority")]` in the Console.

Additionally, if you would like to see a list of _all_ of the packages that have been installed (both pre-installed with base R as well as those that you have installed), you can run `rownames(installed.packages())` in the Console.

However because of the broad array of packages that have been created for use in R, it's not uncommon for two (or more!) packages to have functions with the same name.
What this message is telling us then is that if we use the `filter()` function, R will use the `filter()` function from the {dplyr} package (a package within the {tidyverse}) rather than the `filter()` function from within the {stats} package (one of the packages that accompanies base R). 

How can we use the Help documentation to explore how the two functions might differ?

R will give precedence the most recently loaded package.

What happens if we want to use the `filter()` function from the {stats} package _and_ the `filter()` function from the {dplyr} package in the same R session? 

One solution would be to reload the library you want to use each time you want to change the package you're using the `filter()` function from.
But this can be tricky for several reasons: 
- It's best practice to keep your `library()` calls at the very top of your R script, so re-loading a package using `library()` throughout your script can clutter things and cause you headaches down the road
- If you scroll to the top of your script and reload the packages as you need them, it can be difficult to keep track of which one you recently loaded.

Instead there's an easier way to handle this kind of problem.
When we have conflicting function names from different packages we can tell R which package we'd like to pull a function from by using `::`.
Using the example of the `filter()` function above, coupled with the examples in the Help documentation, we can specify which package to pull the `filter()` function using `::`, as outlined below: 

_Note: we haven't covered what any of this code does yet, but see what you can learn from running the code and using the Help documentation!_


```r
# using the filter() function from the stats package
x <- 1:100
stats::filter(x, rep(1, 3))

# using the filter() function from the dplyr package
starwars %>% 
    dplyr::filter(mass > 85)
```


### Installing the {dataedu} package using {devtools}
Here, we will show how to install the {dataedu} package that accompanies this book.

As of this writing, the {dataedu} package is not available on CRAN. 
This means we'll have to install the package using {devtools}. 
To do this you first have to install the {devtools} package, and then the {dataedu} package by running the following code either in your RStudio console or in a script (an .R file): 


```r
# install devtools
install.packages("devtools", repos = "http://cran.us.r-project.org")

# install the dataedu package
devtools::install_github("data-edu/dataedu")
```

From here we can load the {dataedu} package using the `library()` call, as follows:


```r
# load the dataedu package into our R environment
library(dataedu)
```

### Mass Installation of Packages

We strived to use packages that we use in our daily work when creating the walkthroughs in the book. Because we covered a variety of subjects, that means we used a lot of packages! As described in the Foundational Skills chapter, you can install the packages individually as they suit your needs. 

However, if you want to quickly get started and download all the packages at once, please use `install_dataedu()`.

``` r
dataedu::install_dataedu()
```

To see the packages used in the book, run:


```r
dataedu::dataedu_packages
```

```
#>  [1] "apaTables"   "caret"       "dummies"     "ggraph"      "here"       
#>  [6] "janitor"     "lme4"        "lubridate"   "performance" "readxl"     
#> [11] "rtweet"      "randomNames" "sjPlot"      "textdata"    "tidygraph"  
#> [16] "tidylog"     "tidyverse"   "tidytext"
```

**A special note on {tabulizer}:** One of the walkthroughs uses [tabulizer](https://github.com/ropensci/tabulizer), created by ROpenSci to read PDFs. {tabulizer} requires the installation of [RJava](https://cran.r-project.org/web/packages/rJava/index.html), which can be a tricky process on Mac computers. {tabulizer} is not included in `mass_install()` and we recommend reading through the notes on its Github repo if installing.



### Downloading and Accessing the Datasets Used in this Book

Throughout this book you'll see data accessed in a multitude of ways.
Sometimes we've pulled the data directly from a website, while other times we ask you to load the data from a `.csv` or `.xls` file.
We've also provided each of the datasets used in this book as `.rda` files that are accessible via the {dataedu} package [@R-dataedu].
More details about the {dataedu} package on be found [on GitHub](https://github.com/data-edu/dataedu) (https://github.com/data-edu/dataedu), however we'll walk through the basic steps here as well.

Once you've installed the {dataedu} package (described above), you can use the `install_dataedu()` function to download all of the packages we'll be using in this text. 
This step is optional, and you're welcome to install packages as you use them. 

To install all of the packages used in this text, run the following code in your RStudio console:


```r
# see which packages are used in the Data Science in Education Using R text
dataedu::dataedu_packages

# install all of the packages used in the Data Science in Education Using R text
dataedu::install_dataedu()
```
## Assigning Data to a Variable//Everything's An Object!
### Run this Code
<!-- write a mini-intro to prime learning: what will readers be able to do at the end of this section? -->
Take a few minutes to type out and run each of the following lines of code, one by one, and notice what you see happening in the Console after you run each line. 

_Note: although we provide all of the data sets used in this book in the `dataedu` package, we would strongly suggest [downloading the dataset from Kaggle](link) so that we can show you the true power of Projects in R._

```r
dataedu::ma_data_init

dataedu::ma_data_init -> my_data

my_data <- dataedu::ma_data_init
```

Each of the three code examples above look slightly different, but two of them do almost the exact same thing.
The first example provided loads the data into our R environment, but not in a format that's immediately useful to us.
The second and third examples read in the data and assign it to a variable,`my_data` and `ma_data_init` respectively.
In our Environment pane we can see how each of the data types has been brought into R, and even click on the table icon to get an interactive table
(The data set is rather large, so RStudio may lag slightly as you open the table and manipulate it.)

### The Assignment Operator
The second and third examples in the code chunk above are how you'll most commonly see things in R being saved to a variable.
When we save something to a variable, we do so using what's called an "assignment operator," which in R is either a left- or right-facing arrow (`<-` or `->`).
Writing the name of your variable followed by a left-facing arrow is currently the most common convention used in R, but it is also perfectly acceptable to use the right-facing arrow.

Intuitively the right-facing arrow may make more sense for those of us who work predemoninantly in languages that read left to right, as what we're essentially saying is "take this entire chunk of code and save it to this variable name." 
Regardless of which option you choose, both are different means to the same end.

## Reading Code and Writing Functions - THIS IS A BAD TITLE
<!-- Write mini-introductions for each code-through section -->
### Run This Code

Take a few minutes to type out and run each of the following lines of code, one by one, and notice what you see happening in the Console after you run each line.
If you'd like, practice commenting your code by noting what you see happening with each line of code that you run.

_Note: we have intentionally included errors in this chapter to help highlight concepts as well as introduce you to error messages early on!_


```r
# Exploring and manipulating your data
names(ma_data_init)

glimpse(ma_dat_init) 
glimpse(ma_data_init)
summary(ma_data_init)

glimpse(ma_data_init$Town)
summary(ma_data_init$Town)

glimpse(ma_data_init$AP_Test Takers)
glimpse(ma_data_init$`AP_Test Takers`)
summary(ma_data_init$`AP_Test Takers`)
```

What differences do you see between each line of code?
What changes in the output to the Console with each line of code that you run?

### Common Errors: Typos, Spaces, and Parentheses

There were two lines of code that resulted in errors, and both were due to one of the most common sources of error in programming - typos!
The first was `glimpse(ma_dat_init)`. 
This might be a tricky error to spot, because at first glance it might seem like nothing is wrong!
However we've left off the "a" in "data," which has caused problems with R.

R will do exactly as you tell it to do.
This means if you want to run a function on a data set, R will only run the function on the data sets that are available in its environment.
Looking at our Environment pane we can see that there is no data set called `ma_dat_init`, which is what R is trying to tell us with its error message of `Error in glimpse(ma_dat_init) : object 'ma_dat_init' not found`. 

The second error was with `glimpse(ma_data_init$AP_Test Takers)`.
What do you think the error is here? 

R is unhappy with the space in the file name, and doesn't know how to read the code. 
To get around this there are a couple of things we can do.
First, we could make sure that data column names never have spaces in them.
This is unlikely to be within our control, so a second option would be to use R to convert the column names upon import, before we start doing any exploration. 
Another method for dealing with it is to leave the column names as they are, but to use single backticks `` `` to surround the column header with spaces in it.

_Note: the single backtick key is usually in the top-left of your keyboard. It's common to try and use a set of single quotation marks `' '` instead of the actual backticks `` ``!_

### Closing your parentheses
Run the following code.
What happens?
How do we fix it?
Seeing the `+` sign in the Console
Fixing it by pressing `Esc`

### The `$` Operator

There are many ways to isolate and explore a single variable within your data set.
In this set of examples we used the `$` symbol.
The pattern for using the `$` symbol is `name_of_dataset$variable_in_dataset`.
It's important that the spelling, punctuation, and capitalization that you use in your code match what's in your data set, otherwise R will tell you that it can't find anything! 

## The Pipe Operator

The pipe operator `%>%` tends to throw R learners for a loop, until all of a sudden something clicks for them and they decide that they either love it or hate it.
We use the pipe operator throughout this text because we also heavily rely on use of the tidyverse. 
The {magrittr} package
{dplyr} and package dependencies 
"Correct" pipe length (careful - will need to stick to this throughout text)

_Note: As you progress in your R learning journey you will likely find that you need to move well beyond the Tidyverse for accomplishing your analytical goals - and that's OK!_
_We like the Tidyverse for teaching and learning because it relies on the same syntax across packages, so as you learn how to use functions within one package, you're learning the syntax for functions in other Tidyverse packages._  

It's worth taking a few moments to talk about the pipe operator and its package.
The pipe operator first appeared in the {magrittr} package, and is a play on a famous painting by the artist Magritte, who painted The Treachery of Images.
In these images he would paint an object, such as a pipe, and accompany it with the text "Ceci n'est pas une pipe," which is French for "This is not a pipe." 

<center>
![](./man/figures/pipe.png)
</center>

At the risk of spoiling a joke by over-explaining it, it's common in the R programming world to name a package by choosing a word that represents what the package does (or what the package is for) and either capitalizing the letter R if it appears in the package name, or adding an R to the end of the package ({dplyr}, {tidyr}, {stringr}, and even {purrr}).


### Run This Code
Take a few minutes to type out and run each of the following lines of code, one by one, and notice what you see happening in the Console after you run each line. 

```r
ma_data_init %>% 
    group_by(District Name) %>%  
    count()

ma_data_init %>% 
    group_by(`District Name`) %>% 
    count()  
    
ma_data_init %>% 
    group_by(`District Name`) %>% 
    count() %>% 
    filter(n > 10)

# ma_data_init %>% 
#     group_by(`District Name`) %>% 
#     count() %>% 
#     filter(n > 10) %>% 
#     arrange(desc(n)
```

### "Reading" Code
When you encounter new-to-you code, it's helpful to pause and read through the code to see if you can come up with a hypothesis as to what the code is trying to accomplish.
Doing this will help you not only understand code a bit better, but also help you spot errors more quickly when the code doesn't do what you thought it was going to do. 

The way that we would read the first chunk of code is:

> Take the `ma_data_init` data set _and then_ 
> **group** it **by** `District Name` _and then_ 
> **count** (the number of schools in a district) _and then_ 
> **filter** for Districts with more than 10 schools _and then_ 
> **arrange** the list of Districts and the number of schools in each District in descending order, based on the number of schools.

That's a mouthful! 
But there are a couple of consistent points to make regarding this paragraph.
Every time we see the pipe, we say "and then." 
This is because we're starting with our data set, `ma_data_init`, _and then_ doing one thing after another to it.
Because we're using the pipe operator between each function, R knows that all of our functions are being applied to the `ma_data_init` data set.
We do not need to call or refer to the `ma_data_init` data set each time.

When we link together functions using the pipe operator in this manner, we often refer to it as "chaining together functions."

## Assignment vs. Equality
<!-- mini-intro -->

### Run This Code 
Take a few minutes to read through the code before typing or running anything in R.
Try to guess what is happening in each code chunk by writing out a sentence for each line of code so that you have a small paragraph for each chunk of code.
Once you've done that, type out and run each of the following lines of code, one by one, and notice what you see happening in the Console after you run each line. 

```r
ma_data_init %>%
    group_by(`District Name`) %>%
    count() %>%
    filter(n > 10) %>%
    arrange(desc(n))

ma_data_init %>%
    group_by(`District Name`) %>%
    count() %>%
    filter(n = 10) 

ma_data_init %>%
    group_by(`District Name`) %>%
    count() %>%
    filter(n == 10) 

ma_data_init %>% 
    rename(district_name = `District Name`,
           grade = Grade) %>% 
    select(district_name, grade)
```

**Wait I thought you said that `<-` and `->` were the assignment operators?**

### The Difference Between `=` and `==` 
We talked earlier about using a left- or right-facing arrow to assign values or code to a variable, but we could also use an equals sign (`=`) to accomplish the same thing.
When R encounters an equal sign (`=`) it is almost always looking to create an object by assigning a value to a variable.
So when we saw `filter(n = 10)`, R didn't understand why we were trying to filter something we were naming, and told us so with an error message.

When we are looking to determine whether or not values are equal, we use a double equals sign (`==`), as we did in `filter(n == 10)`. 
When R sees a double equals sign (`==`) it is evaluating whether or not the value on the left is equivalent to the value on the right. 

## Basics of Names
Naming things is important! 
The more you use R the more you'll develop your own sense of how you prefer to name things, either as an organization or an individual programmer. 
But there are some hard and fast rules that R has about naming things, and we'll cover them in this section. 

### Run This Code
Take a few minutes to type out and run each of the following lines of code, one by one, and notice what you see happening in the Console after you run each line. 

```r
ma_data %>% 
    clean_names()

01_ma_data <- ma_data_init %>%  
    clean_names()

$_ma_data <- ma_data_init %>%  
    clean_names()

ma_data_01 <- ma_data_init %>% 
    clean_names()
```

As you saw in the above examples, R doesn't like it when you create a name that starts with a number or symbol.
In addition, R is going to squawk when you give it a name with a space in it.
<!--ELABORATE-->

## Conclusion

It would be impossible for us to cover _everything_ you can do with R in a single chapter of a book, but it is our hope that this chapter gives you a strong foundation from which to explore both subsequent chapters as well as additional R resources. 
In this chapter we've covered the concepts of Projects, packages, functions, and data, and also walked through foundational ideas, concepts, and skills related to doing data science in R.
It is our hope that...

## Technical Appendix A

Here, we show how to use data from a few other common sources - your data likely exists somewhere in the world. 
That is to say, somewhere besides a package.

## Using Functions to Import Data

You might be thinking that an Excel file is the first type of data that we would load, but there happens to be a format which you can open and edit in Excel that is even easier to use between Excel and R, as well as SPSS and other statistical software (like MPlus) and even other programming languages, like Python. That format is `.csv`, or a comma-separated-values file. 

The `.csv` file is useful because you can open it with Excel and save Excel files as `.csv` files. 
Additionally, and as its name indicates, a `.csv` file is rows of a spreadsheet with the columns separated by commas, so you can also view it in a text editor, like TextEdit for Macintosh. 
Not surprisingly, Google Sheets easily converts `.csv` files into a Sheet, and also easily saves Sheets as `.csv` files. 
However we would be remiss if we didn't point out that there is a package, {googlesheets4}, which can be used to read a Google Sheet directly into R.

For these reasons, we start with - and emphasize - reading `.csv` files. 

### Saving a File from the Web

You'll need to copy this URL:

`https://goo.gl/bUeMhV`

Here's what it resolves to (it's a `.csv` file):

`https://raw.githubusercontent.com/data-edu/data-science-in-education/master/data/pisaUSA15/stu-quest.csv`

This next chunk of code downloads the file to your working directory. 
Run this to download it so in the next step you can read it into R. 
As a note: There are ways to read the file directory (from the web) into R. 
Also, of course, you could do what the next (two) lines of code do manually: Feel free to open the file in your browser and to save it to your computer (you should be able to 'right' or 'control' click the page to save it as a text file with a `.csv` extension).


```r
student_responses_url <-
    "https://goo.gl/bUeMhV"

student_responses_file_name <-
    paste0(getwd(), "/data/student-responses-data.csv")

download.file(
    url = student_responses_url,
    destfile = student_responses_file_name)
```

It may take a few seconds to download as it's around 20 MB.

The process above involves many core data science ideas and ideas from programming/coding. 
We will walk through them step-by-step.

1. The *character string* `"https://goo.gl/wPmujv"` is being saved to an *object* called `student_responses_url`.


```r
student_responses_url <-
    "https://goo.gl/bUeMhV"
```

2. We concatenate your working directory file path to the desired file name for the `.csv` using a *function* called `paste0`. 
This is stored in another *object* called `student_reponses_file_name`. 
This creates a file name with a *file path* in your working directory and it saves the file in the folder that you are working in. 


```r
student_responses_file_name <-
    paste0(getwd(), "/data/student-responses-data.csv")
```

3. The `student_responses_url` *object* is passed to the `url` argument of the *function* called `download.file()` along with `student_responses_file_name`, which is passed to the `destfile` argument.

In short, the `download.file()` function needs to know
- where the file is coming from (which you tell it through the `url`) argument and
- where the file will be saved (which you tell it through the `destfile` argument).


```r
download.file(
    url = student_responses_url,
    destfile = student_responses_file_name)
```

Understanding how R is working in these terms can be helpful for troubleshooting and reaching out for help. 
It also helps you to use functions that you have never used before because you are familiar with how some functions work.

Now, in RStudio, you should see the downloaded file in the Files tab. 
This should be the case if you created a project with RStudio; if not, it should be whatever your working directory is set to. 
If the file is there, great. 
If things are *not* working, consider downloading the file in the manual way and then move it into the directory that the R Project you created it.

### Loading a `.csv` File

Okay, we're ready to go. 
The easiest way to read a `.csv` file is with the function `read_csv()` from the package `readr`, which is contained within the Tidyverse.

Let's load the tidyverse library:


```r
library(tidyverse) # so tidyverse packages can be used for analysis
```

You may have noticed the hash symbol after the code that says `library(tidyverse`)`. 
It reads `# so tidyverse packages can be used for analysis`. 
That is a comment and the code after it (but not before it) is not run (the code before it runs just like normal). 
Comments are useful for showing *why* a line of code does what it does. 

After loading the tidyverse packages, we can now load a file. 
We are going to call the data `student_responses`:


```r
# readr::write_csv(pisaUSA15::stu_quest, here::here("data", "pisaUSA15", "stu_quest.csv"))
student_responses <-
    read_csv("./data/student-responses-data.csv")
```

```
#> Parsed with column specification:
#> cols(
#>   .default = col_double(),
#>   CNT = col_character(),
#>   CYC = col_character(),
#>   NatCen = col_character(),
#>   STRATUM = col_character(),
#>   Option_Read = col_character(),
#>   Option_Math = col_character(),
#>   ST011D17TA = col_character(),
#>   ST011D18TA = col_character(),
#>   ST011D19TA = col_character(),
#>   ST124Q01TA = col_logical(),
#>   IC001Q01TA = col_logical(),
#>   IC001Q02TA = col_logical(),
#>   IC001Q03TA = col_logical(),
#>   IC001Q04TA = col_logical(),
#>   IC001Q05TA = col_logical(),
#>   IC001Q06TA = col_logical(),
#>   IC001Q07TA = col_logical(),
#>   IC001Q08TA = col_logical(),
#>   IC001Q09TA = col_logical(),
#>   IC001Q10TA = col_logical()
#>   # ... with 420 more columns
#> )
```

```
#> See spec(...) for full column specifications.
```

Since we loaded the data, we now want to look at it. 
We can type its name in the function `glimpse()` to print some information on the dataset (this code is not run here).


```r
glimpse(student_responses)
```

Woah, that's a big data frame (with a lot of variables with confusing names, to boot)!

Great job loading a file and printing it! 
We are now well on our way to carrying out analysis of our data.

### Saving Files

Using our data frame `student_responses`, we can save it as a `.csv` (for example) with the following function. The first argument, `student_reponses`, is the name of the object that you want to save. The second argument, `student-responses.csv`, what you want to call the saved dataset.


```r
write_csv(student_responses, "student-responses.csv")
```

That will save a `.csv` file entitled `student-responses.csv` in the working directory. If you want to save it to another directory, simply add the file path to the file, i.e. `path/to/student-responses.csv`. To save a file for SPSS, load the haven package and use `write_sav()`. There is not a function to save an Excel file, but you can save as a `.csv` and directly load it in Excel.

In Technical Appendix A (at the end of this chapter), we show how to access directly data from a few other sources: Excel, SPSS (via `.SAV` files), and Google Sheets.


### Loading Excel Files

You might be thinking that you can open the file in Excel and then save it as a `.csv`. 
This is generally a good idea. 
At the same time, sometimes you may need to directly read a file from Excel. 
Note that, when possible, we recommend the use of `.csv` files. 
They work well across platforms and software (i.e., even if you need to load the file with some other software, such as Python).

The package for loading Excel files, {readxl}, is not a part of the tidyverse, so we will have to install it first (remember, we only need to do this once), and then load it using `library(readxl)`. Note that the command to install {readxl} is grayed-out below: The `#` symbol before `install.packages("readxl")` indicates that this line should be treated as a comment and not actually run, like the lines of code that are not grayed-out. It is here just as a reminder that the package needs to be installed if it is not already.

Once we have installed readxl, we have to load it (just like tidyverse):


```r
install.packages("readxl")
```


```r
library(readxl)
```

We can then use the function `read_excel()` in the same way as `read_csv()`, where "path/to/file.xlsx" is where an Excel file you want to load is located (note that this code is not run here):


```r
my_data <-
    read_excel("path/to/file.xlsx")
```

Of course, were this run, you can replace `my_data` with a name you like. Generally, it's best to use short and easy-to-type names for data as you will be typing and using it a lot. 

Note that one easy way to find the path to a file is to use the "Import Dataset" menu. It is in the Environment window of RStudio. Click on that menu bar option, select the option corresponding to the type of file you are trying to load (e.g., "From Excel"), and then click The "Browse" button beside the File/URL field. Once you click on the, RStudio will automatically generate the file path - and the code to read the file, too - for you. You can copy this code or click Import to load the data.

### Loading SAV Files

The same factors that apply to reading Excel files apply to reading `SAV` files (from SPSS). NOte that you can also read `.csv` file directly into SPSS and so because of this and the benefits of using CSVs (they are simple files that work across platforms and software), we recommend using CSVs when possible. First, install the package `haven`, load it, and the use the function `read_sav()`:
    
    
    ```r
    install.packages("haven")
    ```


```r
library(haven)
my_data <-
    read_sav("path/to/file.xlsx")
```

### Google Sheets

Finally, it can sometimes be useful to load a file directly from Google Sheets, and this can be done using the Google Sheets package.


```r
install.packages("googlesheets")
```


```r
library(googlesheets)
```

When you run the command below, a link to authenticate with your Google account will open in your browser. 


```r
my_sheets <- gs_ls()
```

You can then simply use the `gs_title()` function in conjunction with the `gs_read()` function:
    
    
    ```r
    df <- gs_title('title')
    df <- gs_read(df)
    ```
