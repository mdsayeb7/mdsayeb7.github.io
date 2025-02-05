---
title: '.ht access code'
date: 2023-12-13T12:09:00.001+06:00
draft: false
url: /2023/12/ht-access-code.html
tags: 
- wordpress
---

\# BEGIN WordPress

  

RewriteEngine On

RewriteRule .\* - \[E=HTTP\_AUTHORIZATION:%{HTTP:Authorization}\]

RewriteBase /

RewriteRule ^index\\.php$ - \[L\]

RewriteCond %{REQUEST\_FILENAME} !-f

RewriteCond %{REQUEST\_FILENAME} !-d

RewriteRule . /index.php \[L\]

  

\# END WordPress