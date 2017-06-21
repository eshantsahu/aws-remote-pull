# aws-remote-pull
Shell Script to Pull Code via Git on AWS Load Balancer

First challenge you may face when you migrate to AWS AutoScaling is Updating your code in Production after minor changes.
If you have environment changes like Python version upgrade, New Application on your machine, you will have to Create New AMI and Attach it to your load baalancer. But code level changes can be applied by logging In to your Machines and updating code via Git.

But the problem begines when you are in autoscaling mode and You have number of machines running. logging In to All machines and updating code can be little bit manual. That's the point where this script comes in play.
