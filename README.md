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

5) Time to edit the Homestead.yaml file. Go to the C:\Users\USER_NAME\Homestead directory. Now open the Homestead.yaml file with any text editor (I used Sublime Text, works just fine). As you go through the file you will notice these lines that correspond to your SSH keys. Make sure they align with the public and private key pair you would like to use. 
        
        authorize: c:/Users/USER_NAME/.ssh/id_rsa.pub
        keys:
        — c:/Users/USER_NAME/.ssh/id_rsa
        
        *** NOTE: be sure you use lowercase for our drive name (c) versus (C) and forward slashes (/) instead of backslashes (\) in this           instance
        
Next we will be mapping our desired folder/repo to be used to our vagrant folder, which will essentially be a copy of our local folder like so: 

        folders:
        — map: c:/Users/dkhalam/Projects
        to: /home/vagrant/Projects
        
        ** Make sure you are not missing the colon after the c, as this silly mistake held me back the first time I tried this. 
        
You can use any folder name here, but for simplicity I have them as the same name. Any changes to one will be automatically routed and applied to the other. 

Next we map our site that we will point to in our hosts file to the public folder in our project. So when you type local.project.com it will serve up our site!

        sites:
        — map: local.project.com
        to: /home/vagrant/Projects/Project1/public


6) We're getting to the point where we need to edit our hosts file and add our IP and desired site name. The hosts file can be found in C:\Windows\System32\drivers\etc\ folder, open it in Sublime or any other text editor in administrator mode, and add a new line for our new local site like so:
        
        192.168.10.10 local.project.com
        
        *** If you want to add another site, just append a dedicated new line to the bottom, that easy!

7) Now we can run the 'vagrant up' and 'vagrant halt' commands to start and stop our instance. To do so, we have to always run these commands from the Homestead directory. 

Here's a link to helpful vagrant commands: https://www.vagrantup.com/docs/cli/

8) Run 'vagrant ssh' command to login to vagrant. Type 'ls' to see a list of the contents of the current directory. You should notice the Projects folder there. Cd to Projects. To add a specific project, type this command 'composer create-project --prefer-dist laravel/laravel Project1'.

This last command can take some time so be patient!

9) To be safe and make sure we have all our dependencies, still SSH'd in, type 'composer install' at the root of your project directory. 

Then, change env.example to .env. You can copy the contents from env.example easily via sublime and save it as a new file called '.env'. 

Finally, run this command at the root of your project directory: 'php artisan key:generate' to set the APP_KEY value in your new .env file.

10) Everything should be set, theoretically all our bases are covered, but ultimately each device is different. Type 'local.project.com' into the browser and with luck we will see our site!

Thanks for following along, hope this was helpful!



