---
title: 'How to unregister all service worker, from mobile and pc (Edge + Chrome)'
date: 2025-01-17T03:05:00.029+06:00
draft: false
url: /2025/01/how-to-unregister-all-service-worker.html
---

For PC
------

  

check all service workers (mobile and pc)  
  
edge://serviceworker-internals/ or chrome://serviceworker-internals/  
  
F12 for open dev tools, in the console paste and hit enter.  
  

[![](https://blogger.googleusercontent.com/img/a/AVvXsEjR5PC72pL-tfloojOaYH6_d5TnAYaKH6p2ayzs_pZUtQVLRkTTH7bfhUZNo2C0z7iL_-opxTs9HdvH0xW3FgTwdWUFWLLog3acXhi-3N1th6G8rfWT0qqW45_KfM5HwJz733DjjvEhOYKKCx-rZYO2DRiYN0Gb2jG4OCr91JxZjDFxl0wGkqC6q0zRJz72)](https://blogger.googleusercontent.com/img/a/AVvXsEjR5PC72pL-tfloojOaYH6_d5TnAYaKH6p2ayzs_pZUtQVLRkTTH7bfhUZNo2C0z7iL_-opxTs9HdvH0xW3FgTwdWUFWLLog3acXhi-3N1th6G8rfWT0qqW45_KfM5HwJz733DjjvEhOYKKCx-rZYO2DRiYN0Gb2jG4OCr91JxZjDFxl0wGkqC6q0zRJz72)

  
" document.querySelectorAll(".unregister").forEach(item=>item.click()) "  

For Mobile
----------

**Enable Developer Mode & USB Debugging on Your Phone:**

  

1- Go to Settings > About phone.

  

2- Tap on Build number seven times to enable Developer Mode.

  

3- Go to Settings > Developer options.

  

4- Enable USB debugging.

  
**Connect Your Phone to Your Computer:**

  

Use a USB cable to connect your phone to your computer.

### **Setup PC**

**Enable Remote Diagnostics on the Target Machine:**

  

1- On the target Windows machine, open Settings.

  

2- Go to Update & Security > For developers.

  

3- Enable Device Portal and Device Discovery.  
  
  

[![](https://blogger.googleusercontent.com/img/a/AVvXsEie_23N9c_j3w5bZDL2yxKb1-jIX91xBwn2yzx9jnv0KYtujmRnAjIzrTzRCQ-GEXDvw2wFezcJsR5RbdTPDZpsJvNsOPj0yxUFPD-8Wmsd9u793102Ied-8LRuzxJwnKF-CDhV2nXB2pg2LnrtgujdV-zC7-wXRLhFRapwR298sLEGBetAHTASvY8mY9Ss)](https://blogger.googleusercontent.com/img/a/AVvXsEie_23N9c_j3w5bZDL2yxKb1-jIX91xBwn2yzx9jnv0KYtujmRnAjIzrTzRCQ-GEXDvw2wFezcJsR5RbdTPDZpsJvNsOPj0yxUFPD-8Wmsd9u793102Ied-8LRuzxJwnKF-CDhV2nXB2pg2LnrtgujdV-zC7-wXRLhFRapwR298sLEGBetAHTASvY8mY9Ss)

  

[![](https://blogger.googleusercontent.com/img/a/AVvXsEhYlxL4TaORXIkrhBOPPU_CHjQ6hXDmiW4Tf-JfsxjAKEa1tdWPsPd5oR62sO1s7aPoZ4cGIWgEs1kVKEaKLP25CjZ62epzf12tld-QI5K34DTrrqi4oMq4udUdNL3wAB1bmvn0bEAAqnnaN6NQlaa37CnQ05zt_E4v2SclgEHBZ1IvskuzlVjb1c68WR-N)](https://blogger.googleusercontent.com/img/a/AVvXsEhYlxL4TaORXIkrhBOPPU_CHjQ6hXDmiW4Tf-JfsxjAKEa1tdWPsPd5oR62sO1s7aPoZ4cGIWgEs1kVKEaKLP25CjZ62epzf12tld-QI5K34DTrrqi4oMq4udUdNL3wAB1bmvn0bEAAqnnaN6NQlaa37CnQ05zt_E4v2SclgEHBZ1IvskuzlVjb1c68WR-N)

  
**Connect to the Remote Device:**

  

In Microsoft Edge on your computer, go to edge://inspect/#devices  
  

open the console and run   
" document.querySelectorAll(".unregister").forEach(item=>item.click()) "  

For Chrome 
-----------

[https://dev.to/dev0x0/using-google-chrome-console-on-any-mobile-device-9ec](https://dev.to/dev0x0/using-google-chrome-console-on-any-mobile-device-9ec)  
  
remove cookies: edge://settings/content/cookies/siteData?searchSubpage