### NOTE: Some of the commands will be in the Windows-Fundamentals file

## Commands for Windows cmd.exe
set - checks the path you are on and returns it

ver - spits out the version of your machine

systeminfo - gives you a lot of information about your system, such as hostname, OS information, and more.

help - gives you help for a specific command
### Network commands
ping - allows you to check the connectivity of another device to yours 

tracert - This will do the same thing as ping, but will also print the route the packets took

nslookup - looks up a domain or host and returns its IP address

netstat - This command displays currently connected networks and listening ports.
### File Disk Management Commands

cd - allows you to display the current directory. Also allows you to change your directory

dir - allows you to view child directories. /a will show hidden directories, and /s will show current and subdirectories

tree - another way to show all of the directories 

mkdir - allows you to make a new directory

rmdir - allows you to remove a directory

type - allows you to view text files

copy - this command allows you to copy files from a location

move - allows you to move files


del - allows you to delete a file

"*" - allows you to copy or move multiple files

### Task and Process Management Commands

tasklist - prints out all of the running processes. /<"FI "imagename eq _Inserttaskname_"> will allow you to filter this 

taskkill /PID - allows you to kill a process

### Other Commanded to Know

chkdsk - checks the file system and disk volumes for errors and bad sectors

driverquery - displays a list of installed device drivers

sfc /scannow - scans system files for corruption and repairs them if possible

## Powershell

### Basic Commands
Get-Content - retrieves the content of a file and displays it 

Set-Location - changes the current working directory

Get-Command - gets all of the commands. can use the -CommandType to filter this

Get-Help - running this command, followed by another command, will display information about that command. -Examples will show you examples

Get-Alias - this will show other ways to type commands. This is so people can transition to PowerShell with ease

Find-Module - will help you find a module 

Install-Module - will allow you to install a module

### Moving Around PowerShell
Get-ChildItem - list the files and directories in a location using the -Path parameter

New-Item - creates a new item. Will need to specify the location with -Path

Remove-Item - lets you remove an item

Copy-Item - lets you copy an item

Get-Content - lets you see in a file like the commands type or cat

### Ping, Filter, Sort 
#### Note all | commands have the same input instructions as the first example
| Sort-Object - can be used to sort a directory ex: "Get-ChildItem | Sort-Object Length"

| Where-Object - allows you to filter and return objects based on criteria you specify

-Like - Another way to filter

| Select-Object - used to select specific properties of objects or return specific objects

| Select-String - allows you to search files for certain words, like grep

### Operators in PowerShell
-ne - not equal 

-gt - greater than

-ge - greater than or equal to 

-lt - less than 

-le - less than or equal to

### System Commands
Get-ComputerInfo - Gets a variety of system information

Get-LocalUser - list all the local user accounts 

Get-NetIPConfiguration - same thing as ipconfig gets information about network interfaces on the system

Get-NetIPAddress - gets information specifically about IP addresses

Get-Process - returns running processes 

Get-Service - gets information about the status of services on a machine

Get-NetTCPConnection - displays current TCP connections

Get-FileHash - can get the hash of a specified file

Invoke-Command - This allows you to invoke commands, allowing for automation 
