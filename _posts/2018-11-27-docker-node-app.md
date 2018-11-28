# Node.js to Docker

- Today I decided to find a simple project to deploy on docker. Decided on something involving Nodejs. Node already has [documentation](https://nodejs.org/en/docs/guides/nodejs-docker-webapp/) on how to do this. I've been learning Docker, so a lot of this was familiar. Using the documentation I setup a basic web server and  installed the necessary modules. I initially used my vagrant box for the project but ran into a few issues with npm install constantly asking me to rewrite the names of different files. After fixing that issue, I uploaded my project to GitHub.  I then proceeded to build the Docker image and spin up the container. I was legit shocked it worked the first time. 

## ISSUES:
- **file re-writes:**
     - When running npm install it kept giving me an error and asking me to rename a few package.json.xxxx files. I use a Vagrant box I used for most of my projects, I believe that may have been causing the issue, after moving the project files to a directory not shared with my host machine, npm install ran fine. 



## THOUGHTS / LESSONS:
- Using vagrant and with Atom on my host machine via a shared mount proved to be a problem, however, using Vim was an easy fix. 
- Next I want to figure out to automate some of this and how to scale it out. 
- Going to try and include more code examples in the next post
