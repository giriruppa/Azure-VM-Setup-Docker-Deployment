# Azure-VM-Setup-Docker-Deployment
Azure VM Setup & Docker Deployment

*******************************************************************************************************************************************************************
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

![image](https://github.com/user-attachments/assets/1051c752-58a4-4906-8768-f5c9ffcec1af)

-------------------------------------------------------------------------------------------------

Method 2: Using Azure CLI (Command Line)
---------------
1.	Open Azure Cloud Shell or run these commands from your local machine (if Azure CLI is installed).
2.	Login to Azure
az login

3.	Create a Resource Group (If not already created)
az group create --name MyResourceGroup --location eastus

4.	Create the First VM (VM1)
az vm create --resource-group MyResourceGroup --name VM1 --image UbuntuLTS --admin-username azureuser --generate-ssh-keys --size Standard_B1s

5.	Check the Running VMs
az vm list --resource-group MyResourceGroup --output table
![image](https://github.com/user-attachments/assets/1744effc-9ef0-4fad-9c8b-5cceb19fb4b6)



-------------------------------------------------------------------------------------------------


Method 3: Using Terraform (Infrastructure as Code)
-------
Using Terraform (Infrastructure as Code) in a Real-World Scenario
Scenario: Scaling Infrastructure for Black Friday Sales
Black Friday and other major sales events, like Amazon’s Great Indian Festival or Flipkart’s Big Billion Days, create massive spikes in user traffic. To handle these spikes, cloud infrastructure needs to scale dynamically.

Challenges Faced by E-Commerce Companies:
1.	Sudden Traffic Surge: Millions of users visit the website simultaneously, causing a huge load on servers.
2.	Performance Issues: If not managed well, slow page loading or server crashes can lead to revenue loss.
3.	Cost Optimization: Companies don’t want to pay for expensive infrastructure when traffic is low.
4.	Rapid Scaling: Infrastructure must scale up before the event and scale down afterward to optimize costs.
Solution: Using Terraform for Automated Infrastructure Scaling
Terraform, an Infrastructure as Code (IaC) tool, allows companies to provision, manage, and scale their cloud infrastructure dynamically.
Here’s how it works:
Step-by-Step Implementation using Terraform
1.	Defining Cloud Resources:
o	Companies use Terraform to define their cloud infrastructure in code (AWS, Azure, GCP).
o	Example: Amazon or Flipkart can create a Terraform script to deploy multiple EC2 instances, databases, and load balancers.
2.	Auto Scaling for Peak Traffic:
o	Using Terraform + AWS Auto Scaling, they define rules to scale instances automatically when CPU utilization exceeds 70%.
o	Example: If 500,000 users suddenly log in, more EC2 instances launch to handle traffic.
3.	Load Balancer for Even Traffic Distribution:
o	Terraform provisions an AWS Elastic Load Balancer (ELB) to distribute incoming traffic across multiple servers.
4.	Infrastructure Monitoring & Logs (Observability):
o	Terraform deploys CloudWatch or Splunk to monitor real-time traffic and detect failures.
o	If a server crashes, Terraform auto-recreates it.
5.	Database Scaling:
o	Using Terraform + AWS RDS Auto Scaling, the database scales up during high traffic and scales down afterward.
6.	Rollback & Disaster Recovery:
o	Terraform allows rolling back changes instantly if any issue occurs.
o	Example: If a faulty update causes server failure, Terraform can redeploy the last stable version.
By implementing Terraform, companies like Amazon and Flipkart can handle Black Friday traffic spikes efficiently without manual intervention, ensuring a seamless shopping experience for millions of customers. 

*******************************************************************************************************************************************************************

2)LOGIN THE VM IN YOUR HOST MACHINE(WINDOWS)
--------------------------------------------
Through your PowerShell you  can login your Virtual machine (Linux) in windows 
Needs – public IP , RSA key,username
1)	Vm1 – creation by GUI
2)	Vm2 -- creation by CMD 
![image](https://github.com/user-attachments/assets/cd2d3b7f-ef73-447e-8028-9fb409a83d3f)
![image](https://github.com/user-attachments/assets/e1920427-0121-481d-b32c-715e86cb4256)

*******************************************************************************************************************************************************************

3)After logging into your Azure Ubuntu VM, follow these steps to install Docker:
----------
________________________________________
🔹 Step 1: Update the System
Run the following command to update the package list and install required dependencies:
sudo apt update && sudo apt upgrade -y
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
________________________________________
🔹 Step 2: Add Docker’s Official GPG Key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
________________________________________
🔹 Step 3: Add Docker Repository
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

Go through above 3 steps first then below 2 steps 
![image](https://github.com/user-attachments/assets/3a53f4f8-bfc8-4d8d-8df2-b56e41fc3e15)
🔹 Step 4: Install Docker
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io
________________________________________
🔹 Step 5: Verify Docker Installation
Check if Docker is installed and running:
docker --version
sudo systemctl status docker


*******************************************************************************************************************************************************************

4) Docker:
![image](https://github.com/user-attachments/assets/4721ab2f-ac31-4a73-b4b1-bd42726a2bb4)
![image](https://github.com/user-attachments/assets/691ae8f2-f9c3-485a-b41b-384b3fb67f7e)

Above one is showing steps from creation to access 
Steps to Run Your HTML-CSS Project in Docker and Access Remotely
--------------------------------------------------------------------
Step 1: Create a Project Directory
Ensure your project files are in a single directory, e.g., my-website/:
my-website/
│── index.html
│── style.css 
![image](https://github.com/user-attachments/assets/cf3933cd-f8bc-4000-8309-783d5eac63f3)

________________________________________
Step 2: Create a Dockerfile
Inside the my-website/ directory, create a file named Dockerfile with the following content:
dockerfile 
![image](https://github.com/user-attachments/assets/fa26545a-e514-4c62-af83-1cc20f8a8770)

________________________________________
Step 3: Build the Docker Image
Navigate to your project directory and build the Docker image using this command:
docker build -t my-website . 
![image](https://github.com/user-attachments/assets/729c5cc5-f205-4d28-a41d-d493446b1a25)

________________________________________
Step 4: Run the Docker Container
Run the container and map port 80 of the container to port 8080 of your local machine:
docker run -d -p 8080:80 --name my-web-container my-website
Now, your website will be accessible on http://localhost:8080.
![image](https://github.com/user-attachments/assets/e0061632-6a83-4ef0-99e2-7f966d14f983)

________________________________________
Step 5: Access Remotely
To access it remotely:
•	If you're using Docker on a cloud server (e.g., AWS, DigitalOcean, etc.), replace localhost with your public IP.
•	If using Docker locally, find your system’s IP and access it using http://your-ip:8080


 Some issues like network releted I faced so encountered that in below 
 ------![image](https://github.com/user-attachments/assets/f570000f-6d9b-4bc7-bec1-986ce1894ab1)



Note : If you not able to accessing through below steps •  Go to Azure Portal → Virtual Machines → Click on MyDockerVM.
---------------------------------------------------------------------------------------
•  Open Networking (left menu).
•  Check Inbound Rules → Look for a rule allowing port 80 (TCP).
•  If no rule exists, Add Inbound Rule:
•	Source: Any
•	Source port ranges: *
•	Destination: Any
•	Destination port ranges: 80
•	Protocol: TCP
•	Action: Allow
•	Priority: 1000
•	Name: Allow-HTTP 
![image](https://github.com/user-attachments/assets/e188a79a-e2c9-4ea0-9635-40c50c5b7d29)
![image](https://github.com/user-attachments/assets/3e352ac0-8f2d-4d62-a329-304e71e1adf7)

Accessing website 
----------------

•	Locally inside VM:
curl -I http://localhost
![image](https://github.com/user-attachments/assets/e3194435-21da-4b6d-8381-d8cce2846d0d)


•	Remotely from another device:
curl -I http://20.169.202.24
![image](https://github.com/user-attachments/assets/ab53fce2-278c-4a51-86bd-d015491f07d2)

•	Browser access:
http://20.168.202.24:8080
![image](https://github.com/user-attachments/assets/ca6d2a69-8885-457c-84ab-5be957c8458e)

