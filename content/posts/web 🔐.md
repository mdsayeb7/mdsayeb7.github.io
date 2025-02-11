---
title: 'Web 🔐  via chatgpt'
date: 2023-12-14T14:34:00.006+06:00
draft: false
---

 V1 (basic) (hack possible)
```
 <style>  
         body {            display: none;        }    </style>    <script>        function validatePassword() {            var password = prompt("Please enter the security key:");  
             if (password !== "200") {                alert("Incorrect security key. Access denied.");                document.body.innerHTML = "";            } else {                // If the password is correct, display the body content                document.body.style.display = "block";            }        }    </script><body onload="validatePassword()"></body>
```
  
V2 (security enhanced)  
```
 <style>  
         body {            display: none;        }    </style>   <script>        function validatePassword() {            var allowedAttempts = 3; // Set the maximum number of attempts            var password = "200"; // Set the correct password            var attempts = 0;  
             function clearBody() {                document.body.innerHTML = "";            }  
             function displayContent() {                document.body.style.display = "block";            }  
             function showAccessDenied() {                alert("Incorrect security key. Access denied.");                attempts++;                if (attempts >= allowedAttempts) {                    alert("Maximum attempts reached. Access denied.");                    clearBody();                } else {                    validatePassword(); // Prompt for password again                }            }  
             var enteredPassword = prompt("Please enter the security key:");  
             if (enteredPassword !== password) {                showAccessDenied();            } else {                // If the password is correct, display the body content                displayContent();            }        }    </script><body onload="validatePassword()">  
> </body>
```