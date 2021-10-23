---
author:
  name: "Ayush Verma"
date: 2019-04-28
linktitle: Ultimate guide to use Cloud Services
type:
- post
- posts
title: Ultimate guide to use Cloud Services
weight: 10
series:
- Cloud
---


This guide will show you how to create a virtual server and deploy an app to it. We are using Digitalocean for PaaS.

**Ultimate guide** to use Cloud Services

This guide will show you how to create a virtual server and deploy an app to it. We are using [Digitalocean](https://www.digitalocean.com) for PaaS.

![](https://cdn-images-1.medium.com/max/800/0*GVMtCxq5Q6S62syt.png)

#### **Okay Why I am writing this TL,DR Guide ?**

The goal of this guide is to introduce you to the concept of provisioning a virtual server. In the world of cloud computing, you’ll likely deploy applications to various providers such as Heroku, Amazon Web Services, Google Cloud, Microsoft Azure, Rackspace, … and more. Understanding how to do this on your own is incredibly important. This is meant to be an_introductory_ guide; it only notes where you should implement a more secure best practice — you’ll see them next. This all ToDo’s are based on Experience . After this guide you shall be able to spin your first server and host a sweet portfolio. Cool .. eh ?

#### What we gonna see here ? NO Deepshit. Promise

1.  Registering for Digital Ocean
2.  Identify what Droplets are and how to create one
3.  Work with a remote server (droplet) via command line
4.  Provisioning a your virtual server
5.  Deploying an application
6.  FAQ

### Introduction about Digital Ocean

_Digital Ocean_ is a Platform as a Service (PaaS). It is designed to do one thing and to do it well — **create instances of web servers for you to use.** Once you’re out working on a job, you’ll be exposed to a variety of PaaS providers — Amazon’s EC2, Heroku, AppHarbor, and of course, Digital Ocean. Today you’re going to sign up for Digital Ocean, _create a droplet_ (their word for a server), and write an app and put it out for the world to see! Because as cool as it is to show your classmates what you’ve been working on, wouldn’t it be cooler to show your friends and prospective employers? Plus, this will give you a leg up when looking for a job: being able to say I can configure and setup a server is kind of a big deal.That’s kinda cool too :-P

### 1\. Registering for Digital Ocean.

_Digital Ocean requires a credit?debit card on file. Please be aware that if you run out of credits, your card will be billed. But you can use 50$ free_ [_credit_](https://github.com/blog/1900-the-best-developer-tools-now-free-for-students) _to start the server.That’s enough for 3/4th year.Follow instructions and come back here. Try_ [_these_](http://promocodeclub.com/digitalocean-promo-code/) _too_

1.  Browse to [https://www.digitalocean.com/](https://www.digitalocean.com/)
2.  Sign up for a new account on the main page by entering your email address and creating a password.
3.  You’ll be sent a confirmation email (can take up to 5 minutes).
4.  Once you confirm your account, you’ll need to enter in credit/Debit card information. Do so. No worries mate . They won’t charge you even a peny right now.
5.  Now, before doing anything else, select the _profile_ icon and select _billing_.
6.  Enter in the unique code sent to you on email for your free credits! (If went for free credits).

### 2\. Identify what Droplets are and how to create one!

A droplet is a scalable server offered by Digital Ocean. Digital Ocean supports a variety of Linux platforms to develop on (amongst others). A droplet can serve a small website that you use for your own portfolio and it can scale up to host an enterprise application! One of the best things about a droplet is that it can scale — if your site blows up, you can expand the resources it has without needing to create a new server. And best part is Support. They offer very good support using ticket based system.

> Now, we need to locate something to make logging into our droplet easy and secure.

Locate an SSH Key. Read more about SSH [here](https://www.digitalocean.com/community/tutorials/how-to-connect-to-your-droplet-with-ssh)

**Keep your SSH key private. These are meant to be kept secret; kept safe. Don’t share it with strangers.**

We need to create a secure way for you to log into any Droplet that you create. We’re going to use an private key that you already are using on your computer. You should only share private keys with entities you trust! I only share mine with my computers and the servers I run. I even have a copy of mine in my will! They’re private!

**Because I want to make sure that you and only you** — not some hacker in Russia, not some script kiddie in China — has access to your droplet, we’ll use a private key that we’re already comfortable with to connect to the server.

Open up terminal ([Ubuntu](https://www.lifewire.com/ways-to-open-a-terminal-console-window-using-ubuntu-4075024)/[mac](http://www.macworld.co.uk/feature/mac-software/get-more-out-of-os-x-terminal-3608274/)) and enter in the following commands:

List all of the keys in the ./ssh directory. You should see an `id_rsa.pub`. This is your public key.

ls -al ~/.ssh

Open the key in Sublime Text/Any other so we can use it in just a moment.

subl ~/.ssh/id\_rsa.pub     
cat ~/.ssh/id\_rsa.pub  # If no sublime

If you don’t have SSH keys. [Click here](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2) to generate

You are half Done…. Now **Create a Droplet**

1.  Log in to Digital Ocean if you have not already done so.
2.  Select “**Create Droplet**” in the top-right corner.
3.  Give your droplet a name. It can be `my-site` or `mycutesite.com`. The name is just used for reference.
4.  Select the $5/month size for your Droplet (hobby sites use less resources than large production sites)
5.  Select a region .
6.  Ignore the available settings.
7.  Select the Ubuntu 16.04 Operating system.
8.  Select Add SSH Key. You will copy/paste the SSH key that we retrieved just moments ago into the text box. Double check here.
9.  Select Create Droplet.
10.  Annnnndd we wait! Woahh it’s done.

### 3\. Work with a remote server (droplet) via command line. Easiest and best Way.

### Log in and setup a server in a few steps!

1.  Log into the remote server (Droplet)
2.  So you must have allotted a IP. `ssh root@0.0.0.0`
3.  I’m magically logged in because it used my private key from earlier to authenticate who I am!

$ sudo apt-get update && apt-get upgrade #To update and upgrade repo's

1.  Now, explore your file system. `apt install tree` to use the `tree` command.
2.  `apt` is similar to `brew` for Mac OS X - it is a package manager for command line applications.
3.  `pwd` and `cd` around. Feel free to `mkdir` a few files. Things should look _very_ familiar.
4.  If you installed the default version of Ubuntu, you might notice you’re in a `bash` shell.
5.  Consider looking for your `.bash_profile` on this system.
6.  Once you’re done practising your Unix/Linux skills, move on. See here for [bash](https://www.google.co.in/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0ahUKEwiTjYKxyOvQAhWKro8KHRluDvEQFggbMAA&url=http%3A%2F%2Fwww.bash.academy%2F&usg=AFQjCNF22X33zxKcBifC_hitJtY2FxH6Ag)
7.  Like any other computer, a user can `logout` of a system to exit.

**Right now you’re automatically logged in as the root user. This user has all of the power on your server. It is best practice create new users to handle specific tasks (such as one user named dba\_admin for databases and one named webmaster for web servers).**

### 4\. Provisioning your virtual server

We’re going to use the _apt_ package manager to install a few tools. You might remember using `brew` to do this in Mac OS X earlier during the cohort. Because each environment and application is different, we have provided a few scripts in this repository to help make life easier. This guide will contain a few familiar stacks. You should only install _what you need_ and nothing else. Unneccesary software installed on your software can expose security vulnerabilities that you don't need in the first place.

For example see this [http://ayushverma.xyz](http://ayushverma.xyz)

This is being hosted with exactly same configurations over Singapore server.

You can ping it and get public IP of any droplet

### Everyone

> _Install Git_

`apt install git && apt install build-essential`

### Ruby

> _Install Ruby on your linux box_

apt install ruby        # installs ruby  
apt install ruby-dev    # install build tools necessary for building some gems (bcrypt, json, ...)

Verify Ruby is installed by running `ruby -v`.

### MySQL

MySQL requires that you add a link to Oracle’s repositories. It is not hosted publically on `apt`. First, we'll grab that repository, add it to `apt`, and update `apt` so we can find MySQL.

\# get the MySQL repository information  
wget [http://dev.mysql.com/get/mysql-apt-config\_0.8.0-1\_all.deb](http://dev.mysql.com/get/mysql-apt-config_0.8.0-1_all.deb)  
\# install it  
sudo dpkg -i mysql-apt-config\_0.8.0-1\_all.deb  
\# you'll be provided a GUI option; select the default options (5.7)  
\# and exit. this is ok! nothing flashy happens here.  
\# update apt so it can point to the MySQL repository  
sudo apt update

Once that is installed, we’ll install MySQL.

\# install a C library that Ruby uses to build the mysql2 gem with  
apt-get install libmysqlclient-dev  
\# install mysql  
apt install mysql-server

Once installed, we can control MySQL with the following commands:

\# start  
sudo service mysql start  
\# stop  
sudo service mysql stop  
\# info  
sudo service mysql status

To login to MySQL, you may do so with `mysql -p`. `-p` specifies that the user is using a password (so it requests you enter one).

### MongoDB

We recommend using the official installation guide for Ubuntu from Mongodb:[https://docs.mongodb.com/v3.2/tutorial/install-mongodb-on-ubuntu/](https://docs.mongodb.com/v3.2/tutorial/install-mongodb-on-ubuntu/)

### Node.js (LTS v4.0)

This version of node is the first LTS release post the io.js merger. Usage of many Javascript 2015 (ES6) features requires`'use strict'` or are not available at all. Node isn't included with the standard list of applications available in `apt`. We'll need to add it ourselves:

curl -sL [https://deb.nodesource.com/setup\_4.x](https://deb.nodesource.com/setup_4.x) | sudo -E bash -

Once completed, we can then install Node by running:

apt install nodejs

You can verify that Node and _npm_ have been installed by running the following commands.

npm -v  
node -v

### Node.js (LTS v6.0)

This version of node contains most Javasript 2015 (ES6) features availability directly in Node without the need of transpiling. Node isn’t included with the standard list of applications available in `apt`. We'll need to add it ourselves:

curl -sL [https://deb.nodesource.com/setup\_6.x](https://deb.nodesource.com/setup_6.x) | sudo -E bash -

Once completed, we can then install Node by running:

apt install nodejs

You can verify that Node and _npm_ have been installed by running the following commands.

npm -v  
node -v

### 5\. Deploying an application

This is some serious and important thing to be taken care of !

Applications on a server are ran just like any other application on your laptop — through terminal commands. To make an application run on your virtual server, you must consider how it runs on your laptop. Does it need a database? Is that database running? Did you change your environment variables to reflect the different SQL users between your laptop and server? There are a lot of things to consider when deploying an application. Before diving into specific platforms, here are some questions to consider:

*   Is Git installed?
*   Have you cloned your application to your server yet?
*   Does my application require a database? Is it the same type on my computer and server?
*   Have I created appropriate SQL users for my database?
*   Have I updated my config files and environment variables to point to the proper server?
*   Have I removed all breakpoints and set my app to run in production mode (vs development)?
*   Have I ran all database related tasks (Rake, Gulp, …)?

Now, we need to create a directory to store all of our web applications.

cd /        # root directory  
cd /var     # var dir  
mkdir www   # creates /var/www  
pwd         # /var/www

Clone any applications you’d like to run using Git in the `/var/www` folder. This is the typical location for storing web applications on Debian (Ubuntu) linux servers. This location is one of the defaults that has been constant throughout decades of web development.

### Deploying Node Applications

To deploy a Node application, clone your Git project into your `/var/www/` folder and change into it. Install the required modules for your application:

npm install

Next, install pm2, a process monitor for Node applications.

npm install pm2 -g

Finally, you can start your application by running the script specified for `npm start` inside of your `package.json`.

pm2 start app.js -x -- --prod

You can stop your application, too (for maintenance and upgrading):

pm2 stop app.js -x -- --prod

### FAQ

Alright some small things that we might have missed !

How do I use Nano?

*   Exit — ctrl-x
*   Prompts you to save — select Y or N
*   Prompts you to confirm where saving. Either edit or press return/enter.

How do I exit vi?

*   `:` + `q!`
*   Forces an exit without a save

Digital Ocean CLI

*   Check [here](https://github.com/digitalocean/doctl)

All scripts used in this article are available at G[_ithub_](https://github.com/Ayushverma8/Ultimate-Guide-to-Cloud).

By [Ayush Verma](https://medium.com/@Ayushverma8) on [December 11, 2016](https://medium.com/p/c78927b50a82).

[Canonical link](https://medium.com/@Ayushverma8/ultimate-guide-to-use-cloud-services-c78927b50a82)

Exported from [Medium](https://medium.com) on July 6, 2019.