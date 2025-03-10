# AWS course project
## App Service
AWS Lambda : Serverless architecture. 
--> Lambda performance depends on memory configurations. 

--> Python
--> .net core
--> java
--> go
--> ruby
--> Node.js

Lambda-canary : It open the required website and look for the string we have given.

google.com --> Google

--> Incresing the memory and timeout values.
--> Changing the required permissions on lambda associated roles. 
--> Can we run lambda within a VPC..?? YES
	--> FOr Lambda role Make sure you associate "AWSLambdaVPCAccessExecutionRole"


-------------

Task : Am sharing some lambda functions... Deploy the lambda functions and test it. 
(1. Volume Status check
2. Volume encrytption check
3. Instance Stop
4. Instance Start)

Task : Create an s3 bucket, When we upload any object to s3 bucket, It should trigger "Stop-Instance" lambda function and instance need to stop.

Task  : What ever the file names starting with "A/a" should move to another s3 bucket.

Task  : What ever the file names ending with ".bkp" should move to another s3 bucket.

Task : Create a lambda function to perform telnet test.  get output as "Telnet success" or "telnet failed".

telnet google.com 443

Task : Get the list of IAM users whoever not logged in to aws account in last 1 hr.

Task : 
** Get the list of IAM users accesskeyid and secretaccess keys not used in last 90 days. Send the list of users in .csv format file and write it to an s3 bucket.

======================================================================================================

D: 26/02/24

How many Account you manage : 
For Every CLient : Sandbox/Training, Dev, SIT/SQA, UAT and PRD ==> 5 Accounts
Central logging account and Management Account

Interview : Atleast 7 Accounts..

AWS Organisations along with SSO: 

Management account : From single aws account, we can manage multiple accounts. Centralized billing option for multiple aws accounts. 

SCP : Service Control Policy : We can apply policy at Org level / OU level to manage permissions on AWS accounts.

identity source : SSO / Active Directory
Permission Sets : set of permissions in aws.
you can see/find only org joined aws accounts in SSO.


AD : https://www.youtube.com/watch?v=RDlBoAHVmZs
Ad Connector : https://www.youtube.com/watch?v=Ca259gg6SoM
Linux to AD : https://www.youtube.com/watch?v=LWi9-XL2vWQ

Switch role : https://www.youtube.com/watch?v=sZiiB4yF0VY


================================================================================

AWS Cloudformation : IaC Infrastructure as Code : JSON/YAML : 
--> it's free. 

Prepare a cloudformation stack. This stack are reusable.
--> CLoudformation created resources will delete automatically when we delete the cloudformation stack.

rollback on failure : yes

2 ec2 instance, 3 s3 bucket, 1 rds instance

AWS Console Recorder : Browser plugin
Former2 : former2.com

https://aws.amazon.com/blogs/machine-learning/plant-leaf-disease-detection-with-amazon-rekognition-custom-labels/


Cloudformation Playlist: https://www.youtube.com/playlist?list=PLneBjIzDLECnvHUiqAe5DYHcnXSOTWeXO

==============================================================================

1. Launch an ec2 instance and use Former2 browser extension and generate the CF script and deploy it. 

2. Create an s3 bucket and configure lifecycle rule. Use Former2 to generate the cft and deploy it by changing the bucket name and test it.

3. Launch an ec2 instance using cloudformation template. While launching use userdata to make it webserver also, open post 80 and 22 open for everyone. Deploy it and test it.

Do the above tasks with the help of chatgpt, if required. 

==============================================================================

D: 28/02/24

Codecommit
CodeDeploy
Codepipeline
codebuild

"S3/codecommit/git" --> Deploy to "ElasticBeanstalk"

________________

Create an IAM user, Make sure he has "Adminaccess / Codecommit full access", Generate "programatic keys (Accesskeyid&secretaccesskey)" and configure it in your local laptop.

aws configure
accesskey : 
secretaccesskey : 
region : ap-south-1
output :  

You need to have some softwares. 
1. Install Python
2. Install git
3. install grc : pip install git-remote-codecommit


git add .
git status
git commit -m "commit msg"
git push
git pull
git clone

Task : get familier with above commands.


GIT : 
https://www.youtube.com/watch?v=rtI26X6FJX0&list=PLneBjIzDLECkdgoinrTO7D519zgPEmcte


================================================================================

SNS : Simple Notifications Service : 
--> We can create a Topic, We can add subscribers (email, website endpoint, sqs, mobile). 
--> Subscriber need to confirm the subscription. 
--> Push based messaging service. 

SNS also supports Push notifications service. Works based on mobile operating systems. 

Task 1 : 
==> Project Video: https://youtu.be/Fk4LIFULlYw

Task 2 : Create CICD pipeline to deliver php webpagfe via beanstalk.

=============================================================================================

https://www.youtube.com/watch?v=xl-29WXdQXg&list=PLneBjIzDLECnvHUiqAe5DYHcnXSOTWeXO

https://github.com/avizway1/aws-projects

=======================

Please complete below projects
project 2 : https://www.youtube.com/watch?v=YEIuuVKIy8U
Project 3 : https://www.youtube.com/watch?v=1IJJmWKzeXQ


============================================================================================

ECR : Elastic Containers Repository : Place to store container images.
ECS : Elastic Container Service : 

1. Install docker in your local laptop
2. Install aws cli tools and configure an IAM user. (aws configure)

ECR process : 
1. Connect to the repo
2. build "docker build -t imagename ."
3. Tagging "docker tag imagename:latest"
4. Push it "docker push URI/imagename:latest"


Fargate : Fully managed by AWS. No backend instance, AWS manages everything.
EC2 : we will get an instance, COnstainers runs within instance, We can login and perform os level operations.
ECS Anywhere : We can install ecs agent on our own hardware, and deliver our application.


Task Defination : Task definitions specify the container information for your application, such as how many containers are part of your task, what resources they will use, how they are linked together, and which host ports they will use.

1. awsvpc — The task is allocated its own elastic network interface (ENI) and a primary private IPv4 address. This gives the task the same networking properties as Amazon EC2 instances.

2. bridge — The task utilizes Docker's built-in virtual network which runs inside each Amazon EC2 instance hosting the task.

3. host — The task bypasses Docker's built-in virtual network and maps container ports directly to the ENI of the Amazon EC2 instance hosting the task. As a result, you can't run multiple instantiations of the same task on a single Amazon EC2 instance when port mappings are used.

4. none — The task has no external network connectivity.

** https://ecsworkshop.com/
https://eksworkshop.com/
https://www.youtube.com/containersfromthecouch
https://kodekloud.com/courses/docker-for-the-absolute-beginner/
https://www.youtube.com/watch?v=fqMOX6JJhGo
Terraform : https://www.youtube.com/watch?v=iRaai1IBlB0
Ansible: Refer youtube channel.


Task : Practice End to end ( 
1. launch ec2 instance, install docker
2. Create a Dockerfile and test it locally
3. Push it to ECR
4. Create a Task Definition
5. Create an ECS cluster
6. Run task
7. Run as Service along with Load Balancer
)
______________________________________________________________________________________

D: 06/03/24

SQS : Simple Queue service : pull based messeging service. 
Ex: AutoScaling group works with sqs service. 

--> Standard
At-least-once delivery, message ordering isn't preserved
At-least once delivery
Best-effort ordering

--> FIFO (Name should end with .fifo) 
First-in-first-out delivery, message ordering is preserved
First-in-first-out delivery
Exactly-once processin

Maximum message size : 256 kb  (AWS cost us based on chunks)
1 chunk = 64 kb..   

1 million req under free tier eligibility.

__________

SES : Simple Email Service : If we want to send messeges on behalf of another email / domain name, We can use SES service. 

--> For bulk email sending, we need to use another service "Amazon pinpoint".
https://www.youtube.com/watch?v=g_NTrw3UU0w

mailchimp
easy sendy pro

_________________________________________________________

AWS Budget
AWS Cost Explorer 

Storage Gateway : https://www.youtube.com/watch?v=wmcBSHpoHhs	(good to know - certification)
CW Custom Metrics : https://www.youtube.com/watch?v=Fe2mEkWiNSA   (good to know)
Gloabl Accelerator : https://www.youtube.com/watch?v=ELEW3R5vgCA. (optional / ignore)

GIT : https://www.youtube.com/watch?v=rtI26X6FJX0&list=PLneBjIzDLECkdgoinrTO7D519zgPEmcte

## Instructions
- amazon-linux-extras install epel -y

- yum install stress -y


- chmod +x asgload.sh			
==> Adding Executable permissions

./asgload.sh				
==> running the script