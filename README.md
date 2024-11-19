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


