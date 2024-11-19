### Aws Load-Balancer(Lab)
![preview](images/LB-architecture.png)

* login into the EC2(dashboard)
  - click on launch instances
  - Name of the instance
  - select AMI(linux-2)
  ![preview](images/ec2-1.png)
  - instance type(t2.micro)
  - select keypair
  ![preview](images/ec2key.png)
  - network(VPC-default)
  - security group-ssh/http

* click on advanced details
  - select-placement group
  - create placement group
  - Name of pg 
 ![preview](images/pg1.png)
  - strategy :partition
* go back to instance creation and select created pg
 ![preview](images/pg2.png)

* `Add user-data` and choose `No.of instances` you want-click on lunch
 ![preview](images/adduser.png)

* `create a Target group`(it stores the collection of the server like which server/vpc/subnet/ip...)
  - click on Target group
  ![preview](images/TG1.png)
  - choose Basic configuration-instances
  - Group name
  - everthing is default
  - Health chceks 
  - check path-/
  - Healthy threshould-3
  - unhealthy threshould-2
  - timeout - 3
  - interval- 20
  - success code- 200
  - next
* it shows register Target(click 0n your target )
  ![preview](images/TG2.png)

1. select include as pending below
2. click on Create Tg

* ` create a Load-Balancer`
1. click on create load balancer
2. choose application lb
3. Name
4. scheme-ineternet facing
![preview](images/lb1.png)
5. create security group
![preview](images/TG-SG.png)
6. name the sg and inbound-ssh/http
![preview](images/TG-SG1.png)
7. listeners-http and ecom
![preview](images/TG-SG2.png)
  
* click on target groups it shows initail
![preview](images/register%20groups.png)
* click on Load balancer it shows DNS IP
![preview](images/DNS.png) 
copy DNS and try to access on Browser it shows Ecom web page
![preview](images/WEB-PAGE.png)

### cloud watch:
* go to cloud watch dashboard
1. create cloud watch
2. give name 
3. select metrics(eg:number)
4. select add metrics graph Eg:ec2
5. select your instance id and paste on metrics  serach box
6. select-pre instance metrics
7. select cpu utilization
8. create widget
  now it shows cpu utilization greph
  ![preview](images/cloudwatch.png)

### SNS(Simple Notification Service)
1. SELECT topic name(ecom)
2. select standard
3. create topic
4. create subscription
5. protocol-email
6. Endpoint-arun@gmail.com
7. create
8. open your email account and confirm sns notification
![preview](images/sns1.png)
![preview](images/sns2.png)

* go to cloud watch click on `Hamburger` (3lines)
1. click on all alarams
2. select metrics(eg:ec2)-copy ec2 instance id and paste
3. select preinstance metrics
4. select cpu-utilization
5. coditions-static-greater
6. than is 80
7. Next

* configure actions
1. in alarams
2. select an existing sns topic
3. send a notification to(ecom/arun)
4. ec2 action-in alaram-select terminate or stop
5. Next
6. in alaram name(ecom)
7.preview and create

* open your server which is selected to cloud watch
1. connect server
2. To increase cpu utilization give below commands
```
sudo yu install -y epel-release
sudo amazon-linux-extras install epel
sudo yum install -y stress
stress --cpu 1 --timeout 10000&
```
![preview](images/connect1.png)

* to check cpu utilization give a command `top`

![preview](images/connect2.png)

* open email and check the notification

![preview](images/snsalaram.png)

* open ec2 - check the instance is terminated or not..!

![preview](images/server-terminate.png)






  
