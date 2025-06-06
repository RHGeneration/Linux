![Zorin SQL](https://github.com/user-attachments/assets/e61da5c6-3772-4046-9e0b-c949f2e9d788)

Installing MySQL Server on my Linux Terminal

Im running VMware workstation where I have some local hard drives I use to run multiple Virtual Machines. I like playing with Linux and my favourite operating systems are Ubuntu because of many server applications it can use and Zorin because it resembles close to Windows and is quite close to home. I currently have both Zorin and Windows installed on my local machine and is capable of dual booting so I can pick which operating system to load. I can also save the state of the VM and reopen from the exact state I saved it so I can continue from there without turning on and load the machine.

Right, getting back to the objective, I am going to show on my VM on how to install MySQL server on my Zorin terminal. Its quite quick and easy to do but can be tricky if you do not who what to do.

1. The first step is of course launching the terminal on your Linux machine.
2. Next is to type 'sudo apt update'. This will update all the apps and processes within the terminal. You may be prompted to enter your password as you are doing this with root permissions. 
3. After that then type 'sudo apt install mysql-server'. It will start installing MySQL server and you may be prompted to confirm install which you press Y.
4. Once installed, you need to then type 'sudo mysql_secure_installation'
5. You will be given some questions on how you want your MySQL to be setup

5a. The first tells you to validate password components. This is useful as it gives a metric of how strong your password it can be when you create your password. It makes your SQL account more securer this way. For now as this is my local VM, I will say no. Normally in companies you should always say Yes to this.
5b. The next is Remove anonymous users. You should say yes to this so only you or a trusted user can access the database. As I am an only user I will say no to this.
5c. Disallow remote root login. It's best practice to say yes to this as you don't want someone to remote access this and compromise the database and your root account. As this is a VM, I will say no to this.
5d. Remove test database? By default a test database is added in the MySQL directory and is used for developers or people practising databases. As I do not need this, I said no.
5e. Reloading privilege tables. This ensures after you log out, any changes gets saved. For this I selected yes.

6. After going through the questions. Type on the console 'sudo mysql'
7. You should get a new command line with a different format that starts as 'mysql>' This shows you are now running MySQL and can now create databases.

Here are a few helpful commands to start. (Replace name with something you want to put and remove the brackets)
 
SHOW DATABASES; - Shows list of databases
CREATE DATABASE (name); - Creates a databases
USE DATABASE (name); - Change database directory
CREATE TABLE (name); - Creates a table 
DESCRIBE (name); - Detail of contents in table
