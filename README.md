# AWS-IAM-PROJECT

Use AWS Identity and Access Management (IAM) to control who is authenticated (signed in) and authorized (has permissions) to use your account's resources.

# Tools
  -EC2 instances
  -IAM policies
  -IAM Users and User Groups
  -AWS Account Alias

# Job Objective for Project
  -⚡️ Boost our computing power to match increased traffic to the website.
  -👩‍💻 Onboard an intern - they should have the right permission settings to contribute while keeping the company's resources secure.

# Step 1 

  -Launch two Amazon EC2 instances.
  -Log in to your https://console.aws.amazon.com/ or create an account.
  -Search EC2 and click.

 ![image](https://github.com/user-attachments/assets/4dd3c7e6-4297-4e5a-8128-2d97f6346346)

![image](https://github.com/user-attachments/assets/7f499f1b-5725-4045-9237-60eba06c21a0)

Make sure you are using a region that is closest to you.
![image](https://github.com/user-attachments/assets/47bb96aa-2133-4e10-a4e3-976e35f4daa0)

Next, in the console, launch an instance.
![image](https://github.com/user-attachments/assets/7a19c5c8-5011-4159-b712-430bad5db477)

In an EC2 instance, you can customize your EC2 instance's CPU, memory, storage, and networking capacity, and more to however much you need!

Create a unique name

![image](https://github.com/user-attachments/assets/6e8d4432-6025-4be6-be55-0f19f0749e06)

 We will add some tags to this. And what are tags for? They are useful filters when you're searching for something, Grouping, mass management, and applying security policies. You will see how it works in this project later.
 Click Add additional tags and add a key and a value.
 Key: Env
 Value: production
![image](https://github.com/user-attachments/assets/9fa95599-8af5-4bc5-a2ef-74e23265a63f)

confirm, then we will use Amazon linux as our Amazon machine image(AMI) because it is free to use 
![image](https://github.com/user-attachments/assets/1b414d3d-de17-418f-a7e3-2fe0b20cf659)

Instance type, same thing use what is free. 
We will not use a key pair for this as it is not needed for this project. 
Proceeding without a key pair means you won't have SSH (Secure Shell) access to your instance, which is generally not recommended because it limits your ability to troubleshoot or manage your EC2 instance through a secure way outside of the Console. It's always more safe and more flexible to have a key pair set up.

![image](https://github.com/user-attachments/assets/1fe5695d-f491-4285-a32c-edb506080708)

For simplicity, we will launch the instance.
We skipped configuring network and storage settings for simplicity in this project. These settings are crucial for fine-tuning your EC2 instances' performance, security, and connectivity, but for this project, we'll focus on the basic steps of launching instances with minimal configuration.

Now lets launch another instance.
![image](https://github.com/user-attachments/assets/b11a8c65-b4f8-4860-be43-e4236a911a85)

Name instance with "Development" instead of "Production"
For the tags we will use 
 Key: Env
 Value: Development

 ![image](https://github.com/user-attachments/assets/fc3ac3cd-f6da-4c0c-aed0-ced7c5b20512)
![image](https://github.com/user-attachments/assets/bd7fec71-f8c5-493b-876f-c6a7176e34ea)
proceed without a key pair again.
then launch instance.

What did we just do?
The development environment we creeated is where developers write, test, and debug code before it's deployed to production, which is the live environment that your end users can use! that is why we made two instances. 

# Step 2 
