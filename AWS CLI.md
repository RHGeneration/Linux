![AWS CLI](https://github.com/user-attachments/assets/cce32a67-fb0a-43f0-99c7-139189657ab5)

INSTALLING AWS CLI

I thought I try my hand and install an Amazon Command Line Interface (CLI) on a Amazon Linux server. The goal of using the CLI was I wanted to grab a policy document from the management console inside the IAM service. While it was easier to grab it directly from the management console, I wanted to see if I can do this from the CLI instead.

First I had to grab the CLI zip package from Amazon using the input:  |curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"|
Then I would need to unzip the package using unzip -u awscliv2.zip, then type |sudo ./aws/install|.
Once installed, I would need to confirm the installation by verifying the version of the CLI using the command |aws --version|.
This gives me an example output like this: aws-cli/2.7.24 Python/3.8.8 Linux/4.14.133-113.105.amzn2.x86_64 botocore/2.4.5

GRABBING A POLICY DOCUMENT IN JSON FORMAT

Some steps will need to be achieved in order to acquire the Policy document within the user's IAM rule. This document details what services in the AWS the user is permitted to use and modify.

I would need the IAM user's access key and a secret access key. This can be created and found inside the users tab inside the IAM services in the AWS Management Console. Once I have those, I would go back on the CLI terminal and I would type the command: |aws configure|

I would add the access key first, then next the secret access key. I then type the region name which would be where we are using our AWS account.
Then I add the output format which I want it as a JSON format. 

Now it's ready for me to create the output. First I type aws iam list-users. It would show me all the list of users in the IAM service. Only one user is displayed. Next I need to see the list of policies that are in the user's IAM account. I then enter aws iam list-policies.
Only 2 policies are being displayed here. I need the JSON file for the first displayed policy. 

The next step is knowing the command to extract the policy. To do this I needed to access the AWS CLI documentation. I searched for policy and found a list for commands for policy. The get command is Linux's term to save the file I needed, so I searched for get and found the command for get-policy. As I read the document, the command I required needed me to replace the arn code and the name of the policy file within the code.

After altering the code, I would then type the following: aws iam get-policy-version --policy-arn arn:aws:iam::175182824121:policy/lab_policy --version-id v1 > lab_policy.json

This will not only tell me what the user is allowed to operate and modify in the AWS management console, but it will also print out the file in JSON format, detail the JSON version and save a copy of the file. Once saved it will then be transferred to an S3 bucket which I can access and view from there. Alternatively I can type ls -a and I can see the directory and can confirm the Policy JSON file has been successfully created inside the CLI terminal.
