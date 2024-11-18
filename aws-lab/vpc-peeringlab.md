### vpc-peering
* Here there is TWo vpc's they are working for one client (Flipkart),one company(dell) is mainting data of flipkart and another copmany(wipro) maintaing Payment information of flipkart-these are very crucial they both maintaing in private Databases.

* Here wipro company request to dell flipkart customer details samething dell reruest to wipro paymentbdetails of customers(Requesting access to each other),sharing information from one pvt server to another pvt server.

* It doesn't possible directly share the information because it is an private subnets.

##### LAB

* create a TWo vpc network's
* create a private Inatnaces in two different networks
 - launch 1st ec2 in dell pvt
   - name(dellpvt)
   - AMI-linux-2
   - t2.micro
   - keypair
   - network(dell vpc)
   - subnet is pvt
   - public-ip:Disable
   - sg: default
- launch 2nd ec2 in wipro pvt

* Now to connect this servers if we try to connect the conection will not go through because the pvt server is comming out of a private subnet,in pvt subnet doesnt have an access to internetgateway that means we can't connect this server from www(world wide web),if we want to connect this server we have ro create a jump server 

- In order to connect to the pvt ec2 we need a bastion host or jump server.

* `bastion host` : It is a special computer that plays the role of a gatekeeper between a device and your private network

- launch a public ec2 in both dell-wpro servers.
   - name-dellpub/wipro
   - linux-2
   - keypair
   - vpc-dell/wpro
   - subnet-dell pub
   - ip-enable
   - sg:defaut

* here we cant connect directly to pvt server so here we try to connect pub server(try to connect)

* here i want to connect a pvt server from public server.
- copy a pvt ssh -i@ip and try to access on pub instance(it shows permission denied) because keypair is not accesible

### Transfering pemfile into private server :
- open new terminal
  - scp -i .\demo.pem ec2-user@publicip:~(secure copy)
- go back to conncted private server terminal and check
  - ls(it shows demo.pem)-try to connect(it shows warning)
  - ll(it shows permissions)
  - chmod 400 demo.pen(read access)
  - now give ssh -i "demo.pem" ec2-user@ip(it connects)

* here we just jumped from pub to pvt server it is called as bastion setup,to the public server i connected to pvt server beacuse they share the lan(local area network)

* same methodoly for another network also before that we have to change our names of the server
  - sudo hostnamectl set-hostname dell-pvt
  - sudo init 6(to restart the server)

* rather than using bastion host we have a option `AWS-ssm`(sessions manager) 
#### transfering data dell to wipro

* In the dell pvt server i want to add some file/pem now this file i want to transfer to wipro pvt server
  - scp -i demo.pem dell-data.txt ec2-user@wipropvtip:~
   ( once check in wipro pvt server terminal)-it shows connect lost.

#### vpc peering :
* networking conncetion btwn two networks
* vpc peering is like a two way connection is like a friend request(reject/accept)

* go to vpc dashboard 
  - peering connections
  - create peering connection
     - name(dell-peering)
     - vpc-id(dell)
     - select another vpc to peer with(my acc)-wipro vpc
     - create

* To accept peering go  to actions (accept/reject requests)  
   - now once give a command scp -iwipro(it doesnt connect)
* once the connection is active modify `dell pvt rout table`
   - go to routes
   - add - desination(dellvpc N/W cidr)
   - target : peering
   - save
* same as `wipro pvt route.`

* once the route tables are updated we can start sending data and receving data across both pvt N/W's

  - try to give scp
  - ls