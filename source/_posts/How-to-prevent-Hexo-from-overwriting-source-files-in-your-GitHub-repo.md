title: How to prevent Hexo from overwriting source files in your GitHub repo
date: 2014-08-09 05:23:00
categories: 
- Hexo
tags:
- GitHub
- Git
- Hexo
- Version Control 
- Deployment 
- Source Code 
- _config.yml
---

I figure I should write about this one, because it took me hours to figure out something that should have taken me 30 minutes to do. I'm also still relatively new to Git and GitHub so that didn't help my situation: The other night, while deploying my website files for this blog, I spent countless hours (probably about 6 hours) performing all kinds of commits, deletions, pushes, etc to the GitHub repo that this site is hosted in.  <!-- more -->

I initially got this blog up and running on Github in a few minutes, however, I noticed that the source files I pushed were getting replaced by the public files that Hexo deploys. I set Hexo to deploy to the Master branch and, for some reason, the Git operation behind the deployment script likes to delete all of the files in the repo and replace them with the newly created files. Please note, I might be totally wrong about how Hexo works in this manner, I just noticed this was causing a versioning conflict - that and mixing public files with the source code was making the repo look messy. 

### Here's what I did to get around the problem 

- After attempting to remove / push files to my remote GitHub repo, I ended up deleting it so I could start fresh. I think there their are commands out there that let you reset Git repos (yes I'm going to laugh at this 5 years from now) but I couldn't get to the point I wanted to get to with my local and remote repos. 

- I then created a branch for my new repo called "source_code" - You can actually name this branch anything you want. 

- I then committed all of the source code files for this blog to that branch. In addition, I let Hexo generate a .deploy and public folder in this branch. You can either delete these before commiting changes in this branch or you can just commit these files / folders as you make commits from this branch. 

- Lastly, I configured Hexo (see the _config.yml file) so it deploys to the Master branch. 



This means all of the public files (The generated HTML, CSS, JS etc ) that Hexo deploys is deploying to the Master branch and I am able to commit any changes made to the source code to the "source_code" branch thus no versioning conflicts or overwriting of files occur. 

If you want to keep your local repo in sync with your remote repo then I would suggest switching to the repo and pulling the files that were deployed to it by Hexo and then switching to your branch for the source code and making commits from there. 

I initially experimented with creating a directory within the Master branch and I somehow thought I could initialize a branch inside of that directory yadda yadda and then I realized Git and other versioning control software work like that and the process was getting too complicated. 

Hopefully that helps. If you have any questions then please feel free to leave a comment here. If you think I could have achieved the above in a much simpler way then I would love to hear from you! 
