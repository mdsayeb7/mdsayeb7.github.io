---
title: 'Azure ubunto cpanel'
date: 2024-02-16T05:12:00.024+06:00
draft: false
tags: ['server']
---

## After creating vps 

check blacklist  ip: [https://mxtoolbox.com/blacklists.aspx](https://mxtoolbox.com/blacklists.aspx)  

download putty : [https://putty.org/](https://putty.org/)

\---------------------------------------------------------------------------------------------------------

## 1- login your vps

go to root

        >  sudo -i

        >  sudo passwd root (for change root pass)

   > hostname (your domain name. ex; server.abc.com)

   > hostname -f (for checking hostname)

## 2- Update it

   > sudo apt update

   > sudo apt install wget

   > sudo apt install perl - RECOMMENDED

   > sudo apt upgrade 

## 3- DISABLE NETWORK MANAGER 

systemctl stop NetworkManager
systemctl disable NetworkManager

sudo systemctl stop systemd-networkd
sudo systemctl disable systemd-networkd

  

## 4- DOWNLOAD & INSTALL CPANEL (official)

cd /home && curl -o latest -L https://securedownloads.cpanel.net/latest && sh latest

## Install SSL

/scripts/install\_lets\_encrypt\_autossl\_provider

IP:2087 for whm

IP:2083 for cpanel

[![](https://blogger.googleusercontent.com/img/a/AVvXsEhsuDQqlWGJRFF8c5kZJRLkG4m_VfV2Uz5hYtbGmAb4g17ybaL5YtCZj5bBpTZJ6RiEWUKy-bEh8qtG23cbeSUvLhCpw8GTUPomLFqvIcrhYsODHpcnuT4-r4sQEk_XtjRt9WP_1HUByU4Elyp7CrICjm62gmU4be34RBkzW8N44Owbp95nCaCT69bLVlm4=w643-h309)](https://blogger.googleusercontent.com/img/a/AVvXsEhsuDQqlWGJRFF8c5kZJRLkG4m_VfV2Uz5hYtbGmAb4g17ybaL5YtCZj5bBpTZJ6RiEWUKy-bEh8qtG23cbeSUvLhCpw8GTUPomLFqvIcrhYsODHpcnuT4-r4sQEk_XtjRt9WP_1HUByU4Elyp7CrICjm62gmU4be34RBkzW8N44Owbp95nCaCT69bLVlm4)  

[![](https://blogger.googleusercontent.com/img/a/AVvXsEhptRF6-T7dLsjwnHWBaF8RhhtsV8yz6uPCv5cyOirg9Yw3L2ZOhBG4SJTfoJU_yIgfYg3ZTMhEeKkjuVUQgN1Gr5kkwnUXPBhlmglIza1yZO6EOvsD5MHUVP-scwtqJTmybFbO2qJ7bVyf2XdhE97KAtw0As20MPNEuL_woATApWb4MbUGVUTtZAm6IBhA=w661-h309)](https://blogger.googleusercontent.com/img/a/AVvXsEhptRF6-T7dLsjwnHWBaF8RhhtsV8yz6uPCv5cyOirg9Yw3L2ZOhBG4SJTfoJU_yIgfYg3ZTMhEeKkjuVUQgN1Gr5kkwnUXPBhlmglIza1yZO6EOvsD5MHUVP-scwtqJTmybFbO2qJ7bVyf2XdhE97KAtw0As20MPNEuL_woATApWb4MbUGVUTtZAm6IBhA)  

[![](https://blogger.googleusercontent.com/img/a/AVvXsEg9HajAxUrWd356NEDrvk7P0_8P03yvV9M8ISjKKMIqXMHHJiUjCRa5MHiHrafM9TN_zl77FdFYNs6cnQK3it1MZhjx8uvBve_prUO30SU2mbpd9mYPBsIU2VeC_O2jiGMpVf8G1-0YuUT4mXM2dtX9PMo0xmngFvc4-RoInof9aDUUCAB1WMikNqjBw4ic=w650-h290)](https://blogger.googleusercontent.com/img/a/AVvXsEg9HajAxUrWd356NEDrvk7P0_8P03yvV9M8ISjKKMIqXMHHJiUjCRa5MHiHrafM9TN_zl77FdFYNs6cnQK3it1MZhjx8uvBve_prUO30SU2mbpd9mYPBsIU2VeC_O2jiGMpVf8G1-0YuUT4mXM2dtX9PMo0xmngFvc4-RoInof9aDUUCAB1WMikNqjBw4ic)

inbound

[![](https://blogger.googleusercontent.com/img/a/AVvXsEh8BpcImmic_kmZ6Xc2eKRXGJ3CY3QtF7mwDe54kmcRfWaaHGucJaaVSyLTiDNrzheg3wcrnvUkSZFWdKBRVPQ8n9TWOQKdEBDBDypVwWsqB-47osoZtKAHblH22z7fqYeJi0BkUMW-p70_OCcMiAIbnbMF76CJ4QNzY_iy_iDdGcRg1j5yt2KAjxYyX8V-=w658-h300)](https://blogger.googleusercontent.com/img/a/AVvXsEh8BpcImmic_kmZ6Xc2eKRXGJ3CY3QtF7mwDe54kmcRfWaaHGucJaaVSyLTiDNrzheg3wcrnvUkSZFWdKBRVPQ8n9TWOQKdEBDBDypVwWsqB-47osoZtKAHblH22z7fqYeJi0BkUMW-p70_OCcMiAIbnbMF76CJ4QNzY_iy_iDdGcRg1j5yt2KAjxYyX8V-)

  
  

  

[![](https://blogger.googleusercontent.com/img/a/AVvXsEhhUktjIEMs4tVul9Ra2oHsKkWfnCmuTlKb7yd6Mvoc6aOM9P2McFUVtB2CX6Rl0B4bRj4yh54vFx7C-3_beJDwZVy7wFtwbAuQamqJLGZcyRMjed8VLjAdCL0NJVw1XuXCNNilZytgGdPIXtQoH9hglDKgwMUhuEJ1FnHQ0bLWM4vgCvRqxVDKVk9wM8-5=w670-h355)](https://blogger.googleusercontent.com/img/a/AVvXsEhhUktjIEMs4tVul9Ra2oHsKkWfnCmuTlKb7yd6Mvoc6aOM9P2McFUVtB2CX6Rl0B4bRj4yh54vFx7C-3_beJDwZVy7wFtwbAuQamqJLGZcyRMjed8VLjAdCL0NJVw1XuXCNNilZytgGdPIXtQoH9hglDKgwMUhuEJ1FnHQ0bLWM4vgCvRqxVDKVk9wM8-5)