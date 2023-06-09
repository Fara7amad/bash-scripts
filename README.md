# bash-scripts
## LunixStatus
--------------------------------------------------------------------------------
This script provides the following functionalities:
- A welcome screen showing the current date, current user, Linux version, and a list of options which are:
   - Option 1: List the running process
   - Option 2: Check the memory status and free memory in the RAM
   - Option 3: Check the hard disk status and free memory in the HDD.
   - Option 4: Check if apache is installed and if yes return its version
   - Option 5: Exit
- When the user selects an option,
   - The result is displayed
   - The view also shows three options,
      - The first option is to back to the main view
      - The second option is to update the view
      - The third option is to exit.
- The script also accepts the following arguments:
   - LunixStatus p: it shows the output of option 1 and exit.
   - LunixStatus r: it shows the output of option 2 and exit.
   - LunixStatus h: it shows the output of option 3 and exit.
   - LunixStatus a: it shows the output of option 4 and exit.
   - Or any mix such as LunixStatus p r a : it shows the output of options 1, 2, and 4, then exit.
  
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
bash LunixStatus.sh
```
**Additional step:** 
You can run the script as a command by adding it to Linux PATH:
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


## Deployment
----------------------------------------------------
This script deploys a static web application from a fixed github repo link. It will install git, curl, and latest apaache2 version, then it deploys the website and add the script to the cronJob to be run daily at midnight to fetch the latest code from the GitHub rep and update the website. 

The script also logs all steps, and store the logs in a file called _install_{current date}.log_.

The cron job has been added by:
```shell
(crontab -l ; echo "0 0 * * * cd /root/SimpleApacheApp && git pull") | crontab -
```
The syntax ```crontab -l``` is used to list the current cron jobs for the user. ```echo "0 0 * * * cd /root/SimpleApacheApp && git pull"``` adds a new cron job to the existing list of cron jobs, which is to run the command ```"cd /root/SimpleApacheApp && git pull"``` at midnight every day "(0 0 * * *)".

The | operator is used to redirect the output of the first command ```crontab -l``` to the input of the second command ```echo "0 0 * * * cd /root/SimpleApacheApp && git pull"``` using a pipe. Finally, the ```| crontab -``` command saves the new cron job list to the user's crontab file.

To test that the script worked successfully, you can use the ```curl``` command or by visiting the website itself:
```shell
 hostname -I
```
The output will be the server's ip.
