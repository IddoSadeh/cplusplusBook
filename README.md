# Foreward
As I progress through my programming journey I learn more and more the importance of documentation. This document will overview the development process of my first online coding textbook.

## Project Background

As of July 2023, I have been teaching programming for over 2 years. I have specialized in teaching AP CSA - Java, Intro to programming with Python, and Competitive programing. I also recently finished a 1 year contract at UBC through their worklearn program working on teaching materials for the department of earth and ocean science and the department of data science. Through this program I have been exposed to the Jupyter project. Specifically through the initiative to transition from teaching DSCI 100 in R to Python.

 I look up to free online educational platforms I used as a kid and appreciate their impact on my learning journey. Getting feedback from students I teach personally, and from those I have built learning tools at my time at UBC brings me great pride. While working on DSCI 100 I was also especially inspired of the scope of the project. The [DSCI 100 course textbook](https://python.datasciencebook.ca/intro.html) will one day be used by over 2000 students a year at UBC alone. I believe I can build similar projects with my own teaching materials, and can benefit thousands of students a year as well, instead of only the several I teach throughout the year.


## The Plan

I plan to make a learning platform for coding. The idea is to formalize everything I have been teaching in the past two years in to organized Textbooks. This can aid my students with their learning, while providing me an oppurtinuty to optimize my teachings while learning how to develop big projects of this size.

To start, I envision a simple website with a textbook directory for my teachings, and a practice platform similar to that available on https://blog.finxter.com/ customized to each chapter and textbook.

If time permits, I will also create videos, in the spirit of Kahn academy, for each chapter.

I will be writing the chapters prior to teaching them to my students, so I expect the first three textbooks to only be ready in the spring of 2024.

The practice questions and videos may take more time.

## Roadmap

**C++**

[X] Intro Chapter - Tools and Hello World (Uploaded July 23, 2023)

[] Types - 

[] Objects and Classes

[] References and Pointers

**AP CSA - Java**
[]

## Ideas
- Translate to Hebrew?
- Monetize like finxter?



# Tech

## Environemnt

I created the environment with mamba.
Environemnts are important for reproducibility and avoiding conflicts and redundancy.

*Creating enviornment*

    mamba create -n nameofmyenv `<list of packages>`

*Activating environemnt*

    mamba activate nameofmyenv
*deactivating environemnt*

    mamba deactivate

## Jupyter Book

*install Jupyter Book*

    conda install -c conda-forge jupyter-book

*Quickly generate a sample book* 

https://jupyterbook.org/en/stable/start/create.html

    jupyter-book create mynewbook/ 
    
*Build your book*

https://jupyterbook.org/en/stable/start/build.html#build-your-book

    jupyter-book build mybookname/

*Create your own content file*

https://jupyterbook.org/en/stable/start/new-file.html

*Updating the book*

https://jupyterbook.org/en/stable/start/publish.html

-  every time i make changes, do the following:

To update your online book, make changes to your book’s content on the main branch of your repository, re-build your book with <code>jupyter-book build mybookname/</code> and then use <code>ghp-import -n -p -f mylocalbook/_build/html</code> as before to push the newly built HTML to the <code>gh-pages</code> branch.

## Publishing the website

- bought domain from google. to connect domain to github:
    - I am already hosting my personal webpage on github pages. This project is considered a GitHub pages project. There is no real difference in how to connect domain to repo:
    - On google domains navigate to your domain.
    - Go to the DNS settings.
    - Add two custom records: A and CNAME
    - A record host name should be left empty, the data ip addresses were taking from [GitHub](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain)
    - CNAME host name should be `www`.  Data should be `yourGitHubUserName.github.io.` - **Note:** GitHub can automatically differentiate between your project and personal website through the CNAME files whihc are automatically generatred. No need to specify the exact URL for your project - it wont work this way.
    - Navigate to your project repo - settings - pages
    - enter your custom domain in the box, save, enforce https. - This can take several tries, be patient. Sometimes you may need to remove and resave the domain. I have had it break unexpectedly as well and needed to reocndigure this part.

# Creating the C++ Textbook

I have "finished" the first chaper of the textbook. 
Some thoughts so far:
- I may need to rethink how the website is designed. Maybe have a main website that redirects to each textbook, and not host all the textbooks on one website.
- It's annoying images are so awkward. I viewed the data science 100 textbook fro UBC and it seems they didnt fix it either.
