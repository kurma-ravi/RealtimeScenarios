# AWS RealTime Scenarios

## 1. How to Login to Linux EC2 instance Using customized user ?

     1. Login to EC2 instance using "ec2-user" via Mobaxterm:
		sudo su -
     2. Create a customized user & set passwords
		useradd ravi
		passwd ravi
     3. You need to uncomment the below statement in "/etc/ssh/ssh_config" file
		cd /etc/ssh/
		vi ssh_config
			PasswordAuthentication yes
			#PasswordAuthentication no
     4. Restart sshd service
		service sshd restart
     5. Now, Login as the customized user(ravi) from Mobaxterm instead of "ec2-user"
