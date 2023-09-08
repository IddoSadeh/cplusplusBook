https://cplusplus.programado.dev/intro.html



# Tech

## Environemnt

I created the environment with mamba.
Environments are important for reproducibility and avoiding conflicts and redundancy.

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

To update your online book, make changes to your book’s content on the main branch of your repository, re-build your book with <code>jupyter-book build cplusplus/</code> and then use <code>ghp-import -n -p -f cplusplus/_build/html</code> as before to push the newly built HTML to the <code>gh-pages</code> branch.

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

# Future Chapter Ideas

- Error Handling and Exceptions: try, catch, and throw; creating custom exceptions.
- Structs and Enums
- More on STL: maps, queues, stacks etc.
- smart pointers and resource management
- lamnda expressions + functional programming
- condurrency
- Large projects: Make fules, compiling etc.
- Networking
- GUI