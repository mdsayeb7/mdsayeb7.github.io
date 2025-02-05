---
title: 'Phpmyadmin error hide'
date: 2024-03-11T19:34:00.004+06:00
draft: false
url: /2024/03/phpmyadmin-error-hide.html
tags: 
- server
---

 The best way to turn off Phpmyadmin errors is to go go config.inc.php and set (or comment out ie removing the // lines in front of the value, which is set to "ask" by default.)

```
$cfg['SendErrorReports'] = 'never';

```

Hit save and that's it.

More info [https://docs.phpmyadmin.net/en/latest/config.html#cfg\_SendErrorReports](https://docs.phpmyadmin.net/en/latest/config.html#cfg_SendErrorReports)