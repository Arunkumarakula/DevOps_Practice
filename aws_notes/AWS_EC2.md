# AWS-EC2

AWS EC2 - Amazon Elastic Compute cloud is a AWS cloud computing service it provides scalable computing capacity. using Ec2 you can develop or deploy your application and virtual servers can run any Os like Ubuntu/Linux/mac/centos/redhat...but most favorable os are Linux/Ubuntu

* Virtual computing environments are known as instances
* Pre configured Templates of Your instance is known as AMI(Anazon Image machine) that package the bits you need for your server 
* Various configurations like cpu/storage/networking for your instance known as Instance types
* Secure Login information for your instance using keypair - AWS stores the Public key and you store the private key in a secure place 
* Additional storage volumes for your instance Data using AWS EBS
* Multiple Physical locations for your Resources such as servers ,EBS volumes know as Availability zones, Region's.
* A firewall that enables you to specify the protocols,ports, source IP ranges that can reach your instances using security Groups. 

**EC2 Purchasing:**

* `On Demand `: pay by the second for the instances That you launch
* `Reservation`: Reserve Capacity for Your Instances in a specific AZ for any Duration 

**EC2 Instance Types :**

* Instance Types refers to a combination of cpu, memory, storage and networking capacity of a virtual machine (VM) in a cloud environment 

* EC2 provides a wide selection of instance types optimized to fit different use cases

1. `General Purpose` : General purpose Instances provide a balance of compute , memory and networking Resources can be used for a variety of diverse workload , such as Webservers/small Databases/Development and Testing Environments.

2. `Compute Optimized` : Compute Optimized Instances are Designed Fo fffr compute intensive Applications that benefit from high performance processors(Designed to run applications that require a lot of processing power and Memory)
Eg : Gaming servers,media transcoding,Hingh performance Web servers(Nginx, Apache,Tomcat)

3. `Memory optimized `: memory optimized designed to fast deliver fast performance for workloads that processs large data sets in memory.

4. `Storage optimized` :Storage optimized instances are designed to handle workloads that require high, sequential read and write access to large data sets on local storage. 
  -They are optimized to deliver tens of thousands of low-latency, random I/O operations per second (IOPS) to applications. 
 Examples : Distributed file systems, data warehousing applications, and high-frequency online transaction processing (OLTP) systems .

`Security Groups :`

* Security Groups are act as virtual firewall for controlling traffic at the instance level
* it contains a set of rules that filter traffic coming Inbound and Outbond of an EC2-Instance
* Security groups are support only allow rules.

`Key-pair :`

* Ec2 uses key to Encrypt and Decrypt login Information.
* Public key uses to encrypt a piece of data ,the recipient uses the private key to decrypt the data.
* The Public-private keys are known as a key-pair.

`Ec2-Access :`

1. Web-Based user interface: The Amazon Ec2 console.If you signed up for an aws account you can access the aws ec2 console by signing into aws management console and selecting ec2 from the console home-page.

2. Aws CLI :Provides commands for a broad set of aws products,and it supported on windows,linux,mac.

`Ec2 windows/linux Instances` :

- An instance is a virtual server in the aws cloud.with aws ec2 you can set-up and configure the operating system and applications that run on your instance.
    
       * Linux Login username as :Ec2-user
       * ubuntu : ubuntu 

`Web-Server(HTTPD) `:

* A web server is a network service that serves content(web pages) to client over the web.
* web servers are also known as HTTP(Hypertext Transport protocol)servers
  Examples : Apache,tomcat,Nginx are making websites are safe and secure.

`Network Interfaces:`

* Each instance has a default network interface,called primary network interface.
* you can create and attach additional network interfaces.

`Elastic IP-Address:`

* An Elastic ip-address is a static IPV4 address designed for Dynamic cloud computig.
* Attaching an EIP to an instance will replace its default public ip address.
* 5 EIP addresses per region.

`EC2 SERVICE QUOTAS (LIMITS): `
 
* When you create your AWS account, we set default limits on AWS resources on a per-Region basis. 
 
**NOTE: You can request an increase for many of these limits.** 


`Ec2-events :`

* Aws can schedule events for your instances such as reboot,stop,start,Terminate.

`Resoures & Tags:`

* To manage your instances,images,volumes,snapshots,you can assign your own metadata to each resorces in the form pf tags.
* tags enable you to categorized in different ways example:owner,purpose,environment.
* Each tag consists of a key and an optimal value.

`AMI-(Amazon Machine Image):`

* Ami is a master image for the creation of virtual servers(ec2 instance) in the aws environment.
* Ami's are used with auto scaling to quickly lunch new servers on demand,and quickly recover from disaster.

`Launch Permissions:`

* PUBLIC : The owner grants launch permissions to all AWS accounts 
* IMPLICIT : The owner has implicit launch permissions for an AMI 
* EXPLICIT : The owner grants launch permissions to specific aws accounts 


`Ami Categories:`

1. community AMI'S :Free to use,with these ami'syour are just selecting the os you want.

2. Market place Ami's :Pay to use.Buying,sharing,and selling AMI'S.Generally comes packaged with additional ,licisenced software.

3. My AMI'S : You can create your self.

`AMI CATELOG :`

* customers can easily search AMI'S specifying desired categories,such as provider,region,Architecture,operating system.

`Launch Templates:`

* Why do you need to specify all the EC2 instance details (AMI-ID, Instance Type and Network Settings) every time you launch an instance?
 
    * Launch Templates is a new capability that enables a new way to templatize your launch requests.  
    * Launch Templates streamline and simplify the launch process for Auto Scaling, Spot Fleet, Spot, and On-Demand instances. 
    * It reduces the number of steps required to create an instance by capturing all launch parameters within one resource. This makes the process easy to reproduce
