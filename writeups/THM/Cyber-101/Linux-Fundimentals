# Linux Fundamentals 1, 2, and 3

## Course Objective
Learn basic Linux commands and how to navigate a CLI

## Key Commands Used
Echo - output any text provided
whoami - find out what user I am currently logged in as
ls - list files in the current directory (-a shows all hidden directories -l shows permission and owner)
cd - change directory 
pwd - print working directory
cat - open a file to read
find - find a folder for us (NOTE typed find -name <name of file>)
grep - allows you to search a file for specific contents (-R is recursive) 
-- help - using this with a command will show all the possible options for that command
man - using man and then a command brings up the manual for that command
touch - create a file
mkdir - creates a folder
cp - copy a file or folder
mv - move a file or folder
rm - remove a file or folder (-R is needed to remove a directory
file - determine the type of file
su - switching between users (-l starts the shell as an actual login)
ssh - log into the attack machine (looks like ssh <username>@<ip>)
nano - allows you to create or edit a file
VIM - a much more advanced file editor
wget- allows you to download files via HTTP
scp - secure copy file
ps - shows the running processes for the user (do ps aux for all users)
top - gives you real-time stats about what is running on your computer
kill - kills a process
systemctl - this command allows us to interact with the systemd process/daemon.
SIGTERM - Kill the process, but allow it to do some cleanup tasks beforehand
SIGKILL - Kill the process - doesn't do any cleanup after the fact
SIGSTOP - Stop/suspend a process
crontab -e - Lets you automate files to backup or run on startup and other things
apt - The apt command is a part of the package management software also named apt. 
add-apt-repository - lets you add a repository 


## Common Linux Operators
- & allows you to run commands in the background of your terminal
- && This allows you to combine commands (NOTE: command one will only run if command 2 runs) 
- > This operator is a redirector. This means that we can take the output of a command and direct it elsewhere
- >> Same as > but appends the output rather than replacing it

## Read Write Execute permissions
Example of permissions: rwxrw--r--

R = Read value = 4
W = Write value = 2
X = Execute value = 1

First 3 = owner
second 3 = group
thrid 3 = others

## Common Directories
/etc - root directory
/var - This folder stores data that is frequently accessed or written by services or applications running on the system
/tmp - this folder stores temporary data 

## How to Host a Web Server (allows you to download files from one machine to another)
Using Python 3, we can host a web server. Here are the following steps
1. Start up Python 3 on one terminal using (python3 -m http.server)
2. From a different machine, you can now download a file using this command (wget http://<ip of machine running Python>:8000/myfile
3. Once done, use CNTRL C to stop

## Looking At Logs 
Going to the /var/logs can let you view helpful logs



