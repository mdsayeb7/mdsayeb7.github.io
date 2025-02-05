---
title: '.htaccess'
date: 2023-12-08T20:33:00.000+06:00
draft: false
url: /2023/12/htaccess.html
tags: 
- wordpress
---

 https://pagespeed.web.dev/

```
https://securityheaders.com/
https://www.webpagetest.org/
https://hackertarget.com/wordpress-security-scan/


# BEGIN WordPress
# The directives (lines) between "BEGIN WordPress" and "END WordPress" are
# dynamically generated, and should only be modified via WordPress filters.
# Any changes to the directives between these markers will be overwritten.
<IfModule mod\_rewrite.c>
RewriteEngine On
RewriteRule .\* - \[E=HTTP\_AUTHORIZATION:%{HTTP:Authorization}\]
RewriteBase /
RewriteRule ^index\\.php$ - \[L\]
RewriteCond %{REQUEST\_FILENAME} !-f
RewriteCond %{REQUEST\_FILENAME} !-d
RewriteRule . /index.php \[L\]
</IfModule>

# END WordPress

# BEGIN Headers Security Advanced & HSTS WP 5.0.28
<IfModule mod\_headers.c>
Header set Access-Control-Allow-Methods "GET,POST"
Header set Access-Control-Allow-Headers "Content-Type, Authorization"
Header set Content-Security-Policy "upgrade-insecure-requests;"
Header set Cross-Origin-Embedder-Policy "unsafe-none; report-to='default'"
Header set Cross-Origin-Embedder-Policy-Report-Only "unsafe-none; report-to='default'"
Header set Cross-Origin-Opener-Policy "unsafe-none"
Header set Cross-Origin-Opener-Policy-Report-Only "unsafe-none; report-to='default'"
Header set Cross-Origin-Resource-Policy "cross-origin"
Header set Permissions-Policy "accelerometer=(), autoplay=(), camera=(), cross-origin-isolated=(), display-capture=(self), encrypted-media=(), fullscreen=\*, geolocation=(self), gyroscope=(), keyboard-map=(), magnetometer=(), microphone=(), midi=(), payment=\*, picture-in-picture=(), publickey-credentials-get=(), screen-wake-lock=(), sync-xhr=(), usb=(), xr-spatial-tracking=(), gamepad=(), serial=()"
Header set Referrer-Policy "strict-origin-when-cross-origin"
Header set Strict-Transport-Security "max-age=63072000"
Header set X-Content-Security-Policy "default-src 'self'; img-src \*; media-src \* data:;"
Header set X-Content-Type-Options "nosniff"
Header set X-Frame-Options "SAMEORIGIN"
Header set X-XSS-Protection "1; mode=block"
Header set X-Permitted-Cross-Domain-Policies "none"
</IfModule>
# END Headers Security Advanced & HSTS WP


# protect .htaccess
<Files ~ "^.\*\\.(\[Hh\]\[Tt\]\[Aa\])">
	Order allow,deny
	Deny from all
	Satisfy all
</Files>

# protect wpconfig.php 
<files wp-config.php> 
  order allow,deny 
  deny from all 
</files>

#directory browsing block
Options All -Indexes

# Block WordPress xmlrpc.php requests
<Files xmlrpc.php>
order deny,allow
deny from all
</Files>

# BEGIN block author scans
RewriteEngine On
RewriteBase /
RewriteCond %{QUERY\_STRING} (author=\\d+) \[NC\]
RewriteRule .\* - \[F\]
# END block author scans


# protect the .htaccess
<files .htaccess> 
  order allow,deny 
  deny from all 
</files>


{{{{{{in wp-Content
create .htaccess
paste code}}}}}}


# wp-content access deny
Order deny,allow
    Deny from all
    <Files ~ "".(xml|css|jpe?g|png|gif|js)$"">
    Allow from all
    </Files>



> create a new .htaccess file in wp-content/uploads directory & put the codes there:
# uploads directory access deny
<Files \*.php>
deny from all
</Files>
# Block executables
<FilesMatch ""\\.(php|phtml|php3|php4|php5|pl|py|jsp|asp|html|htm|shtml|sh|cgi|suspected)$"">
    deny from all
</FilesMatch>


wordfence
62ae96abbc505f813e0de5ca850391957685866faebd87550a664a902773535f83a07d71a729955aa513322a0e958520b1de578b5a932d0c2b1508a1c6674795
```