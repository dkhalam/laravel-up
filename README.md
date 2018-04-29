# laravel-up
Step-by-step Windows 10 guide to help you create a local Laravel project via Homestead

Laravel is a fantastic resource for building modern, dynamic web apps. Best of all, it is a free, open source PHP framework and can be fully taken advantage of within local development using Homestead. Use this guide to equip yourself with a local version of your site and get to testing out your features before you push them live. This guide will be especially beneficial for those on a Windows machine. 

Full disclosure, Eaiman Shoshi has a brilliant guide on Medium that I used, but I had to make a few amendments that you may find helpful to getting the full picture.

*** Please be sure to type in all commands instead of copy and pasting to ensure ultimate accuracy ***

https://medium.com/@eaimanshoshi/i-am-going-to-write-down-step-by-step-procedure-to-setup-homestead-for-laravel-5-2-17491a423aa

Here is a link to the official laravel documentation as well: https://laravel.com/docs/5.2/homestead

PREREQUISITES
One note that Eaiman made that I did not personally have an issue with was enabling hardware virtualization. Refer to this link for more info on the subject: https://www.howtogeek.com/213795/how-to-enable-intel-vt-x-in-your-computers-bios-or-uefi-firmware/

Download and install Git Bash.
Git Bash download link: https://git-scm.com/download/win

Download and install virtualbox and vagrant. 
VirtualBox download link: https://www.virtualbox.org/wiki/Downloads
Vagrant download link: https://www.vagrantup.com/downloads.html

It is very important that you restart your PC after these downloads and installs to ensure changes are processed. Installs may take a while so be patient with this step. 

1) Open Git Bash in Administrator mode and run this command: 'vagrant box add laravel/homestead' ... This will take a few minutes. 

2) Type 'cd ~' to make sure you are in your home (C:\Users\USER_NAME) directory. Now run 'git clone https://github.com/laravel/homestead.git Homestead' to clone the homestead repository into a Homestead folder within your home directory. 

3) Run the following commands one by one to create your Homestead.yaml configuration file in your Homestead folder, which will be a critical piece to this puzzle. 
    1. 'cd Homestead'
    2. 'bash init.sh'

4) Check for an SSH Key or add your SSH Key if it doesn't already exist. I have always referenced Git's SSH tutorial for it's wonderful clarity. 
    Check for existing keys: https://help.github.com/enterprise/2.13/user/articles/checking-for-existing-ssh-keys/
    Generating a new SSH key: https://help.github.com/enterprise/2.13/user/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/
    Adding a new SSH key to your GitHub account: https://help.github.com/enterprise/2.13/user/articles/adding-a-new-ssh-key-to-your-github-account/
    
    Check the .ssh file in your C:\Users\USER_NAME\ directory to see your public and private key pair(s)

5) Time to edit the Homestead.yaml file. 

6)

7)

8)

9)

10)



