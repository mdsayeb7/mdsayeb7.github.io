---
title: 'Add install app button '
date: 2025-01-29T13:17:00.004+06:00
draft: false
---

## অ্যাপ ইনস্টল

অ্যাপ ইনস্টল করুন

অ্যাপটি ইতিমধ্যে ইনস্টল করা আছে

let deferredPrompt; // Function to update install UI function updateInstallUI() { const installButton = document.getElementById('installApp'); const installMessage = document.getElementById('installMessage'); if (deferredPrompt) { // Can be installed - show button, hide message installButton.style.display = 'block'; installMessage.style.display = 'none'; } else { // Can't be installed - hide button, show message installButton.style.display = 'none'; installMessage.style.display = 'block'; } } // Listen for install prompt window.addEventListener('beforeinstallprompt', (e) => { e.preventDefault(); deferredPrompt = e; updateInstallUI(); }); // Handle install button click document.getElementById('installApp').addEventListener('click', async () => { if (!deferredPrompt) return; try { await deferredPrompt.prompt(); await deferredPrompt.userChoice; deferredPrompt = null; updateInstallUI(); } catch (error) { console.error('Installation error:', error); } }); // Listen for successful installation window.addEventListener('appinstalled', () => { deferredPrompt = null; updateInstallUI(); }); // Initial UI update document.addEventListener('DOMContentLoaded', () => { updateInstallUI(); initializeSettings(); loadSubjects(); loadSavedData(); });