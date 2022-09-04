---
title: Automation with VirtualBox, Vagrant & Chef
author: Ahmad Buhari
date: 2022-09-04 14:10:00 +0800
categories: [tutorial]
tags: [chef, vagrant]
render_with_liquid: false
--- 


In this article, we're testing [Chef](https://www.chef.io/) to automated deploying virtual machines (vm)s using:
- Chef Zero -> infrastructure code, developing in local mode.
- Vagrant -> VM template manager.
- VirtualBox -> software hypervisor.
<iframe src="https://giphy.com/embed/2knCiF52bpFiNWXcJ7" width="480" height="360" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>

## Prepping the compute element

### 1. If using Windows disable Hyper-V
Disable Hyper-V & reboot using PowerShell 
```
    Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V-All
```

### 2. Download VirtualBox Application
Follow default prompts, download from https://www.virtualbox.org/wiki/Downloads is a software-defined hypervisor for creating virtual machines. 

### 3. Download Vagrant Application
Follow default prompts, and download from https://www.vagrantup.com/downloads the application allows you to deploy VMs using CLI in a consistent manner.
- by default vagrant box images are stored in the `./vagrant` directory

### 4. Download Chef Workstation
Follow default prompts, and download from https://www.chef.io/downloads/tools/workstation the application is open-source that provides template deployment for OS

### 5. Test vagrant application functionality
On a linux instance run `sudo /sbin/vboxconfig` from the command line an ensure all checks are cleared.
1. Testing Vagrant Application
    - Run vagrant commands to ensure the application is installed correctly.

2. Start/Initialize the Project
Navigate to the project folder and initialize a vagrant config file `vagrant.exe init hashicorp/bionic64` note bionic64 is a maintained custom image of Ubuntu by hashicorp.

3. Start the vagrant VM installation
Run `vagrant.exe up` this will initiate the build process, it will look for the vagrant version of ubuntu if not available it will download from the Vagrant Cloud https://app.vagrantup.com/ubuntu/boxes/bionic64

4. Destroy the vagrant instance
Run `vagrant.exe destroy` this will destroy the vagrant vm instance.

<br>

## Testing VM Automation with Chef Zero

1. Create a Chef Project Subfolder 
I recommend creating the subfolder within the same project directory for easy management/reference example `chef_myproj`. It can get confusing as the build progress with new files and folders. Hence take the time to plan out the folder structure for the project. 

2. Initialize a Chef cookbook (a.k.a template)
Navigate to the project folder and use `chef generate cookbook chef_myproj` note chef_myproj is the subfolder where all the configuration files for Chef will be saved in.

3. Test build with kitchen
Run `kitchen list` to test deployable vagrant vm instances.

### Note: Code deployment for Ubuntu64, requires an internet connection to download the packages & it's dependencies.