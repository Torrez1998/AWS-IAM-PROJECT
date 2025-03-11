# AWS-IAM-PROJECT

Use AWS Identity and Access Management (IAM) to control who is authenticated (signed in) and authorized (has permissions) to use your account's resources.

![image](https://github.com/user-attachments/assets/4e22f64d-57ce-4fa0-b42e-76c55f7a2455)


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
The development environment we created is where developers write, test, and debug code before it's deployed to production, which is the live environment that your end users can use! that is why we made two instances. 

# Step 2 

Search IAM in the Search bar and open the dashboard.
we will use AWS IAM to manage the access level that other users and services have to your resources.
![image](https://github.com/user-attachments/assets/89421de5-e18f-4add-b6f4-2a66f546acdf)
![image](https://github.com/user-attachments/assets/09418beb-19d6-4aae-ba21-98e25aec6f4e)

Click on "Policies" on the left side of the page and create a policy.

IAM policy is a rule for who can do what with your AWS resources. It's all about giving permissions to IAM users, groups, or roles, saying what they can or can't do on certain resources, and when those rules kick in.

Switch your Policy editor tab to JSON editor.
![image](https://github.com/user-attachments/assets/90b56671-26b9-4b9c-8010-01f930973a57)

![image](https://github.com/user-attachments/assets/9a030864-3b53-4bde-93d3-41073f20c093)

![image](https://github.com/user-attachments/assets/e156ceb0-1fa2-4dd6-b691-f441e3447eab)

Erase everything and we will create our own policy.

This policy I put together allows some actions (like starting, stopping, and describing EC2 instances) for instances tagged with "Env = development" while denying the ability to create or delete tags for all instances.
Here is the explanation for what this policy will do.

Statement
‍The main part of the policy structure and defines a list of permissions.

‍Effect
‍This can have two values - either Allow or Deny - to indicate whether the policy allows or denies a certain action. Deny has priority. Looking at the first statement, "Effect": "Allow" means this statement is trying to allow for an action.

‍Action
‍A list of the actions that the policy allows or denies. In this case, "Action": "ec2:*" means all actions that you could possibly take on EC2 instances are allowed. Woohoo!

‍Resource
‍Which resources does this policy apply to? Specifying "*" means all resources within the defined scope (see the next point).

Condition Block (optional)
‍The circumstances under which the policy is in action. In this case, the condition is that the resource is tagged Env - development. This means specifying "Resource": "*" in the line above means all resources with the Env - development tag are impacted by your statement.

you will usually always use an amazon template instead as it is best practice but for this i decided to make my own for more understanding on how it works.

![image](https://github.com/user-attachments/assets/ec5bc656-8d6a-48f5-a2a1-f4727b166fc4)

click on next and fill in policy name and description then click "create Policy".
![image](https://github.com/user-attachments/assets/df1ee1c8-12b3-424c-a061-bd8f2bcb4090)

![image](https://github.com/user-attachments/assets/c2d617b6-33b8-4e95-a6f6-5037bb55b12c)

# Step 3

Create an AWS Account alias.
An Account Alias is a friendly name for your AWS account that you can use instead of your account ID (which is usually a bunch of digits, as you can see in the next screenshot) to sign in to the AWS Management Console.
You would create an alias to make it easier to remember and share your AWS console's login URL with others and make it unique.
Go to the dashboard, and on the right side of the page we can create our alias.

![image](https://github.com/user-attachments/assets/64f565eb-0180-433f-8c85-fa04a77de5dd)

In the Preferred alias field, enter Project-alias-yourname.
![image](https://github.com/user-attachments/assets/73456ef7-e5cc-4d42-baef-f1584541278c)

Create alias.
![image](https://github.com/user-attachments/assets/e327afd5-324e-410e-b793-2a1c9c4146f4)
It should be a lot faster for users to find your account and log in now.

# Step 4

new interns dont actually have a way to log in to a team's AWS account yet
You wouldn't want to just share your account details with them. After all, you have access to the production instance, which they shouldn't get access to.

Let's solve this problem using IAM again - this time we're using two other tools called groups and users.
let us create our first User group so we can manage all interns' permissions from one place.

Choose User groups in your left-hand navigation panel.
Choose Create group.
Let's create the first user group!

![image](https://github.com/user-attachments/assets/45f136a3-b1d4-48cf-b7c4-4d4ca0d2a387)

Name user group

![image](https://github.com/user-attachments/assets/1ec0da67-0240-4085-8c58-5bb97c618d42)

Search env and attach the policy that we create in step 3
![image](https://github.com/user-attachments/assets/d244de02-2e6f-45b9-a1ff-9c7c95cfa79a)

Then create
![image](https://github.com/user-attachments/assets/97b86455-0e7b-49f9-964b-cc392b3782fe)

Now it is time to add our users.

💡 Why do we need users in our user group?
IAM users are the people that will get access to your resources/AWS account, whereas user groups are the collections/folders of users for easier user management.

This simplifies managing permissions and ensures consistency across users who have similar access to AWS resources. Imagine if you have a whole team of 5 interns (users) that need the same permission settings.

Choose Users from the left-hand navigation panel.
Choose Create user.
Let's set up this user! Under User name, enter Project-dev-yourname
Tick the checkbox for Provide user access to the AWS Management Console.
If you don't tick this box, your new user won't get to sign in and access AWS services through the Console only access through using more advanced methods.

![image](https://github.com/user-attachments/assets/78931d4d-cdeb-4317-acca-b7c51d283223)

![image](https://github.com/user-attachments/assets/c5360fcc-33e8-491d-b00d-da7f2a910f33)

![image](https://github.com/user-attachments/assets/54e986ce-8691-45c2-bbf9-6f239e7b3371)

Next, add the permissions we just added.
review and create.
![image](https://github.com/user-attachments/assets/f4082278-b09b-4afa-96a3-7f188e487908)

![image](https://github.com/user-attachments/assets/2d45ce4f-5997-424c-aa7e-7894a063d2d7)

We just created a user Group with any users(interns) that are added will inherit the permissions we placed on the User group.

# Step 5 
Using a new incognito window, we will log in to our user we just created.
use the credentials we received.
![image](https://github.com/user-attachments/assets/855ecbad-533e-4fb5-9dfc-174d39baffe6)


![image](https://github.com/user-attachments/assets/d525e911-764d-4d6d-a4d7-3c5395f43333)

as you can see, it looks differnet and things are accessed denied.
Any intern or new imploye should have limited access to things in the organization.

we will now test out the user EC2 console. 
seach EC2 in the search bar and click then we will go into our instances. 

![image](https://github.com/user-attachments/assets/b4f45aa0-1d06-424c-bfe0-15f721eaf2db)

lets test a rule by trying to delete an instance we created as an intern or new employee.

Click on the production instance we are currently on, and then, in the actions section at the top right of the web page, we will manage the instance state.
click on stop and try to change the state.
![image](https://github.com/user-attachments/assets/99168b20-399a-49a1-9a47-22fd3dbc75de)

![image](https://github.com/user-attachments/assets/5334511b-7696-46e9-8c96-5ef6172380d9)

You should get a fail to stop the instance and should still be running.

![image](https://github.com/user-attachments/assets/36bac6cc-c3ce-4f79-9a05-f8ec8fcfa7a6)

Great, now let's try the development instance, same process like we did with the production instance. Try and stop the instance.

![image](https://github.com/user-attachments/assets/589c2abd-523f-49a5-bac1-57de314b7e22)

looks like everything is working.
We are done!
Make sure to delete all instances, users, and policies that we made before logging off or finishing to avoid any extra charges.

In this project, I have learned...

💻 Launch EC2 instances.
🏷️ Use tags for easy identification.
💂 Set up IAM policies accessing EC2 instances based on their environment (development or production)
👩‍👩‍👧‍👧 Create an IAM user and assign them to the appropriate user group with the necessary permissions for their role.
🔓 Test IAM access for the User you've created.

