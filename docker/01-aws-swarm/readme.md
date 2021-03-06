## Create a Docker Swarm on AWS

1. Log on to AWS
    1. Ensure you have selected the 'Oregon' region in the top-right
2. Create a Swarm using Docker's Cloud Formation Template
    1. Go to docker's [AWS Page](https://www.docker.com/docker-aws).
    This is also a great place to learn about Docker on AWS.
    2. Click on "Get CE From Docker Store"
    3. Click on "Get Docker" Button
3. In the AWS 'Create Stack' screen, click 'Next'.
Defaults for all fields, except:
    1. Stack name should be docker-yourname
    2. Swarm Managers = 1
    3. Swarm Workers = 0
    4. SSH Key = ...us-west-2...
    5. Resource cleanup = Yes
    6. Cloudwatch logging = Yes
    7. EFS prerequsities = Yes
    8. Instance Types = t2.large
    9. 'Next'
4. Tags:
    1. Owner = ems
    2. Project = docker-training
    3. Email = Your Email
    4. Contact = Your Name
    5. 'Next'
5. Review and Create
    1. Acknowledge - Check
    2. 'Create'
    3. Wait about 10 minutes for 'CREATE_COMPLETE' message
6. In AWS go to the EC2 menu item
    1. Under the running instances display screen
    find a manager instance for your swarm:
    name docker-yourname-Manager
        1. Note the Public DNS: **ec2-xx-xx-xx-xx.us-west-2.compute.amazonaws.com**.
        This will be your management server (port 22)
    2. Under the Load Balancers item, 
    find the DNS of your load balancer (Should start with docker-yourna..).
        This is your base URL (port 80/443).
        
        **You now have a Docker Swarm on AWS.**
7. Set up an ssh tunnel to send docker commands to the Swarm
    1. Instructions are here:
[https://github.com/uscdev/ssh-pipe](https://github.com/uscdev/ssh-pipe)
    2. Test your pipe with a docker command such as:
    **docker service ls**

**Note: Remember to delete your swarm when you are done using
it.**

To delete your swarm:
1. Go to the CloudFormation template page.
2. Select your stack
3. Action -> Delete Stack.
