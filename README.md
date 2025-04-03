![image](https://github.com/user-attachments/assets/fe005004-3701-4e90-b6fe-c73da7b4d8b4)# Azure-VM-Setup-Docker-Deployment
Azure VM Setup &amp; Docker Deployment
1) CREATING VIRTUAL MACHINE IN AZURE
   
Method 1: Using Azure Portal (GUI)
1.	Sign in to Azure Portal
*	Go to Azure Portal
*	Sign in with your credentials.
  
2.	Create the First Virtual Machine
*	Click on "Create a resource" > "Virtual Machine"
*	Configure the following:
* Subscription: Select your subscription – In my case azure for students
* Resource Group: Create a new one or use an existing – mine is new one.
*	Virtual Machine Name: e.g., VM1
*	Region: Choose a region (e.g., East US) – better to choose the recommended one
*	Image: Choose an OS (e.g., Ubuntu, Windows Server) – I choose the Linux OS
*	Size: Select an appropriate VM size – select the size with respectively and check the cost per hour / per month.
*	Administrator Account: Set username & password/SSH key(better to choose the key )  - After choose ssh it will download one file in your system .pem extension  . This private key will use up coming steps. Like when your connecting to the Virtual machine in windows or Linux or mac. 
*	Networking: Choose/Create a Virtual Network
For beginners(practice purpose) we need to assign the all options . But it  required in industry (better to choose the best pratices)
o	Click Next and configure other settings (Storage, Monitoring, etc.), then click Review + Create
o	Click Create and wait for deployment.
![image](https://github.com/user-attachments/assets/7054f2df-5fc4-47d3-bfc9-1c8429110d86)

![image](https://github.com/user-attachments/assets/6c3cc253-13b5-4e67-ab47-8555088689a5)


Method 2: Using Azure CLI (Command Line)
Method 3: Using Terraform (Infrastructure as Code)

2)LOGIN THE VM IN YOUR HOST MACHINE(WINDOWS) 

3)After logging into your Azure Ubuntu VM, follow these steps to install Docker:
🔹 Step 1: Update the System
