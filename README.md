# bash-scripts
## LunixStatus
This script provides the following functionalities:
a. A welcome screen showing the current date, current user, Linux version,
and a list of options which are:
   Option 1: List the running process
   Option 2: Check the memory status and free memory in the RAM
   Option 3: Check the hard disk status and free memory in the HDD.
   Option 4: Check if apache is installed and if yes return its version
   Option 5: Exit
b. When the user selects an option,
   i. The result is displayed
   ii.The view also shows three options,
      The first option is to back to the main view
      The second option is to update the view
      The third option is to exit.
h. The script also accepts the following arguments:
   i. LunixStatus p: it shows the output of option 1 and exit.
   ii. LunixStatus r: it shows the output of option 2 and exit.
   iii. LunixStatus h: it shows the output of option 3 and exit.
   iv. LunixStatus a: it shows the output of option 4 and exit.
   v. Or any mix such as LunixStatus p r a : it shows the output of
      options 1, 2, and 4, then exit.
--------------------------------------------------------------------------------
To run the script:
1. You need to copy the script to a file with .sh extension.
e.g:
```shell
nano LunixStatus.sh
```
2. Set execute permission using:
```shell
chmod +x LunixStatus.sh
```
3. You can then run the script using:
```shell
./LunixStatus.sh
```
or
```shell
bash LumixStatus.sh
```
**Additional step:** You can run the script as a command by adding it to Linux PATH:
Move the shell script to a directory that is already in your PATH
You can move the shell script into any of the directories which are listed in response to the ```echo $PATH``` command. The best practice is to put your personal shell scripts into the /usr/local/bin directory:
```shell
sudo mv LunixStatus.sh /usr/local/bin/
```
You can check that the file has been added by running:
```shell
cd /usr/local/bin/
ls
```
Now you can run the script as a command by just typing the name of the file.


##Deployment
This script deploys a static web application from a fixed github repo link. It will install git, curl, and latest apaache2 version, then it deploys the website and add the script to the cronJob to be run daily at midnight to fetch the latest code from the GitHub rep and update the website. The script also logs all steps, and store the logs in a file called _install_{current date}.log_.
