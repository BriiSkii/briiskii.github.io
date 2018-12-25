---
title: Docker Swarm
updated: 2018-12-24 20:55
---

Docker Swarm Blog

- For the past few weeks or so, I've been learning Docker. It's been pretty fun. I'm following the [Docker Mastery](https://www.udemy.com/share/1001eQA0Idd1dURQ==/) the amazing course by Bret Fisher. I've learned a ton. I'm always working to improve my Linux skills and this course has helped immensely. I use Linux for work everyday, but it's not enough for me to learn certain tasks. This past week, I've been learning Docker Swarm. Today's task was creating a 3-node cluster. 

Trying to setup worker nodes, I initially thought it would be easy, but it's proven to be quite the task. I ran into several issues. 

1. Could not connect to my cloud servers
I spun up a few worker nodes to play around with. Following a tutorial, during the initial setup, I added my ssh key to the servers as instructed only to not be able to connect. I tried every fix I found on Stack Overflow and every other site. 
- ssh-copy, -i , etc. NOTHING seemed to work. 
- Attempted to paste my key into the console directly, but it kept adding random chars. Not sure what that's about. 
- Even tried restarting the sshd service, checking firewall rules. Still nothing. 
As a last ditch effort, I generate a key from my windows laptop, destroyed the servers, spun up some new nodes and like magic I was able to connect. 
- It's possible I missed something, and at some point I will try and figure out what the issue was. 

2. Worker node timeouts
I'm so elated I can connect, I hit the ground running, I run `docker swarm init` and everything is going working fine. That is, until I paste the token and it kicks back a timeout error. I'm down, but not defeated. I break out my Google-fu skills and get to work. I head to the Docker documentation and Stack Overflow, where I see that it may be a port issue. I figure out how to check the ports on a Ubuntu server, and proceed. I open up the necessary tcp and udp ports, run the docker swarm leave cmd and try the join command again. SUCCESS!!, the node joins the swarm,  I do the same on the other nodes and take a much earned break. It might not seem like much to some people, but for me it's a win. 

3. After deploying a stack, I couldn't access the respective web page would have been forwarded to port 5000/5001. After too long than I'm willing to admit, after using my manager as a sounding board I basically figured out it was the work firewall and the app actually did work I just need to be home or use my mobile for testing. 

4. Error: No such container: psql.1.xxxx Luckily this didn't take too much troubleshooting, turns out I needed to be on the same node the service lives. 

LESSONS / THOUGHTS
- This gave me an opportunity to learn more about the netstat and ufw commands, since I don't get the use the regularly. 
- I need to brush up on ssh, and different ways to troubleshoot it. 
- Stack Overflow is a life saver -- That helpful post can be found [here](https://stackoverflow.com/questions/46116999/workers-unable-to-connect-to-swarm-on-aws-ec2). It post says EC2, but works for other hosts. 
- The Docker docs, are also helpful [Docker docs](https://docs.docker.com/engine/swarm/swarm-tutorial/)
- Ask for help sooner. 
- Definitely going to need to review Swarm 
- Seriously girl?
