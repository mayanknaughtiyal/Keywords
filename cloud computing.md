h# CLOUD COMPUTING 

# How to make a vm( virtual machine)=
1.make an account on aws.

2.select ec2 service.

3.inside ec2 make an instance,

For an instance select an os( operating system),
5.make an key pair ( the key pair will automatically be downloaded).

6 while making key pair select ppk type ,

7.an public ip will be generated,

8.launch the instance

Install an putty ( search on google how to download putty for (the operating system you have chosen) and download it.

After that open the putty and on ssh option paste the public ip from the instance,

11.in the aut option select credentials and browse the key pair you have created in instance,

Now to download a web server open putty and type :-sudo apt update, after that type :-sudo apt Install apache2,
13:- to remove the dollar sign type:- sudo su,

14:- after that the next step is to type :-/var/www/html/

15.enter the above and on the next line type index.html

16.after that type :-rm index.html

17.enter the above and type :-vi index.html ( by writing this a new page will appear in which you have to either type html code aur copy paste it from GitHub),

18.to run the code type :- control+c ,shift+ ,wq and enter


# using EC2 in aws
First open aws search EC2 then Launch Instance and there select keypair in putty then download it.

after that Launch it and run putty and paste public id on HOST NAME and open that downloaded key pair for putty in SSH then Auth then Credentials and open there.

after that run it and write username as ubuntu as selected os and then type following commands.

```bash
sudo apt update
```
``` bash
sudo apt install apache2
```
to install a web server on ip then
```
sudo su
```
for convert $ into # for getting admin role then
```
cd /var/www/html/
```
then
```
ls
```
for list of html file in it
then copy that html file name and write

```
rm index.html
```
rm means remove command

```
vi index.html
```
this will open a notepad like and write html code there like (vi is editor) 

 then press ctrl+c then shift+colon then write wq and enter

12. now copy your public ip and paste it on browser you will see the texts written by you (by using html above).

# Hosting a Website on AWS with Apache2 Using PowerShell
(These are the steps after launching instance and downloading .pem passkey)





Step 1: Connect to EC2 Instance Using PowerShell
Open PowerShell in Windows.
Navigate to your PEM file: First, ensure you’re in the directory where your .pem file is located. Use cd to change directories:
cd path\to\your-pem-file
Use the ssh command to connect to your EC2 instance:
ssh -i "path_to_your_key.pem" ec2-user@your_instance_public_IP
Replace path_to_your_key.pem with the location of your private key. Replace your_instance_public_IP with the public IP of your EC2 instance.

Step 2: Update the Package List on Your EC2 Instance
Run the following command after logging in to update your packages:

sudo apt update
Step 3: Install Apache2
To install the Apache2 web server:

sudo apt install apache2 -y
Step 4: Delete the Default index.html and Create Your Own
Navigate to the Apache web directory:

cd /var/www/html
Delete the default index.html file:
sudo rm index.html
Create a new index.html file:
sudo vi index.html
Add your website's HTML content and save the file.
YAY! Your link or IP adress of your instance will now work.

# USING DOCKER CONTAINER's IN VM ,TO ADD NGINX SEVER IN IT AND TYPING HI IN WEB SERVER
1. First I login in my AWS account . Thne I created an instance .
2. In instance I make some changes , where I edit in network setting , where I added SSH , HTTPS , HTTP, ALL TRAFFIC , ALL TCP , ALL UDP AND CREATED AN INSTANCE.
3. Then I open puuty add the IP address from instance and add key pair file which I have downloaded when I creating instance.
4. After that I click on open , then my ubuntu terminal was opended , where I logined by writting ubuntu.
5. After that I have to install docker in my OS .
6. Then , I enter few command to install the docker
7. COMMANDS ARE:
``` bash
curl -sL https://github.com/ShubhamTatvamasi/docker-install/raw/master/docker-install.sh | bash
```
```
newgrp docker
```
this command will help us to use docker
```
docker ps
```
provides a list of the Docker containers on your machine
```
docker --version
```
to check the version of docker which is installed
```
docker pull nginx
```
TO use nginx server in container
```
docker run --name docker-nginx -p 80:80 nginx
```
In a web browser, enter your server’s IP address to reveal Nginx’s default landing page
ctrl + c #to stop the container from running
```
docker ps -a
```
The output reveals that the Docker container has exited
●DETACHED MODE
```
docker run --name docker-nginx -p 80:80 -d nginx
```
output is the container’s ID
```
docker ps
```
provoide new information about container
```
docker stop docker-nginx
```
to stop the container
```
docker rm docker-nginx
```
Building a Web Page to Serve on Nginx
```
mkdir -p ~/docker-nginx/html
```
Create a new directory for the website content within the home directory
```
cd ~/docker-nginx/html
```
Create an HTML file to serve on the server
```
ls
```
```
cd html/
```
```
ls
```
will show index.html file
```
sudo vi index.html
```
```
i
```
help to insert in the web server
```
<html> hi </html>
```
write whatever you want to write I write only hi
ctrl + c
shift + ;
wq
press {ENTER}
```
docker run --name docker-nginx -p 80:80 -d -v ~/docker-nginx/html:/usr/share/nginx/html nginx
```
Linking the container to the VM

After running that command, enter the server’s IP address into the browser to view the new landing page





# INSTALLING MINIKUBE IN VM
1. CREATE AN INSTANCE IN AWS AS , WITH OS OF UBUNTU OR WHAT YOU WANT THEN CHANGE SOME SETTINGS TO WORK LIKE TAKING
Amozon Machine Image (AMI)
Instance type
t3.xlarge
AND
STORAGE
30GB
NETWORK SETTING YOU CAN INCLUDE
1. SSH
2. HTTP
3. HTTPS
4. ALL TRAFFIC
2. AFTER THESE CHANGES YOU CAN LAUNCH THE INSTNACE
3. AFTER THAT COPYING THE IP ADDRESS , ADD IT IN PUTTY AND ALSO SELECT THE KEY WHICH HAS BEEN CREATED IN PERIVOUS STEPS , THEN CLICK OPEN , AND YOUR VM IS AGAIN READY
4. NOW WE HAVE TO INSTALL DOCKER
```
curl -sL https://github.com/ShubhamTatvamasi/docker-install/raw/master/docker-install.sh | bash
```
THIS COMMAND WILL HELP TO INSTALL DOCKER
```
sudo usermod -aG docker $USER
```
THIS COMMAND WILL HEPL TO USE DOCKER FUNCTIONS
```
newgrp docker
```
THIS WILL CREATE A NEW GROUP IN OS
```
sudo snap install kubectl --classic
```
TO INSTALL kubectl IN DOCKER
```
kubectl version --client
```
TO SEE THE VERISON OF kubectl
```curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
```
TO INSTALL MINIKUBE
```
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```
TO INSTALL MINIKUBE IN LINUX DIRECTORY
```
minikube version
```
TO CHECK THE VERISON
```
minikube start --driver=docker
```
TO START THE MINIKUBE ON VM
```
minikube start --driver=docker --force
```
IF YOU GET SOME ERROR TRY THIS COMMAND TO SOLVE IT
```
minikube status
```
TO CHECK THE STATUS OF MINIKUBE THAT IT IS RUNNING OR NOT
```
kubectl cluster-info
```
TO SEE THE CLUSTER INFORMATION
```
kubectl config view
```
CONFIGURING THE KUBECTL
```
kubectl get nodes
```
TO SEE HOW MANY NODES ARE PRESENT IN KUBECTL
```
kubectl get pods
```
TO SEE HOW MANY PODS ARE PRESENT IN KUBECTL

To deploy a sample nginx deployment, run following set of commands.
```
kubectl create deployment nginx-web --image=nginx
```
```
 kubectl expose deployment nginx-web --type NodePort --port=80
```
```
kubectl get deployment,pod,svc
```
Managing Minikube Addons
```
minikube addons list
```
TO SEE THE LIST OF ADDONS WHICH WE CAN ENABLE
```
minikube addons enable dashboard
```
ENABLING DASHBORAD
```
minikube addons enable ingress
```
ENABLING INGRESS
```
minikube dashboard --url
```
It will get the url and run the dashboard of MiniKube
```
kubectl proxy --address='0.0.0.0' --disable-filter=true &
```
It will convert the address for 8001 which we can access on our browser
```
http://server_ip:8001/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy
```
# Run the above command on you browser and in server_ip add you ip address provided by AWS

![Screenshot_20241104_202055_Telegram](https://github.com/user-attachments/assets/51c7b173-156a-436f-9077-99fc4ebbd38c)

# Installing openstack on VM and creating a VM on it
1. CREATE AN INSTANCE IN AWS AS , WITH OS OF UBUNTU OR WHAT YOU WANT THEN CHANGE SOME SETTINGS TO WORK LIKE TAKING
Amozon Machine Image (AMI)
Instance type
t3.xlarge
AND
STORAGE
50GB
NETWORK SETTING YOU CAN INCLUDE
1. SSH
2. HTTP
3. HTTPS
4. ALL TRAFFIC
2. AFTER THESE CHANGES YOU CAN LAUNCH THE INSTNACE
3. AFTER THAT COPYING THE IP ADDRESS , ADD IT IN PUTTY AND ALSO SELECT THE KEY WHICH HAS BEEN CREATED IN PERIVOUS STEPS , THEN CLICK OPEN , AND YOUR VM IS AGAIN READY
Install the openstack snap
```
sudo snap install openstack --channel 2024.1/beta
```
Prepare the machine
Sunbeam can generate a script to ensure that the machine has all of the required dependencies installed and is configured correctly for use in OpenStack - you can review this script using:
```
sunbeam prepare-node-script
```
```
sunbeam prepare-node-script | bash -x && newgrp snap_daemon
```
It will directly execute it
#Deploy the OpenStack cloud using the cluster bootstrap command and accept software defaults:
```
sunbeam cluster bootstrap --accept-defaults
```
This process will take around 30 min or more/less dependes upon internet speed
```
sunbeam configure --accept-defaults --openrc demo-openrc
```
This command will configure the deployed cloud . It will also take around 5 min .
```
sunbeam launch ubuntu --name test
```
This command will launch our vm which we have created on openstack

# VPC
•Go to VPC and create a VPC then we have to create 4 subnets , where 2 subnets are private and other two are public .


![Screenshot_20241104_202449_Telegram](https://github.com/user-attachments/assets/9b1de56e-f147-4db6-a164-985d76f3603b)


![Screenshot_20241104_202503_Telegram](https://github.com/user-attachments/assets/3ff0a649-2545-4527-8cd0-b75136d830f2)

•Then create INTERNET GATWAY , whic is to be connected to your VPC which is created earliarly.

![Screenshot_20241104_202520_Telegram](https://github.com/user-attachments/assets/b3627ce6-6b80-4d70-b2ee-85da2521fd7d)


•Then we have to create VPG virtual privaye gate, and connect to VPC .

•Now we have to go to the route table and create 2 route table , one for IGW and another for VGW .

![Screenshot_20241104_202616_Telegram](https://github.com/user-attachments/assets/241e0840-5dfe-49b5-8c21-04c35d9b9572)


•Now we have to connect two public subnet in myigw and on other we have to add the private subnets .

![Screenshot_20241104_202629_Telegram](https://github.com/user-attachments/assets/37c75423-59a1-4a0b-b9a6-36bc9436768c)

•now we have to create two instnaces where we have to enable the public IPv4 .

•then on both instance we have to downlaod the web server here i have downlaoded the apache2 server

•after that i chech that my instances are working or not . 

•now we have to create the load balancer

•where we have to give vpc, aviablity zone of the ec2 instance

•then we have to create the target group where we have to select the two insatance we have create then we have to go to helath check edited option which was present below the load balancer is create ,then edit it as given below image


![Screenshot_20241104_202750_Telegram](https://github.com/user-attachments/assets/0dec2ccd-a41e-4321-bed4-014550d97d7b)

•after that come to load balancer where we have to select the target group which we have created then make the load balancer , it will look like the given image below .

# ![Screenshot_20241104_202826_Telegram](https://github.com/user-attachments/assets/e999f175-6622-4fdf-959c-af1d670c92d7)


![Screenshot_20241104_202837_Telegram](https://github.com/user-attachments/assets/fb1cc518-3da3-4315-abae-05c364a847e1)


•Now go to any server and type some commands
```
htop
```
```
seq 999999999999999999999999999999999999999999999999999999999 > /dev/null &
```
