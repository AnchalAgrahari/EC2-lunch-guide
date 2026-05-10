---
EC2-lunch-guide
---
## LAUNCH an EC2 Instance in AWS
Why are we Launching EC2 :
When we build a website, APIs, or Application on our local system, it only runs while our laptop is turned on and connected to the internet. Once the system is turned off, the application stops running and becomes inaccessible to users
So, how can we host our application on a system that runs 24/7, stays connected to the internet, and is accessible to users anytime?
Solution: **Launch an EC2 Instance**

### Prerequisites:
- **AWS Account:** An active AWS account with access to the Management Console
- **IAM Knowledge:** Basic understanding of IAM roles and permission.
- Basic knowledge about *Networking concept* such as **Subnet** and **VPC**
- Basic knowledge about **Python** for application setup

**Note:**If you are new to AWS, it is recommended to go through the
 AWS Free Tier documentation before proceeding.

### Steps to Launch EC2:
#### Step1: Login into AWS console
After logging into a AWS Management console, you can see a Dashboard that provides access to all AWS web service services. From here, you can easily navigate all the AWS services such as **Amazon Lambda,  Amazon S3,Amazon  EC2, IAM roles.**
<img width="1732" height="919" alt="image" src="https://github.com/user-attachments/assets/f1d51a2d-5a54-4f73-a7c1-16a0b8bd9d0c" />

#### Step2:  Open the EC2 console after signing into the AWS console
Search for the EC2 in the search bar of the AWS management console and click the EC2. This will open the EC2 console, where you can create an Instance.

#### Step3: Launch Instance in EC2
In the EC2 console, if you click on the *“Launch Instance”* button it will start the instance creation process. This will take you to the series of steps to create your instance.
After clicking on the *“Launch Instance”* button, you will see the following page.
<img width="1903" height="874" alt="image" src="https://github.com/user-attachments/assets/d9695a5e-3a14-48ad-b845-91b460f64a84" />
Now, to create an instance, provide the required configuration details.

#### Step4: Provide a Name for an EC2 Instance
Here you have to provide a name for your EC2 Instance. By providing a meaningful name to the instance, management and identification become easier in the future.
<img width="1903" height="874" alt="image" src="https://github.com/user-attachments/assets/210e95af-7630-4ad0-aebc-7a018b16ed17" />
In this case, you can name the Instance *“backend-server”* for the EC2 server.
<img width="1088" height="150" alt="image" src="https://github.com/user-attachments/assets/d7f942a2-fbe0-43cb-a9ae-63b015e336b3" />

#### Step5: Choose an Amazon Machine Image (AMI)
An Amazon Machine Image (AMI) is a pre-configured template that contains the operating system and necessary software to launch an instance. Here, you can choose from various AMIs provided by AWS or the AWS Marketplace. Select the one that best suits your needs.
In this case, you can choose *”Ubuntu”* as the operating system for your Instance
Make sure that the Architecture should be *“64 bit(x86)”* 
<img width="1088" height="708" alt="image" src="https://github.com/user-attachments/assets/c16f4baf-d18f-4f34-9c95-82e56664e6a0" />

#### Step6: Choose an InstanceType
The instance type determines the hardware of the host computer used for your instance. AWS offers a range of instance types with varying compute, memory, and storage capabilities. Consider your workload requirements and select the instance type that meets your needs.
In this case, you can select *“t3a.micro“* as the instance type.

**Note:** The t3.micro instance type is eligible for the AWS Free Tier and provides limited free usage of certain AWS services.
<img width="1088" height="209" alt="image" src="https://github.com/user-attachments/assets/6c6a29e6-7509-4482-acbd-3a7c855e58ab" />

#### Step7: Create a Key pair
To securely access your EC2 instance from your system, you need to create a key pair. A key pair consists of a public key that AWS stores and a private key that you download to your local machine. The private key is used to authenticate and establish a secure connection with your EC2 instance.
You have the option to select an existing key pair if you already have one, or you can create a new key pair by clicking on the *"Create new key pair"*
<img width="1098" height="194" alt="image" src="https://github.com/user-attachments/assets/a941b8ca-d6bd-451c-803b-db718e0ffaa0" />

Upon clicking this button, a dialogue box will appear where you can provide a unique name for your kay pair. Select the Key pair type as “RSA” and choose the private key file format as “.pem”.
Finally, click on the “ Create Key Pair “ button to generate your new key pair.
<img width="612" height="575" alt="image" src="https://github.com/user-attachments/assets/b7a4c221-dff7-43c3-b0f2-ee9482165428" />

**Note:** It is recommended to save the *“.pem”* file on your desktop for easy access during instance connection.

#### Step8: Network Setting
In this section, configure the network settings for your instance, including the VPC, subnet, and security group. These settings control how your instance communicates with other resources and the internet.
<img width="1088" height="637" alt="image" src="https://github.com/user-attachments/assets/eff01da2-3f4d-4de6-910d-f36e9a8e2e55" />

Click the *"Edit”* button to open the network configuration settings.
<img width="831" height="800" alt="image" src="https://github.com/user-attachments/assets/d5d1a69a-1a52-4c3c-b58a-6ef19c9da390" />

In this step, configure the network settings based on how you want your instance to connect and communicate.
So as for VPC you should set it to be default. And for subnet, 
- You have to open the AWS  Management console on the different tab , and Search for VPC in the search bar of
 the AWS management console.
- Open the VPC from the search result, this will open the VPE console
  <img width="1917" height="844" alt="image" src="https://github.com/user-attachments/assets/f73a782d-b5f5-49c8-9b1a-903f1ec27e28" />

- From the VPC dashboard , click on the *“subnet”* from “Virtual Private Cloud”
  <img width="1917" height="844" alt="image" src="https://github.com/user-attachments/assets/cb14c41f-a7fd-4e2a-80fc-f19374ff1a94" />

- A new page will open, which has some subnets , you have to select one of them and copy the *“subnet ID”* from Details.
  <img width="1919" height="274" alt="image" src="https://github.com/user-attachments/assets/edc4dc86-4051-430a-88db-4b28e141430d" />

And finally paste in the subnet column for the network setting of the Instance.

Now for the auto-assign public IP *“Enable”* the block
<img width="719" height="98" alt="image" src="https://github.com/user-attachments/assets/2665cca8-4780-4d8b-8afb-feefbf0ba9a8" />

For Firewall (Security groups) check the option *“Create security group”.*
<img width="773" height="98" alt="image" src="https://github.com/user-attachments/assets/1fe7002d-ba0a-4c7a-832f-62bd95d5c2eb" />

Here, name the security group as *“launch-wizard-1”* and the leave the description block
<img width="1043" height="108" alt="image" src="https://github.com/user-attachments/assets/1370c214-f910-42a9-887b-d05e9d41eb7d" />

Now , for the block Inbound Security Group Rules prefere
Type : **ssh**
Protocol : **TCP**
Port range : **22**
Source Type : **Custom**
Source : **0.0.0.0/0**
These rules ensure that your instance is accessible over the internet and that your application can receive traffic on the required port.
Once all the rules are added, leave the rest of the setting as default and move on to the next step.
<img width="989" height="274" alt="image" src="https://github.com/user-attachments/assets/292e6290-db03-4416-b4e7-4d746d07c90c" />

#### Step9: Configuration Storage
Storage is where all your application files, Operating System, and Data will be stored on your EC2 instance. AWS provides an **EBS(Elastic Block Store)** volume as the default storage option for your instance.
In the *“Configuration Storage”* section, you will see a default storage volume already attached to your instance. By default, AWS assigns 8 GiB  of storage with volume type **“gp3”(General Purposed SSD)**
<img width="1061" height="463" alt="image" src="https://github.com/user-attachments/assets/aa00c741-74a7-4033-934c-ca5a958639ea" />

#### Step10: Launch the Instance
Once you have configured all the required settings – name, AIM, Instance type, Key pair, network setting, security group rules, and storage – you are ready to launch your EC2 instance.
On the right-hand side of the page, you will see a **summary panel** that shows all the configuration details you have selected so far. Review all the details carefully to make sure everything is correct.
After reviewing, click on the **“Launch Instance”** button.
<img width="530" height="768" alt="image" src="https://github.com/user-attachments/assets/35393147-e3f5-46ae-be9b-cec427e33cff" />

AWS will now begin the process of creating and launching your EC2 instance. You will be redirected to a confirmation page that shows the messsge **“Successfully initiated launch of Instance”** along with your **“Instance ID”**
By clicking on the **Instance ID** a EC2 instance dashboard will open, where you can see your newly created instance.

After a moment AWS stares at the instance. Once the **“Instance State”** changes to **“Running”**, your instance is successfully launched and ready to use!.
<img width="1638" height="583" alt="image" src="https://github.com/user-attachments/assets/8784d561-25c0-4128-8d08-f795250511b3" />


### Key Concept: 
- **EC2:** A Virtual computer that runs on AWS cloud.
- **AMI:** A ready-made template of an operating system.
- **Instance Type:** Size and power of your virtual computer.
- **Key Pair:** A password system to securely login to your instance.
- **Securtiy Group:** A firewall that controls who can access your instance.
- **VPC:** Your own private network inside AWS.
- **Subnet:** A smaller section of your VPC network.
- **EBS:** A hard drive attached to your EC2 instance.
