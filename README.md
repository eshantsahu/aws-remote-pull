aws-remote-pull

Shell Script to Pull Code via Git on AWS Load Balancer

First challenge you may face when you migrate to AWS AutoScaling is Updating your code in Production after minor changes. If you have environment changes like Python version upgrade, New Application on your machine, you will have to Create New AMI and attach it to your load balancer. But code level changes can be applied by logging In to your Machines and updating code via Git.

But the problem begines when you are in autoscaling mode and You have number of machines running. logging In to All machines and updating code can be little bit manual. That's the point where this script comes in play.

For this script to work, following programs are required to be installed :

    AWS CLI with Setup
    sshpass

You can follow this link to install AWS CLI http://docs.aws.amazon.com/cli/latest/userguide/installing.html

To Setup AWS CLI visit http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html

To Install sshpass run following command in terminal

sudo apt-get install sshpass

Once you are done with setting up, You can Edit the script to add the name of your load balancer in LOAD_BALANCER_NAME variable.

The script works in following manner : 

1. It calls AWS CLI to get details of the Load Balancer with 
	
	aws elb describe-load-balancers --load-balancer-name LOAD_BALANCER_NAME

This command shall return all the details of the load balancer including instance Ids of the Machnines.

2. Instance Id list returned by the first step are again send to AWS to get Public IP of these Instances using following command 

	aws ec2 describe-instances --instance-ids INSTANCE_ID_LIST

3. Once we have the Public IP list of instances, we can ssh them to make changes on them. sshpass is a utility designed for running ssh using the mode referred to as “keyboard-interactive” password authentication, but in non-interactive mode.
	To install sshpass type :

	sudo apt-get install sshpass

	Below is the example how sshpass works with ssh

	sshpass -p "YOUR_PASS_PHRASE" ssh -o StrictHostKeyChecking=no USER_NAME@$IP_ADDRESS -i YOUR_PEM_FILE.pem 

	
4. So when combined with inline command argument, The ssh command looks like 

	sshpass -p "YOUR_PASS_PHRASE" ssh -o StrictHostKeyChecking=no USER_NAME@$IP_ADDRESS -i YOUR_PEM_FILE.pem "cd /var/www/html/myApp/;git pull origin master"




