# Foreward
As I progress through my programming journey I learn more and mroe the importance of documentation. This document will overview the development process of my first online coding textbook.

The markdown file shows in chronological order how I built this book.

# Environemnt

I created the environment with mamaba.
Environemnts are important for reproducibility and avoiding conflicts and redundancy.

*Creating enviornment*

    mamba create -n nameofmyenv `<list of packages>`

*Activating environemnt*

    mamba activate nameofmyenv
*deactivating environemnt*

    mamba deactivate

# Jupyter Book

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
