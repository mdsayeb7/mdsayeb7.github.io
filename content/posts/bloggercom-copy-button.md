---
title: 'Blogger.com Copy Button'
date: 2025-01-19T12:22:00.053+06:00
draft: false
url: /2025/01/blog-post_19.html
---

1- Go To Your Blogger Dashboard  
2- Click On Theme Section  
3- Click On Edit HTML  
4- Find </body> Tag  
5- Paste the code above body end tag  
6- remove /\* & \*/ before and after script tag.  

.infinite-blockquote { position: relative; background: #f8f9fa; padding: 20px; margin: 15px 0; border-radius: 8px; border-left: 4px solid #0d6efd; font-family: 'Courier New', monospace; line-height: 1.6; color: #333; box-shadow: 0 2px 5px rgba(0,0,0,0.1); white-space: pre; overflow-x: auto; } .copy-button { position: absolute; top: 10px; right: 10px; padding: 6px 12px; background: #0d6efd; color: white; border: none; border-radius: 4px; cursor: pointer; font-size: 13px; transition: background 0.3s; } .copy-button:hover { background: #0b5ed7; } @media screen and (max-width: 768px) { .infinite-blockquote { padding: 15px; margin: 10px 0; } } /\* \*/ document.addEventListener('DOMContentLoaded', function() { const blockquotes = document.querySelectorAll('.infinite-blockquote'); blockquotes.forEach(blockquote => { // Preserve formatting of the original content const formattedContent = blockquote.innerHTML; blockquote.textContent = formattedContent; const copyButton = document.createElement('button'); copyButton.textContent = 'Copy'; copyButton.className = 'copy-button'; blockquote.appendChild(copyButton); copyButton.addEventListener('click', async () => { try { await navigator.clipboard.writeText(blockquote.textContent.replace('Copy', '').trim()); copyButton.textContent = 'Copied!'; setTimeout(() => { copyButton.textContent = 'Copy'; }, 1500); } catch (err) { copyButton.textContent = 'Error'; setTimeout(() => { copyButton.textContent = 'Copy'; }, 1500); } }); }); }); /\* \*/

6- Go To Your Blogger Dashboard  
7- Click On New Post  
8- Now Open HTML View  
9- Paste This line, There You Want To Add copy button  
10- Replace "Example" With Your text  

Example