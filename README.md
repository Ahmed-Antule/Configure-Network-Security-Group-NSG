# Configure-Network-Security-Group-NSG
### What is Network Security Group (NSG)?
A Network Security Group (NSG) is a security feature in Microsoft Azure that acts as a virtual firewall to control inbound and outbound traffic to Azure resources. It allows you to define security rules that permit or deny network traffic based on source/destination IP address, port, and protocol.NSGs can be assigned to subnets or network interfaces of virtual machines, helping to enforce security policies at different levels. They are stateful, meaning if traffic is allowed in one direction, the response is automatically permitted. Azure also includes default security rules to manage baseline traffic control while allowing customization for specific security needs.

### Summary

### Step-1
i.Creating a virtual network
![Capture1](https://github.com/user-attachments/assets/d4288559-f95f-4fc7-a8ff-786c04c3ec5b)

ii.Navigate to IP address
![Capture2](https://github.com/user-attachments/assets/96b8e9ee-0bf1-4e42-a311-d073b9532e1b)

### Step-2
i.Create two Virtual machines(select only RDP port)
![Capture3](https://github.com/user-attachments/assets/c03ea246-e651-4c20-9696-bdf407fa58a7)
![Capture4](https://github.com/user-attachments/assets/a81ad009-66ca-4f31-a900-a1025dfce438)


### Step-3
i.Create two Network Security Groups(NSG)<br>
one for VMs and another for the subnet
![Capture5](https://github.com/user-attachments/assets/9ec35846-cf73-4161-8c89-95b50bc06a91)

### Step-4
i.Open the VM NSG and configure inbound rules to allow HTTP(Port 80),HTTPS(Port 443) and RDP(Port 3389) access.
![Capture6](https://github.com/user-attachments/assets/f18730db-b1d9-4fed-9ebf-30744d319de3)
![Capture7](https://github.com/user-attachments/assets/08792c9b-d53e-4b9b-bc68-4b6b963ce2d4)

ii.Open the Subnet NSG and configure an inbound rule to allow RDP access only.
![Capture8](https://github.com/user-attachments/assets/f226eda9-01f8-43b9-b1c3-c239b1c2f9fd)

### Step-5
i.Open the machine-1 virtual machine, navigate to <strong> Network Settings </strong> and select the <strong> Network Interface </strong> to access the NSG option
![Capture9](https://github.com/user-attachments/assets/90b42941-d1b6-42c3-bc64-35221a0009ec)

ii. Click on Network Security Group (NSG), select VM-NSG (the NSG created for the VMs), and click Save. Repeat the same process for the second VM.
![Capture10](https://github.com/user-attachments/assets/8fbc68e6-3e82-4977-9378-689627b9d061)

iii. Now, set the NSG for the subnet. Open the virtual network you created, select Subnets, click on the specific subnet, and then choose the Subnet-NSG that you created for the subnet.
![Capture11](https://github.com/user-attachments/assets/70a96545-e654-4df8-8bf9-017a37c2c2e7)

### Step-6
i. Connect both virtual machines and install the IIS server on each to host the website.
![Capture12](https://github.com/user-attachments/assets/50bfdcbb-a3fc-4ff0-a674-be4a0aa1708e)

iii. Once the website is hosted, obtain the public IP address of the VM and paste it into your browser (not within the virtual machine).
![Capture13](https://github.com/user-attachments/assets/3c5ba822-67bf-4a34-a116-8f0831d47b33)

You will notice that we are unable to access the website hosted on the VM. This is because, based on the Network Security Group (NSG) rules, HTTP and HTTPS traffic is only allowed within the VMs and not from external sources.

iv. Now, paste the same public IP address into the browser on your machine-2 VM.
![Capture15](https://github.com/user-attachments/assets/dbcd03d4-4f3a-4b7e-a02d-2071bcaecd6a)

You will notice that you are able to access the website from within the same subnet, as the VM NSG allows HTTP and HTTPS traffic only within the VMs, and the communication between the VMs within the same subnet is permitted.














