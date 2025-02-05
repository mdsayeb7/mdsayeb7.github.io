---
title: 'Making Your PWA Work Across All Pages'
date: 2025-01-18T23:28:00.046+06:00
draft: false
url: /2025/01/making-your-pwa-work-across-all-pages.html
---

This guide explains how to make your Progressive Web App (PWA) functional across all pages, even if you don't add the `<link rel="manifest" href="manifest.json">` manually to every page.

1\. Add the Manifest File
-------------------------

Create a manifest.json file in the root directory of your project. (you can use this: [https://pwa.zneloy.site/](https://pwa.zneloy.site/))

2\. Add a Service Worker (sw.js)
--------------------------------

Create a sw.js file in the root directory of your project. Use the following code:

self.addEventListener('install', (event) => { console.log('Service Worker installed'); }); self.addEventListener('activate', (event) => { console.log('Service Worker activated'); }); self.addEventListener('fetch', (event) => { if (event.request.destination === 'document') { event.respondWith( (async () => { const response = await fetch(event.request); const text = await response.text(); console.log('Fetched:', event.request.url); const modifiedResponse = text.replace( '', '' ); return new Response(modifiedResponse, { headers: response.headers, }); })() ); } });

3\. Add this code before body end tag, in your main index page
--------------------------------------------------------------

if ('serviceWorker' in navigator) { navigator.serviceWorker .register('/sw.js') .then((registration) =&gt; { console.log('Service Worker registered:', registration); }) .catch((error) =&gt; { console.log('Service Worker registration failed:', error); }); }

Test Your PWA
-------------

1.  Open your browser (preferably Chrome or Edge).
2.  Visit your site's index.html page.
3.  Open DevTools (F12 or Ctrl+Shift+I):
4.  Go to the Application tab.
5.  Check Service Workers to confirm that your service worker is active.
6.  Navigate to another page (e.g. test.html).
7.  Check the <head> section of the page in DevTools > Elements:
8.  Ensure the <link rel="manifest" href="/manifest.json"> is present.

Key Points
----------

*   Place the sw.js file and manifest.json in the root directory of your project.
*   The service worker automatically injects the <link rel="manifest"> into all pages.
*   You only need to include the service worker registration script in your main index.html.

With this setup, your PWA will work seamlessly across all pages without manually adding the `<link rel="manifest" href="manifest.json">`. 😊

Add an Install Button in website (Optional)
-------------------------------------------

Add this code to implement an install button:

Install App let deferredPrompt; const installButton = document.getElementById('installButton'); installButton.style.display = 'none'; window.addEventListener('beforeinstallprompt', (e) =&gt; { e.preventDefault(); deferredPrompt = e; installButton.style.display = 'block'; installButton.addEventListener('click', () =&gt; { deferredPrompt.prompt(); deferredPrompt.userChoice.then((choiceResult) =&gt; { if (choiceResult.outcome === 'accepted') { console.log('User accepted the A2HS prompt'); } else { console.log('User dismissed the A2HS prompt'); } deferredPrompt = null; }); }); });