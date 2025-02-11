---
title: 'enable shell_exec function to server'
date: 2024-04-04T03:08:00.001+06:00
draft: false
tags: ['server']
---

 The shell\_exec function allows PHP scripts to execute commands via the shell, which can be useful for certain tasks but also poses security risks if not managed properly

  

edit the php.ini file (on cpanel it’s /usr/local/lib/php.ini)

search for the line that says “disable\_functions”

remove shell\_exec from this line

Save the file, and restart apache.