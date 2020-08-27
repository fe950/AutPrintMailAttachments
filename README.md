# AutPrintMailAttachments 



This is a shell script for automatically printing email attachments.
It's 99% a copy of thomasX/autoprint work, I just made it work with gmail in 2020 and make it easier to get started for beginners.




#### how does it work
In this configuration it's setup for gmail, with imap, printing pdf to a cups printer
It uses fetchmail to download new attachments, leave messages on server and mark it read. 
Then using uudeview to render files and print it with lpr
It can be scheduled to run at intervalls with cron.


#### files used:
```
autoprint
autoprint.cfg
workingdir/logfile.log
```


 
#### dependencies that needs to be installed
 ```
 fetchmail
 uudeview
 lpr
 ```
          
       
#### config file

The config file has 1 configline containing the following parameters:         
   ```
    param 1:  mail-server 
    param 2:  server type (imap/pop3)
    param 3:  ssl (Y/N)       (needed for gmail imap, no need to download certificate)    
    param 4:  mail-address    (use full email adress for gmail, username@gmail.com)
    param 5:  password         
    param 6:  printserver     (hostname, ip, to cups server, postscript printer)
    param 7:  printqueue      (name of printer in cups)   
    param 8:  attachment types (.pdf.jpg.gif.png)         
    param 9:  copies           (1,2,3...)                           
    param 10:  keep mail on Server (Y/N)                  
    param 11:  folder  (optional parameter if folder is set only this mail-folder will be downloaded  
   ```
    ```
    ####This is config file
   # mailserver servertype ssl e-mail  password  lprhost lprqueue attachmenttypes copies keepOnServer imapFolder    
       imap.gmail.com imap ssl username@gmail.com Your¤#"SecrtPswd 127.0.0.1 Brother_Printer .pdf 1 Y
       ```
    

#### other things to do to make it run
```
Edit 2 lines in script to correct paths.
Edit line starting with "autoprintBaseDir="
Edit line in script that starts with "echo "set logfile"
```

#### make it run automatically
crontab -e

Add this line to the buttom to make it run every 10 minutes (I read that google will make you log in with a captcha if you run it more frequently)
```
*/10 * * * * /pathto/AutPrintMailAttachements /path to configfile.cfg
```


#### logging:    
    
   Logging is done to workdir/logfile.log
    
 Following is from original author, I dont understand that it so I just leave it here untuched. :)
 I think its not used when I logg to a single file in workdir.
 
we use syslog logging... if you want to put all printlogging to a customized file add the following line to /etc/rsyslog.cong:
:msg, contains ," autoprint-logging:"  /var/log/autprint.log

Attention: don't forget to config the logrotate ! 

   
   
