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

Next, click "Settings" on the newly created virtual machine, and go to the "Network" section. For Adapter 1, select "NAT" as the adapter to act as the WAN interface to enable an internet connection. For Adapter 2, select "Internal Network" to act as a LAN interface. 

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

![image](https://github.com/user-attachments/assets/cfae67e0-045f-41ab-95d9-d3a1797445c1)

Minimise the window for the pfSense VM. On VirtualBox, click on the Kali VM, then go to "Settings", and then to "Network". Select "Internal Network" as the adapter as shown below:

![image](https://github.com/user-attachments/assets/8d324222-1fa0-4a8c-a08a-c1a1020c1dbb)

Next, start the Kali virtual machine. 

### Step 2: Configuration

Once the Kali VM is running, open the web browser in the virtual machine. In the address bar, type in the IP address of the LAN interface shown in the pfSense virtual machine which is 192.168.1.1:

![image](https://github.com/user-attachments/assets/42514714-f762-4b8e-b2a3-37b90acc931b)

This will take you to the pfSense page:

![image](https://github.com/user-attachments/assets/6ae2cbd9-0a57-4ad0-91ca-3d85e5a79374)

Log in to this page using the default credentials:

```
Username: admin

Password: pfsense
```

Once successfully logged in, you will be asked to set up pfSense. Click "Next" until you arrive at the "General Information" page. On this page, you can give a name of your choice as the "Hostname":

![image](https://github.com/user-attachments/assets/2b9dc15c-7c50-4722-9fc2-e7e2c535963c)

Leave everything else to its default and click "Next". On the "Time Server Information" page, set the timezone to your local time:

![image](https://github.com/user-attachments/assets/db05919b-1ae5-42c5-a18a-b16b4e1a6e9e)

Click "Next". On the "Configure WAN Interface" page, scroll down to the bottom of the page and uncheck the "Block private networks from entering via WAN". This will enable wireless internet connections:

![image](https://github.com/user-attachments/assets/72af925f-ca1d-4c71-8407-5bb70bc67028)

Continue clicking "Next" over the following pages and leave everything else to its default. Next, click "Reload", to update its configurations:

![image](https://github.com/user-attachments/assets/ca2928d1-901c-4210-83f7-5af17e243375)

Once the setup wizard is complete, click "Finish" and this will take you to the dashboard which displays the system information about the pfSense virtual machine along with the network interfaces used:

![image](https://github.com/user-attachments/assets/7e7dd8c1-720a-4265-b035-17b03dd1d2ca)

To check if the internet connection is working, just search for something random and if it gives results, the internet connection is working. As shown below, the internet connection is working:

![image](https://github.com/user-attachments/assets/2a980a26-5951-43da-816a-ec882f4a364c)

### Step 3: Set Up Basic Firewall Rules

On the pfSense dashboard page in the Kali VM, go to "Firewall" and then to "Rules". Set the following rules:

- Allow LAN to WAN - This is to enable devices in the local network to access internet and external sources without restrictions. 
- Block WAN to LAN - This is to prevent any unwanted or malicious traffic outside the local network from entering the local network.

To set the rule to allow LAN to WAN, go to the LAN tab and click "Add":

![image](https://github.com/user-attachments/assets/123158c3-fac1-41f5-a0a4-ac42fdef3a6e)

Once you are on the "Edit Firewall Rule" page, configure the following fields

```
Action: Pass

Interface: LAN

Protocol: Any

Source: LAN subnets

Destination: Any

Description (optional): Allow LAN to WAN
```

![image](https://github.com/user-attachments/assets/aae7695b-c828-4617-8cd4-5fb2ace6c8b1)

Once the configuration is set, click "Save". This will ensure that the devices in the local network can access the internet and external sources easily.

To set the rule to block WAN to LAN, go to the WAN tab and click "Add". Configure the following fields:

```
Action: Block

Interface: WAN

Protocol: Any

Source: Any

Destination: LAN subnets

Description (optional): Block WAN to LAN
```

![image](https://github.com/user-attachments/assets/a8a8f27c-51a1-4ade-b16b-5bdd612cb2bf)

Click "Save". This will prevent any unwanted traffic from entering the local network. Next, click "Apply changes" for the rules to take effect:

![image](https://github.com/user-attachments/assets/c2ce18d7-768a-47b0-8cd5-bafb915d4943)

Now that these basic firewall rules are set. The next step is to test the firewall.

### Step 4: Testing The Firewall

To test if the devices in the local network can access the internet or any other external resources without restrictions, use a virtual machine with the same LAN interface as the pfSense virtual machine. In this case, the Kali virtual machine that was used earlier. Search for something random on the internet to see if the connection is successful. As shown below, access to the internet is successful:

![image](https://github.com/user-attachments/assets/3a6d5e14-dcb4-49f6-ae1c-4e1e750a6cb2)

Let's use another virtual machine with the same LAN interface to see if the internet connection is successful. A Windows 10 Pro virtual machine will be used. On VirtualBox, go to "Settings" for the Windows VM and then to "Network". Ensure that the "Internal Network" is selected as the adapter:

![image](https://github.com/user-attachments/assets/ca1b2e3b-6f72-4b1b-bbcb-933e9e6fc0f5)

Start the virtual machine and log in using your credentials. Open the web browser in this virtual machine and search for something random:

![image](https://github.com/user-attachments/assets/6f01f7e0-8f3b-4c52-ab77-45a4bb25aa62)

As shown above, the internet connection is successful. In the same virtual machine, let's try logging in to the pfSense dashboard using the LAN IP address along with the default credentials:

![image](https://github.com/user-attachments/assets/ede3add8-5353-4f3c-93ab-5cd875251cfa)

As shown above, access to the pfSense dashboard is successful. 

To test if a device from an external network is blocked from accessing the local network, let's use a virtual machine that is external to the local network. This time, the network adapter for the Windows virtual machine used earlier will be changed to "Bridged Adapter":

![image](https://github.com/user-attachments/assets/08b2d286-06d9-43fe-8340-5cbb4a5e5956)

Now that this is set, let's restart the machine. Once you are logged in, open the web browser in the virtual machine and log in to the pfSense dashboard using the LAN IP address:

![image](https://github.com/user-attachments/assets/41fce301-481e-49eb-a2ea-eb417fb740df)

As shown above, the attempt to access the pfSense dashboard failed. Let's try accessing the pfSense dashboard using the IP address for the WAN interface:

![image](https://github.com/user-attachments/assets/4f53a802-31ef-4325-b8b2-0a0a3cc6a172)

The attempt to access the dashboard through the IP address of the WAN interface also failed. This shows that external traffic entering the local network has successfully been blocked. When you ping the WAN IP address from the external device, it says "Request timed out" meaning that the pinging failed:

![image](https://github.com/user-attachments/assets/877c2045-d342-45ec-9ced-7f18d29f1a0b)

### Step 5: Monitor The Logs

Now that many attempts to connect to the internet using devices within the local network have been successful along with attempts to access the pfSense dashboard from external devices successfully being blocked, you can review the traffic logs that show all inbound and outbound traffic along with which traffic has been blocked or allowed. To view these logs, go to "Status", then to "System Logs", then go to the "Firewall" tab. This will show the traffic logs based on the firewall rules that were set earlier:

![image](https://github.com/user-attachments/assets/bdea289b-ffb1-4a5c-ab52-3fc9b01aedae)

As you can see in the traffic logs shown above, when a device from the local network attempts to connect to the internet such as searching for something random or entering a random website, the results show that the network traffic for this has successfully passed the firewall therefore allowing access to the internet without restrictions. However, when a device outside the local network attempts to connect to the local network by accessing the pfSense dashboard using the WAN IP address, the network traffic from the said device is blocked by the firewall from accessing the pfSense dashboard which is in the local network.  


## References

- https://youtu.be/XU5IvWW6luk?si=CmMwl6ObwH0AkaS9
- https://www.youtube.com/watch?v=ZYLULVIwC0k 

