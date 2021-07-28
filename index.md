# Health Data Analytics and Machine Learning: pre-course preparation resources

## Table of Contents
1. [General advice](#general_advice)
2. [How to spend your preparation time](#prep_time)
3. [Setting up your computer](#cpu_setup-example)
4. [Reading list](#reading_list)
5. [Advice from previous HDA students](#student_advice)

## General advice <a name="general_advice"></a>

The term 1 modules will give you a solid foundation in epidemiology, statistics, and handling healthcare data, with an introduction to molecular epidemiology and some basic machine learning modelling. Our students have a highly diverse range of backgrounds, and there will always be some students with very little experience of each particular subject. So don't panic if you haven't, for example, studied epidemiology before. The modules start with the basics and, if you work hard, you will be on a steep learning curve and will reach a high level of understanding by the end of term 1, even from a standing start.

With that said, you have the opportunity to lower the gradient of your learning curve by doing some preparatory study ahead of the course in areas that you are less familiar with. This page aims to give you some pointers on how to spend that pre-course preparation time.


## Choosing how to spend your preparation time <a name="prep_time"></a>

### Learning to code

Everything we do on the HDA course is underpinned by an ability to code. As with everything else, you will be well trained in coding throughout the course, and we do not assume or require any prior experience. However, in the very early stages of learning to code it can take a long time to solve simple problems, so you can certainly make things easier on yourself by getting through this very early stage before the course, so you're not doing the frustrating slow bit at the same time as studying epidemiology, statistics, etc.

The HDA course primarily uses R, and there are numerous free or cheap resources online for getting started. Here are a selection of the best:

**[Free R Tutorial - R Basics - R Programming Language Introduction](https://www.udemy.com/course/r-basics/)**

Excellent intro to R, starting from the very beginning. Free to take the course – you only have to pay if you want the certificate.

**[Free R Tutorial - R, ggplot, and Simple Linear Regression](https://www.udemy.com/course/machlearn1/)**

A gentle introduction to using R for data manipulation, visualisation, statistics and simple ML. Free to take the course – you only have to pay if you want the certificate.

**[R for statistics](https://cran.r-project.org/doc/contrib/Verzani-SimpleR.pdf)**

A really thorough guide to using R for statistics

**[erikgahner/awesome-ggplot2](https://github.com/erikgahner/awesome-ggplot2)**

A great curated list of resources for R programming

---

### Statistics

While the term 1 statistics course starts with the basics, the whole HDA course is based around a solid understanding of statistics and many concepts can take time to digest. So, if your stats is a bit rusty, you can make things easier on yourself by brushing ahead of the course. When you get to the machine learning module, an understanding of linear algebra will be a great asset. The course does provide optional maths refreshers in term one, which cover linear algebra, but if you haven't studied it before then some pre-course revision may well be beneficial.

Here are some useful stats and linear algebra resources:

**[Statistics with R](https://www.coursera.org/specializations/statistics)**

Kill two birds with one stone – this course teaches statistics as applied in R

**[Biostatistics in Public Health: Coursera](https://www.coursera.org/specializations/biostatistics-public-health)**

A more epi/biostats focus, but still useful

**[Mathematics for Machine Learning: Linear Algebra](https://www.coursera.org/learn/linear-algebra-machine-learning)**

This course provides a thorough grounding in linear algebra for ML

**[3Blue1Brown](https://www.youtube.com/channel/UCYO_jab_esuFRV4b17AJtAw)**

Great youtube channel with stats/ML instructional videos

**[StatQuest with Josh Starmer](https://www.youtube.com/user/joshstarmer)**

Another great statistics youtube channel

**[Statistics and Probability: Khan Academy](https://www.khanacademy.org/math/statistics-probability)**

For starting from the basics, Khan Academy has excellent tutorials


## Computer set-up <a name="cpu_setup"></a>

We will have a dedicated session in the induction week where we will guide you through installing all the required software and packages. However, if you want to do this in advance of starting the course, here 's what you need to do.

You will be extensively using R throughout the year, a widely used programming language for statistical analyses and machine learning (see [https://www.r-project.org/about.html](https://www.r-project.org/about.html)). In this session, we are going to install R, R Studio, and the main R packages that you will be using throughout the year on your laptops.

### Installing R

First download and install R (version 4.0.2) from the CRAN.

**[R for Mac OS X](https://cran.r-project.org/bin/macosx/)**

For Mac users

**[Download R-4.0.2 for Windows. The R-project for statistical computing.](https://cran.r-project.org/bin/windows/base/)**

For Windows users

**[The Comprehensive R Archive Network](https://cran.r-project.org)**

For Linux users

### Installing RStudio

R Studio is an integrated development environment for R. You can download the Open Source R Studio Desktop from this link:

**[Download RStudio](https://www.rstudio.com/products/rstudio/download/)**

### Install required packages in R

There are two main repositories of R packages (sets of built-in R functions): the CRAN (Comprehensive R Archive Network) and Bioconductor. Once both R and R Studio are installed, you can open R Studio and install the required packages by running the following code:

    ```r
    ### First we create a function that checks if you have the package installed 
    ### and, if you don't have it, installs the package
    checkInstallPackage <- function(package.list){
      new.packages <- package.list[!(package.list %in% installed.packages()[,"Package"])]
      print(paste(length(new.packages), "packages require installation. Installing now"))
      if(length(new.packages)) install.packages(new.packages)
    }
    ### Now we have a function, we can pass a list of the packages we will be 
    ### using on the course into the function, and install them all in one go
    # first we create the list of packages
    package.list <- c("e1071", "optparse", "tidyverse", "mvoutlier", "pcaMethods",
    			"imputeLCMD", "lme4", "RColorBrewer", "VennDiagram", "glmnet", "omics","stringr",
    			"utils","dplyr", "ROCR", "ggplot2", "ggfortify", "survival", "igraph", "corpcor",
    			"ppcor", "abind", "parallel")
    # now we run the function
    checkInstallPackage(package.list)
    # this may take some time to run #
    ### Installing some packages from Bioconductor ###
    # some of the packages we use are only available on bioconductor and these need 
    # to be installed separately. Run this code to install these packages.
    # You may receive a prompt "Update all/some/none? [a/s/n]:" – 
    # if you see this, type "a" and press enter
    if (!"pcaMethods" %in% rownames(installed.packages())) {
      if (!requireNamespace("BiocManager",
                            quietly = TRUE))
        install.packages("BiocManager")
      BiocManager::install("pcaMethods")
    }
    if (!"impute" %in% rownames(installed.packages())) {
      if (!requireNamespace("BiocManager",
                            quietly = TRUE))
        install.packages("BiocManager")
      BiocManager::install("impute")
    }
    ```

Once you have run all these lines of code, please make sure that all the packages have been properly installed. They should all be listed in the “Packages” tab (bottom right hand quadrant of R Studio):
![Screenshot of installed packages](Screenshot%202020-08-14%20at%2016.25.52.png)

## Term 1 reading list <a name="reading_list"></a>

### Epidemiology

#### Recommended reading
- **Oxford Handbook of Epidemiology for Clinicians.** Ward et al. [https://oxfordmedicine.com/view/10.1093/med/9780198529880.001.0001/med-9780198529880](https://oxfordmedicine.com/view/10.1093/med/9780198529880.001.0001/med-9780198529880)
- **Basic Epidemiology** Bonita et al. Available free of charge from: [https://apps.who.int/iris/bitstream/handle/10665/43541/9241547073_eng.pdf?sequence=1](https://apps.who.int/iris/bitstream/handle/10665/43541/9241547073_eng.pdf?sequence=1)

#### Other good introductory epidemiology books
- **Epidemiology(Fifth edition.).** Szklo, M. and Nieto, F.J. (2014).  Burlington, Massachusetts,Jones & Bartlett Learning (approx. £93). Available to purchase from: [https://blackwells.co.uk/bookshop/product/9781449604691?gclid=Cj0KCQjwwqXMBRCDARIsAD-AQ2g9wGEkLUMAkkoIY_FO62AVEVFj2neeE93lnZKq--zCsJF7IuAp65kaAgAKEALw_wcB](https://blackwells.co.uk/bookshop/product/9781449604691?gclid=Cj0KCQjwwqXMBRCDARIsAD-AQ2g9wGEkLUMAkkoIY_FO62AVEVFj2neeE93lnZKq--zCsJF7IuAp65kaAgAKEALw_wcB)
- **Gordis Epidemiology.** Gordis, L. (2014).  Philadelphia, PA: Elsevier Saunders (approx. £35). Available to purchase from: [https://www.uk.elsevierhealth.com/epidemiology-9781455737338.html](https://www.uk.elsevierhealth.com/epidemiology-9781455737338.html)
- **Epidemiology: Beyond the Basics.** Ward H, Toledano M, Shaddick G, Davies B, Elliott P (2012) . Oxford University Press, Oxford UK. (Amazon price £26).
- **Essential epidemiology: an introduction for students and health professionals.** Webb, P., Bain, C. and Page, A., 2016. . Cambridge University Press. [https://www.amazon.co.uk/Essential-Epidemiology-Introduction-Students-Professionals/dp/0521177316](https://www.amazon.co.uk/Essential-Epidemiology-Introduction-Students-Professionals/dp/0521177316)

### Statistics

- **Essential Medical Statistics.** Kirkwood B and Sterne J (2003) (2nd ed). Blackwell Science Ltd. [https://www.amazon.co.uk/Essential-Medical-Statistics-Essentials-Kirkwood/dp/0865428719](https://www.amazon.co.uk/Essential-Medical-Statistics-Essentials-Kirkwood/dp/0865428719) 
Chapters 2–5 will support what you learn in the term 1 statistics module.
- **An Introduction to Medical Statistics.** Bland M (2015) (4th ed). Oxford University Press. An alternative excellent standard text book. This includes multiple choice and other questions at the end of chapters, which may be useful for revision purposes. [http://www-users.york.ac.uk/~mb55/intro/introcon.htm](http://www-users.york.ac.uk/~mb55/intro/introcon.htm) (accessed 25 July 2017) contains useful additional material. Chapters 4–7 will support what you learn in the term 1 statistics module.

### Clinical Data Management

- UK Biobank: Protocol for a large-scale prospective epidemiological resource. [http://www.ukbiobank.ac.uk/wp-content/uploads/2011/11/UK-Biobank-Protocol.pdf](http://www.ukbiobank.ac.uk/wp-content/uploads/2011/11/UK-Biobank-Protocol.pdf)
- Surkis et al. Research data management, J Med Libr Assoc. 2015 Jul; 103(3): 154–156. [https://dx.doi.org/10.3163%2F1536-5050.103.3.011](https://dx.doi.org/10.3163%2F1536-5050.103.3.011)
- Mcardle et al. Research data management 'Green Shoots' pilot programme, final reports, Imperial College London. [https://spiral.imperial.ac.uk:8443/handle/10044/1/28409](https://spiral.imperial.ac.uk:8443/handle/10044/1/28409)

### R programming

- Hands-on programming with R, Garrett Grolemund. [https://rstudio-education.github.io/hopr/index.html](https://rstudio-education.github.io/hopr/index.html)



## Advice from previous HDA students <a name="student_advice"></a>

We asked students on the 2019–2020 HDA course what advice they would give their past selves before starting the course. Their responses are below.

### Before starting the course

- My advice would be: if you are a biologist and have not done maths in a while, take a linear algebra course as a MOOC maybe. If you have questions, ask! Never be afraid of being curious!
- Don’t be disheartened when you don’t have a clue what’s happening in R or python if you have zero prior coding experience - it’s a steep learning curve but you’ll pick it up. Coding is the sort of thing where there’s a certain level of understanding beyond which everything just seems very understandable, and before that level it just seems super overwhelming. Just the ability to understand the syntax in R and the different nuances etc gives you the ability to understand and search every problem on stack overflow. You don’t need to know a load of functions off by heart.
- If possible, do some of the data camp courses BEFORE starting the MSc
- Take an intro linear algebra course and don’t just rely on the math refreshers

### Throughout the course

- Organise and document everything during projects: scripts, data, notes etc. You will definitely revisit old code and old notes
- Be proactive, ask question and use the resources that are made available to you (the people around you and the lecturers)
- Keep your notes and code organised, I kept referring back to past tutorials in the project, and having a filing system from the beginning of the project made this so much quicker.
- Don’t think you’re the only one who doesn’t understand something. There’s a huge range of pre-existing skills and knowledge in the other people in the class and inevitably you’ll know less about some stuff and more about other stuff than your pals
- Especially with the wide range of skill sets in the program, whenever I didn’t get something I knew at least a quarter of our program did and had to fight my self consciousness to ask the question. Also lecturers are really nice I would have asked a few more questions had I not been worried about looking like an idiot
- Get to know the people on the course and work with them – everyone has different strengths and will pick things up at different rates and it really helped this year working together to understand things.
- Capitalise on your classmates’ knowledge! It’s a nice symbiotic relationship
- Start projects earlier.
- Revise the second term lectures such that there are some baby steps leading to the big equations
- Summer quarter advice - make sure they have data you want to work with.
- Advice for the thesis: get your references and stuff organised and maybe don’t wait too much before writing some stuff.


