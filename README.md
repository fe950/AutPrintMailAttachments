# autoprint
autoprint is a shell script for automatically printing all new email-attachments from gmail to a printer.

Connects to gmail with fetchmail using imap and download new pdf atachments and prints them to a cups printer.
Leave email at server and mark them as read.
Also support pdf,jpg,png, change filetypes in autoprint.cfg
Supported printers: all postscript printers ... you can add multiple printer-types with cups
Supports pop3 and imap and imap with ssl
       


files: autoprint .... shell script
       autoprint.cfg ... config file

the config file has 1 configline per e-mail containing the following parameters:         
    param 1:  mail-server         
    param 2:  mail-address         
    param 3:  password         
    param 4:  printserver     
    param 5:  printqueue         
    param 6:  attachment types (.pdf.jpg.gif.png)         
    param 7:  copies                                      
    param 8:  keep mail on Server (Y/N)                  
    param 9:  folder  (optional parameter if folder is set only this mail-folder will be downloaded  
    
    
# logging:    
    
we use syslog logging... if you want to put all printlogging to a customized file add the following line to /etc/rsyslog.cong:
:msg, contains ," autoprint-logging:"  /var/log/autprint.log

Attention: don't forget to config the logrotate ! 


   
   
   
