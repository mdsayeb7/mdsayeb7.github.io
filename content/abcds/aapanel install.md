---
title: 'aapanel Install'
date: 2024-02-21T13:23:00.029+06:00
draft: false
tags: ['server']
---

[![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjLEXwSYAdPlc6zlvkyzkrfyNKS3YlXECZtmBc_dgiefbRdns4CdcXQkwTlntZwdS6QIO24f2JJfSxcexnEwwTCD_LCn4k-vw9QqDDiQnCkgZY80AS_dTOh6EdLuCTjWm9eTW7McKYoRF9wdFZ8Wn938foM4VNvFZpb3447IfhBE5lB9O_VMJBaA9aJUu-2/w672-h364/Screenshot_21-2-2024_13296_demo.aapanel.com.jpeg)](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjLEXwSYAdPlc6zlvkyzkrfyNKS3YlXECZtmBc_dgiefbRdns4CdcXQkwTlntZwdS6QIO24f2JJfSxcexnEwwTCD_LCn4k-vw9QqDDiQnCkgZY80AS_dTOh6EdLuCTjWm9eTW7McKYoRF9wdFZ8Wn938foM4VNvFZpb3447IfhBE5lB9O_VMJBaA9aJUu-2/s1794/Screenshot_21-2-2024_13296_demo.aapanel.com.jpeg)

  

1-  
sudo su -

  
2-  
sudo apt update && sudo apt upgrade -y

  
reboot (recommended)

  
3-

URL=https://www.aapanel.com/script/install\_6.0\_en.sh && if \[ -f /usr/bin/curl \];then curl -ksSO "$URL" ;else wget --no-check-certificate -O install\_6.0\_en.sh "$URL";fi;bash install\_6.0\_en.sh aapanel

  
4- (settings)  
bt

  

  

for PHP   
Compiled

Module name: mbstring  
Module parameter:- \--enable-mbstring

  

hide PHPMyAdmin errors  
config.inc.php 

$cfg\['SendErrorReports'\] = 'never';

To disable strict\_trans\_tables, you simply need to remove it from the list. So your sql-mode setting should look like:  
sql-mode=NO\_ENGINE\_SUBSTITUTION

Once you've made this change, save the file and restart the MySQL service for the changes to take effect.

  

While installing add any CODE to code field, then go to /install/ folder open index.php go to line 71 and change this line :  
  
from : $ServerErrors\[\] = $p\['ERROR\_NAME'\]:  
to : $can = 1;