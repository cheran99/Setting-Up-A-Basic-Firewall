# Setting-Up-A-Basic-Firewall

## Introduction

The purpose of this project is to set up a basic firewall using pfSense. pfSense is a open source firewall tool that is user-friendly and great for beginners. The firewall will be used to let certain devices access the internet while blocking any unwanted traffic to enter the network.

### Objectives

- Install pfSense to your dedicated machine/virtual environment
- Set up and configure network interfaces
- Set up basic firewall rules
- Test the firewall rules and monitor traffic logs

## Methodology 

### Step 1: Install pfSense To Your Machine

The first step is to install pfSense on your dedicated machine. In this case, pfSense will be downloaded and installed on VirtualBox so that the firewall can be tested in a virtual environment.  

Go to the pfSense website to download the software.

![image](https://github.com/user-attachments/assets/bfb3ecef-583c-4da4-8817-6f456536ff72)

When you click download, you will be taken to the Netgate website, as shown below, where you will need to download the Netgate Installer. The installation image that you need to select is the "AMD64 ISO IPMI/Virtual Machines" since pfSense is being installed on the virtual machine.  

![image](https://github.com/user-attachments/assets/d4b67228-a43a-43f1-bb64-7c0b24d6cf6e)

The Netgate Installer is free to purchase and download so you don't need to provide your bank details. You will need to create an account to download the installer.

![image](https://github.com/user-attachments/assets/1ed95cf1-c4ce-4b87-9840-408d2f99ecfb)

Once the Netgate Installer is downloaded, extract the downloaded file using 7zip.

![image](https://github.com/user-attachments/assets/05c3bd02-75f9-4709-be7a-dcd47a297788)

Next, go to VirtualBox, and click "New" to create a new virtual machine.

![image](https://github.com/user-attachments/assets/d038fcd5-6a63-45f6-8def-2c79c3ffefbc)

As illustrated above, select the extracted ISO file as the ISO image and BSD as the operating system type. In terms of subtype and version, select FreeBSD (64-bit) as the subtype and version. 

For hardware, set the base memory to 2GB and the processor to 1 CPU.

![image](https://github.com/user-attachments/assets/b739f08d-8d55-4b94-8372-6a3840743560)

Once all of this is set, click "Finish" to set up the virtual machine. 

![image](https://github.com/user-attachments/assets/e37a48db-531b-410e-97af-a09b9b93c95f)

Next, click "Settings" on the newly created virtual machine, and go to the "Network" section. For Adapter 1, select "NAT" as the adapter to act as the WAN connection to the internet. For Adapter 2, select "Internal Network" to act as a LAN connection. 

![image](https://github.com/user-attachments/assets/f6184b9c-c928-4ee1-8d7e-aad7c26bda18) ![image](https://github.com/user-attachments/assets/32c584b5-f97c-408c-a4df-9602abb916ca)

Once this is set, click "Ok" and start the virtual machine. 

You will be asked to install pfSense upon starting the virtual machine.

![image](https://github.com/user-attachments/assets/af30792c-6e06-4ddb-9367-5db527c3c7cd)

Select the active WAN interface:

![image](https://github.com/user-attachments/assets/14131ec0-88bb-42c2-a97a-314c77b451c1)

Enter "OK" to continue. Select the remaining network interface to act as the LAN interface:

![image](https://github.com/user-attachments/assets/c9e6bd6c-77f2-496d-9e00-3617e15d57a5)

Press "CONTINUE" as you go along. Once you get to the part where it asks you if you want to destroy the current contents of the following disks, select "YES" as shown below:

![image](https://github.com/user-attachments/assets/216da644-fab2-4a08-9d7b-530585ca7e12)

Next, select the current stable release as the version for the pfSense CE to install:

![image](https://github.com/user-attachments/assets/a4441e45-f271-4fe9-8d77-4cc5ddb073e1)

Once it is installed, you can reboot the virtual machine:

![image](https://github.com/user-attachments/assets/24ddda84-7e89-407c-81b1-854ebb736cc9)

Next, remove the disk from the virtual drive:

![image](https://github.com/user-attachments/assets/b86d17c0-40fb-4cef-b9b0-3b076ef3d0aa)

This will finish the configuration. Once the configuration is finished, you will be given options to select from along with IP addresses of the WAN and LAN interfaces:

![image](https://github.com/user-attachments/assets/f6347036-9868-4774-8ecd-11c6a38f27f4)



