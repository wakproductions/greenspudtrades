# Intro

**Description:** Setup GitHub Pages "gh-pages" branch and "master" branch as subfolders of a parent project folder ("grandmaster").

**Author:** Chris Jacob [@_chrisjacob](http://twitter.com/#!/_chrisjacob)

**Tutorial (Gist):** [https://gist.github.com/833223](https://gist.github.com/833223)

## The Result

The final folder structure on my local system is:

	/grandmaster
	/grandmaster/master
	/grandmaster/master/.git # checkout of "master" branch
	/grandmaster/master/README.markdown
	/grandmaster/gh-pages
	/grandmaster/gh-pages/.git # checkout of "gh-pages" branch (removed "master" branch)
	/grandmaster/gh-pages/index.html
	/grandmaster/gh-pages/README.textile

See "master" branch: [https://github.com/chrisjacob/grandmaster](https://github.com/chrisjacob/grandmaster)

See "gh-pages" branch: [https://github.com/chrisjacob/grandmaster/tree/gh-pages](https://github.com/chrisjacob/grandmaster/tree/gh-pages)

See GitHub Page (auto generated): [http://chrisjacob.github.com/grandmaster/](http://chrisjacob.github.com/grandmaster/)


## The Process

> A note for GitHub novices - replace "chrisjacob" with your own GitHub username.
>
> A note for Terminal novices - you don't need to enter the "ichris:Sites $ " parts of the code listed below. ^_^

Visit GitHub and create a new repository with the project name "grandmaster".  
[https://github.com/repositories/new](https://github.com/repositories/new)

> Don't follow GitHub's `Next steps` instructions! Follow the steps below to setup your projects folders on your local system.

Open Terminal.app, create project parent folder "grandmaster", and a subfolder for the "master" branch. Initialise a new git repository for the project and push the "master" branch to GitHub.

	ichris:Sites $ mkdir grandmaster
	ichris:Sites $ cd grandmaster/
	ichris:grandmaster $ mkdir master
	ichris:grandmaster $ cd master/
	ichris:master $ git init
	ichris:master $ echo "# Master README file" > README.markdown
	ichris:master $ git add .
	ichris:master $ git commit -m "Master README added"
	ichris:master $ git remote add origin git@github.com:chrisjacob/grandmaster.git
	ichris:master $ git push origin master

Refresh your projects "master" branch page on GitHub to see the committed files.  
[https://github.com/chrisjacob/grandmaster](https://github.com/chrisjacob/grandmaster)

Auto generate a GitHub Pages branch, with some default content.  
[https://github.com/chrisjacob/grandmaster/pages/create](https://github.com/chrisjacob/grandmaster/pages/create)

> Or follow these steps to get to the generator page: 
>
> 1. Go to the projects Admin page on GitHub [https://github.com/chrisjacob/grandmaster/admin](https://github.com/chrisjacob/grandmaster/admin)
>
> 2. Check the "GitHub Pages" checkbox
>
> 3. A popup will ask you to "Activate GitHub Pages" - click the big "Automatic GitHub Page Generator" button

Check that your GitHub Pages page has been built and is available.  
[http://chrisjacob.github.com/grandmaster/](http://chrisjacob.github.com/grandmaster/)

Back in Terminal.app, change directory back to the parent folder, setup a "gh-pages" subfolder for your "gh-pages" branch and change directory into it.

	ichris:master $ cd ../
	ichris:grandmaster $ mkdir gh-pages
	ichris:grandmaster $ cd gh-pages/

Clone your "grandmaster" repository into the "gh-pages" folder (this will clone in the "master" branch), checkout the "gh-pages" branch, list the files (should have "index.html" and ".git") and then remove the "master" branch to avoid any confusion. Last step is to check that "master" branch was removed and only "gh-pages" branch is listed.

	ichris:gh-pages $ git clone git@github.com:chrisjacob/grandmaster.git .
	ichris:gh-pages $ git checkout origin/gh-pages -b gh-pages
	ichris:gh-pages $ ls -la
	ichris:gh-pages $ git branch -d master
	ichris:gh-pages $ git branch

> You will probably get a warning when deleting the "master" branch... don't worry about it ^_^

Lets add a "README.textile" file to the "gh-pages" branch

	ichris:gh-pages $ echo "h1. GitHub Pages README file" > README.textile
	ichris:gh-pages $ git add .
	ichris:gh-pages $ git commit -m "Child README added"

Now push to the "gh-pages" branch

	ichris:gh-pages $ git push origin gh-pages

Visit your projects "gh-pages" branch page on GitHub to see the committed files.    
[https://github.com/chrisjacob/grandmaster/tree/gh-pages](https://github.com/chrisjacob/grandmaster/tree/gh-pages)

If everything has gone well you now have a parent project folder named "grandmaster", with subfolders for its two branches "master" and "gh-pages"; each containing a checkout of their respective branch.

> For me this system keeps things nice and tidy without needing to do `git checkout gh-pages` each time I want to view my "gh-pages" branch. 
> 
> Might also be a useful structure for output from static site generators like [Jekyll](http://jekyllrb.com/), [Webby](http://webby.rubyforge.org/), or [nanoc](http://nanoc.stoneship.org/).  
> 
> Enjoy ^_^

