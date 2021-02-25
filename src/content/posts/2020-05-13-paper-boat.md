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

![](/assets/screenshot_16.png)

As I have connected to my VPN machine, now I need to download the pre-requisites which are required for downloading Onionscan. You can refer official page to check the dependencies for the onion_scan.

Before you download onioscan dependencies, make sure that you got python and TOR installed on your machine, if not please type below commands.

```shell
apt-get update

apt-get install tor git bison libexif-dev

apt-get install python3-pip

pip3 install stem
```

![](/assets/screenshot_19.png)

*Stem is a Python controller library that allows our application to interact with Tor.*

#### Now you need to download of installing the latest version of Go

**Step1: Visit the official Go downloads page and find the version for the current binary release’s tarball and download it using curl command line utility.**

```shell
curl -O https://dl.google.com/go/go1.10.16.linux-amd64.tar.gz
```

![](/assets/screenshot_23.png)

**Step2: Extract the Tarball**

```shell
tar xvf go1.10.16.linux-amd64.tar.gz
```

**Step 3: Change the permission and move the file to local**

```shell
sudo chown -R root:root ./go
sudo mv go /usr/local
```

**Step 4:  Now set-up go path.**

```shell
sudo nano ~/.profile
```

**Add the following below line at the end.**

`export GOPATH=$HOME/work`

`export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin`

``

``

![](/assets/screenshot_24.png)

**Step 5: Now refresh the profile and check the version of Go**

```
source ~/.profile
```

![](/assets/screenshot_25.png)

### Installation of Onionscan

Now we have installed GO, now we can easily download the onionscan from below repository

```
go get github.com/s-rah/onionscan

go install github.com/s-rah/onionscan@latest
```

![](/assets/screenshot_27.png)

Now we have successfully installed Onionscan!!

### 3. Python script to automate the tool

Thanks to the author of Automatingosint, who has created onionscan automated python script which will kill a stuck onionscan process and grab a fresh IP address from the TOR network and  I have made small modification on the script and converted into python3 version.

You can download it from below repo link using wget command.

Link: <https://raw.githubusercontent.com/4n6shetty/Darkweb_OnionScan/main/OnionScannerPython3>



```
wget https://raw.githubusercontent.com/4n6shetty/Darkweb_OnionScan/main/OnionScannerPython3
```

![](/assets/screenshot_30.png)