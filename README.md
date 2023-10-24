# AWS-EC2-BACKUP-AND-RESTORE
Step.1
-	Create your primary ec2 instance 
i)	Give it a name
ii)	Select Amazon linux 2 AMI
iii)	Select a vpc and a subnet that you prefer(private or public)
iv)	Create an ssh key if you don’t have one already(because we are to need it to securely logon to our instance through ssh). When create , save it somewhere safe on your computer.
v)	Select or create a security that atleast allows port 22(ssh)
vi)	Leave the ebs storage to the default(8gib)
vii)	Go to the advanced settings at the bottom and scroll until you find user data, paste this: #!/bin/bash
# Use this for your user data (script from top to bottom)
# install httpd (Linux 2 version)
yum update -y
Then click launch instance

Step.2
-	Create a file 
i)	ssh into the ec2 instance using your terminal for the mac user and command prompt for windows user: first locate the ssh key you created in the early steps.
ii)	After locating where you saved it, run the chmod 400 <your-ssh-key.pem> command to make sure it’s read-only. Replace the <your-ssh-key.pem> with the actual name for your key.
iii)	Then to ssh into your instance, run this command and replace the <your-ssh-key.pem> with the actual name for your key and the <public- ip-address>: 
ssh -I “the <your-ssh-key.pem>” ec2-user@ec2- <public-ip-address>.computer-1.amazonaws.com
iv)	You’ll then be prompted with a yes/no question, type yes
v)	When logged in create a file(like file.txt). use the cat > filename command replace the “filename” with your preferred name in my case I used file.txt. With the cat command you’ll be prompted to add some data into the file on the next line, write in Hello world, then press ctrl D to save and then ctrl c to exit the prompt.
vi)	If you want to see what you wrote run cat file.txt or what file name you gave yours. You must see the Hello world text.

Step.3
-	Create an image of your primary instance
i)	Select the primary instance 
ii)	Go to actions and find images and templates
iii)	Select create image
iv)	Give it a name and description
v)	After select create image
vi)	Then on the left pane under images select AMIs you’ll see your image being created or already created and available. If you don’t see your image, make sure you selected private images in the filter which is on the left side of the search field.
vii)	When you find your image and it shows available under status, select it.
viii)	On the top right corner you’ll see a button stating Launch instance form AMI, click it to launch a new instance for that image.

Step 4.
-	Check if the file.txt file is on the new launched instance.
i)	After the instance is launched and running, ssh to it and try to find the file you created in the primary instance, and make sure that it was captured when we created the image.
ii)	If you find, Congratulations! You backed up and restored an instance.


HOW IS THIS HELPFUL?
This skill is exceptionally valuable and a best practice for ensuring a highly available architecture. In situations where your primary instance experiences a failure, this skill enables you to swiftly initiate a new instance, ensuring that all files and resources are readily accessible. It serves as a critical component of disaster recovery preparedness.
![visualization of the project](img width="1006" alt="backup" src="https://github.com/MarvinMuhangi/AWS-EC2-BACKUP-AND-RESTORE/assets/142567693/8c01a997-8fea-48bc-a081-0d2b93d58a11")

