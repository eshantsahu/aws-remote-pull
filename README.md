# aws-remote-pull
Shell Script to Pull Code via Git on AWS Load Balancer

First challenge you may face when you migrate to AWS AutoScaling is Updating your code in Production after minor changes.
If you have environment changes like Python version upgrade, New Application on your machine, you will have to Create New AMI and attach it to your load balancer. But code level changes can be applied by logging In to your Machines and updating code via Git.

But the problem begines when you are in autoscaling mode and You have number of machines running. logging In to All machines and updating code can be little bit manual. That's the point where this script comes in play.

For this script to work, following programs are required to be installed :
1.	AWS CLI with Setup 
2.	sshpass 

You can follow this link to install AWS CLI 
http://docs.aws.amazon.com/cli/latest/userguide/installing.html 

To Setup AWS CLI visit
http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html

To Install sshpass run following command in terminal

sudo apt-get install sshpass

Once you are done with setting up, You can Edit the script 



