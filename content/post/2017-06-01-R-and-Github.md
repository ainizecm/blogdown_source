---
title: "R and Github"
author: "Ainize Cidoncha"
date: 2017-06-03T21:13:14-05:00
categories: ["R"]
tags: ["R", "analytics","Github","version control"]
---



I have being using R since I was at uni and I did recently discovered how to sync it with Github for version control of projects which is making my life much easier. 

I love being to have a version control of my project. Moreover, I can use any computer to work on my app which is giving me a lot of flexibility. 

There are obviuosly other tool as Google Drive, One Drive...that you can use to save your work through laptops but I just find the integration of R with Github very handy.

Here is how I do sync my R projects with GitHub.

First of all, we need:

- A Github account (You can set it up [**here**] (https://github.com/join?source=header-home))

- Install Desktop Github on your computer (You can download it [**here**] (https://desktop.github.com/))

- Generate and activate your computer's SSH key (Check how to do it [**here**] (https://help.github.com/articles/connecting-to-github-with-ssh/))

- Download [**R**](https://cran.r-project.org/bin/windows/base/) and [**RStudio**](https://www.rstudio.com/products/rstudio/download2/)

Once that checklist is completed we can start syncing!

Let's create a new reposirory. Give it the name you want for your project and save it.

![](/img/newrepository.png)


Open now that repository, click on Clone or Download and copy the SSH addres to your clipboard.

![](/img/clone.png)

Let's open now RStudio and click on the top right hand side Project dropdown option. This is also when you can access your projects later on.

Click on New Project and you should be given three options, the last one being Version Control. Selecting that option should give you the opction to choose Git as the platform and you will need to fill out the configuration for your project.

Enter the copied address on the Repository URL, the name of the project on Project directory name and find the folder you want to clone it into.

![](/img/Rprojectconfig.png)


Done!

You know have a folder on your computer cloned from Github. You should be able to see a little Git icon on your header, and you can iclude a Git tab to your Enviroment and History tabs for easier proccesing.

Now, everytime you want to work on your project you can:
- First ensure that your local copy and git are sycn by looking at the differences and pulling from the server if necesary
- Make any changes you need to project and we you are happy with it
- Check the differences with the server, commit your changes and push them so that your git is updated.

![](/img/Rcommit.png)

Following this procces you can work on you R projects wherever you want and you will always have a nice version control in case something goes wrong.

I hope you find this as useful as I did!


