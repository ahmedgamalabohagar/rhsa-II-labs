# Lab 6: Scheduled-jobs

## Objective

- Learn how to automate repetitive tasks in Linux using job scheduling tools.

- Configure and manage recurring jobs using cron and system-wide /etc/cron.* directories.

- Schedule one-time jobs using the at command.

- Verify and monitor scheduled jobs using crontab -l, atq, and system logs.

- Understand how to redirect output and errors from scheduled jobs to log files.

- Test, troubleshoot, and remove scheduled jobs effectively

## Steps

  ### 1. create cron job write date in /home/ahmed/mycron.log every minute.
- edit crontab

```bash
     crontab -e  
```

- add this line to the file
  
```bash
    * * * * * date >> /home/ahmed/mycron.log
```
- display /home/ahmed/mycron.log content

 
```bash
     cat /home/ahmed/mycron.log
```


 [![](images/1.PNG)](images/1.PNG)

 

  ### 2. create job  using at execute command run after two minutes.
  - run this command
  ```bash
    echo "echo hello >> ~/newfile.txt | at now + 2 minutes "
  ```
  - list scheduled jobs
```bash
    atq
```
[![](images/2.PNG)](images/2.PNG)

  - display ~/newfile.txt content

[![](images/3.PNG)](images/3.PNG)

  ### 3. create cron System-wide in /etc/cron.d .
- create new file /etc/cron.d/newjob 
```bash
  vim /etc/cron.d//newjob
```
- add this line 
```bash
* * * * * root cal >> /var/log/mycron.log
```
- change file owner to root
```bash
chown root:root /etc/cron.d/newjob
```
- display /var/log/mycron.log content

  [![](images/5.PNG)](images/5.PNG)

## Challenge:
- When creating the cron job, it didn’t run as expected.

### Cause:
- The file inside /etc/cron.d/ was not owned by root:root.

### Details:
- System-wide cron files must be owned by the root user.
- When the ownership is incorrect, the cron daemon skips the job and logs an error 

### Fix:
- Changed the file owner to root using:

```bash
sudo chown root:root /etc/cron.d/newjob
```

- After that, the cron job executed successfull








