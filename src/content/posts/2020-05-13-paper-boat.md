---
template: blog-post
title: Setting up Darkweb Monitoring using Onionscan deployed in Virtual Private
  Server
slug: /Setting up Darkweb Monitoring using Onionscan deployed in Virtual Private
  Server
date: 2020-05-23 23:40
description: ddd
featuredImage: ""
---
### When it comes to Dark web OSINT tool, I would recommend Onionscan tool which is free and open source tool, written in GO language & it checks for onion website vulnerabilities, misconfiguration etc.,

* It queries apache server mod_status to find any leaking information in the server like IP Address or hosted server.
* It also checks for open directories and even in backup copies of the website.
* It strips EXIF data from images to find geolocation data and much more.
* Onionscan identifies cryptocurrency addresses that can correlated a shared
* Also correlated clearnet versions of a site and find user information like email address.

### To deploy our 24x7 monitoring tool we need to setup few pre-requisites:

1. Virtual Private Network (Digital ocean, AWS, etc.,)
2. Installation of Onionscan tool and dependencies in the VPN server
3. Python script to automate the tool
4. Peace of Mind :)

### 1. Setting up virtual Private Network

I would like to select digital ocean platform to run our tool, so follow below instruction to setup the droplet in the Digital Ocean.

**Step1: You need to create droplets as shown in below.**

![](/assets/screenshot_12.png "Droplet")

**Step2: Select “Ubuntu 20.04 (LTS) x64” distribution** or latest version and set-up the required details to create a droplet.

![](/assets/screenshot_13.png)

**Step 3: Viola! Now your droplet has been created.**

![](/assets/screenshot_15.png)





### *2.* Installation of Onionscan tool and dependencies in the VPN server

First and foremost, you need to do is to connect your VPN server.



> ```shell
> ssh root@public_ip
> ```


*Note: You can connect the VPN Server using SSH in the terminal if your using Mac/Linux Platform. Incase if your using windows 10 machine you can enable Linux Sub-system or SSH App*

As I have connected to my VPN machine, now I need to download the pre-requisties which are required for downloading Onionscan. You can refer official page to check the dependencies for the onion_scan.