---
title: 'Web 🔐  via chatgpt'
date: 2023-12-14T14:34:00.001+06:00
draft: false
url: /2023/12/web.html
---

**V1 (basic) (hack possible)**

_<style>_

        _body {_

            _display: none;_

        _}_

    _</style>_

    _<script>_

        _function validatePassword() {_

            _var password = prompt("Please enter the security key:");_

            _if (password !== "200") {_

                _alert("Incorrect security key. Access denied.");_

                _document.body.innerHTML = "";_

            _} else {_

                _// If the password is correct, display the body content_

                _document.body.style.display = "block";_

            _}_

        _}_

    _</script>_

_<body onload="validatePassword()"/>_

**V2 (security enhanced)**

_<style>_

        _body {_

            _display: none;_

        _}_

    _</style>_

    _<script>_

        _function validatePassword() {_

            _var allowedAttempts = 3; // Set the maximum number of attempts_

            _var password = "200"; // Set the correct password_

            _var attempts = 0;_

            _function clearBody() {_

                _document.body.innerHTML = "";_

            _}_

            _function displayContent() {_

                _document.body.style.display = "block";_

            _}_

            _function showAccessDenied() {_

                _alert("Incorrect security key. Access denied.");_

                _attempts++;_

                _if (attempts >= allowedAttempts) {_

                    _alert("Maximum attempts reached. Access denied.");_

                    _clearBody();_

                _} else {_

                    _validatePassword(); // Prompt for password again_

                _}_

            _}_

            _var enteredPassword = prompt("Please enter the security key:");_

            _if (enteredPassword !== password) {_

                _showAccessDenied();_

            _} else {_

                _// If the password is correct, display the body content_

                _displayContent();_

            _}_

        _}_

    _</script>_

_<body onload='validatePassword()'>_