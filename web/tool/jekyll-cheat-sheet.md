# Jekyll Cheat Sheet
A blog-aware, static site generator powered by Ruby.

Similar other programs are Harp, Middleman, and Octopress.



## Advantages of using a static site generator

- Sites load fast (load pages directly and don't worry about database)
- Site is more secure
- Less maintenance involved
- Easier to host in more places



## How to get started with Jekyll

1. Install Ruby
2. Run `gem install jekyll`
3. Run `jekyll new my-project-name` (or `jekyll new .` to create in current directory)
4. Run `jekyll serve` to see the project locally
5. Upload to any server to see online. May need to update `config.yml` for url and baseurl



## How to deploy Jekyll blogs with Git
More info: [https://www.digitalocean.com/community/tutorials/how-to-deploy-jekyll-blogs-with-git]([https://www.digitalocean.com/community/tutorials/how-to-deploy-jekyll-blogs-with-git)

### Local and Remote installation
Do the following steps for both:

- Install RVM public key, run `gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3` for security reasons [More info](http://rvm.io/rvm/security).
- Install the latest stable Ruby, run `curl -sSL https://get.rvm.io | bash -s stable --ruby` (More info)[http://rvm.io/]
- Install Jekyll, run `gem install jekyll`
- Install Git. On Ubuntu you can run `apt-get install git` [More info](http://git-scm.com/)

### Create the Jekyll blog

- Navigate to where you want to store your blog files on local machine, then run `jekyll new my-blog-name`
- Depending on your website configuration, you may want to edit `_config.yml`

### Initialize Git

- Enter the blog directory you created, run `cd my-blog-name`
- Run `git init`
- Run `git add .`
- Run `git commit -m "New Jekyll blog"`

### Deploy configurations

- On the remote server, navigate to home directory and create a new "bare repository" to deploy to, Run:

        cd ~
        mkdir repo && cd repo
        mkdir my-blog-name.git && cd my-blog-name.git
        git init --bare

- Setup the Git hook/script that will automatically create the blog each push. Run:

        cd hooks
        touch post-receive
        nano post-receive

- Paste the following into that open file, and edit the three variables at the top as necessary:

        #!/bin/bash -l
        GIT_REPO=$HOME/repo/my-blog-name.git
        TMP_GIT_CLONE=$HOME/tmp/git/my-blog-name
        PUBLIC_WWW=/var/www/my-blog-name

        git clone $GIT_REPO $TMP_GIT_CLONE
        jekyll build --source $TMP_GIT_CLONE --destination $PUBLIC_WWW
        rm -Rf $TMP_GIT_CLONE
        exit

- Save the file by pressing `ctrl+o`, then `enter`
- Give the file executable permissions. Run `chmod +x post-receive`
- Back on the local computer, point Git to the remote repository. Run `git remote add droplet user@example.com:repo/my-blog-name.git`
- To publish the blog, just run `git push droplet master`

- Potential error when publishing: "Could not find a JavaScript runtime." In that case, the simplest fix is to run `sudo apt-get install nodejs`. More info: [issue tracker](https://github.com/jekyll/jekyll/issues/2327) and [reasons](https://github.com/sstephenson/execjs#execjs). This JavaScript requirement will be removed in Jekyll 3.0.



## GitHub Pages
Two types:

- User pages: Create a new repo with the name of `<username>.github.io`, for example: `danialgoodwin.github.io`. Limit 1.
- Project pages: In any existing repo, create a branch called `gh-pages` and GitHub will automatically serve the files to users. Must be a static site.

Updates may take up to 10 minutes to GitHub to handle changes.



## More Info

- [(Official Jekyll website](http://jekyllrb.com/)
- [Jekyll on GitHub](https://github.com/jekyll/jekyll)
- [treehouse.com](http://teamtreehouse.com/library/build-a-blog-with-jekyll-and-github-pages#hosting-with-github-pages)

- Great: [How to create separate pages per tag/category (without plugins)](http://christianspecht.de/2014/10/25/separate-pages-per-tag-category-with-jekyll-without-plugins/)
- Great: [How I Created a Beautiful and Minimal Blog Using Jekyll, Github Pages, and poole](http://joshualande.com/jekyll-github-pages-poole/)
- Great: [How to add Google Plus comments box to Jekyll](http://steelx.github.io/best-internet-tips/2014/11/23/Add-google-plus-comments-box-to-jekyll-website.html)
- Great: [How to build a better sitemap with Jekyll](http://davidensinger.com/2013/11/building-a-better-sitemap-xml-with-jekyll/)
