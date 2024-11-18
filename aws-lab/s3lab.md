### S3-Simple storage service :

 Downfalls(EBS/EFS):

* `EBS` : It is a server specific storage we can attach to only one ec2 instance.
* `EFS `: It is a vpc specific storage we can ec2 instance from the same vpc if the instance in     another vpc it can't
* `s3` : Any user,any account,any vpc,used to attch local computer
---

* It is a weidly used storage service for aws,there is n particular limit
- It is a global service(whenever we store the data those data can replicate multiple datacenters in the backend)
- s3 is a scalable service.
- s3 biling is similar to EFS IT IS a metered service.
- s3 is a serverless storage dont need any instance or server.
---
### S3 components:

* `S3` :Amazon Simple Storage Service (Amazon S3) is an object storage service that offers industry-leading scalability, data availability, security, and performance. You can use Amazon S3 to store and retrieve any amount of data at any time, from anywhere.

- Buckets
- Objects - Fundamental entity stored in aws s3(Files/Floder)
- bucket settings
- Acl settings
- versioning
- Replication
- lifecycle polocies
- web-hosting (host a web website)

---
 `S3 creation `:
* Go to Console - Search in dashboard s3
  - CREATE S3 bucket
  - Name(must be globally unique)
  - Acl disabled
  - block all public access
  - Bucket versoining-Disable
  - bucket key - Enable.
  - create
----
* There is no limit for the number of objects
* The size of each object should not exceed 5TB(terabyte) close to 5240 GB
* Uupload any type of files(code/images/videos/document)
---
  - Choose created bucket and add files
  ---

* every file as its own URL,if we tried to browse the URL it shows Access Denied due to there is no permissions for those bucket,if we want to midfy the permission
        {These all bucket level settings}
    - choose file and select permissions
    - Block public access-Edit (remove Block) and save
    - Object ownership-Edit-Enable ACL-Bucket owner prefferd
    - ACL(most important layer for access)-Edit-Eeryone(LIST/READ)

----
* We can give access to another aws user through s3 bucket Acl.

    - Go to objects select the object-Actions-Make public using ACL(Now try to Browse).

`preassingned URL:` We have another option for make it public that is preassigned URL without modify any settings.
    -Actions-preassigned URl (minutes/HOURS) AVAILABLE only for limited time(1-12hrs).

* s3 is widely used for streemings.

### S3 versioning :

* we can retrive the deleted files through versioning(whenever we creating a bucket versioning is must be enable)
     - properties-Bucket versioning-Edit-Enable
     - switch should be always off(switch off we can recover delted files if it is on we cant)
     - if we want to recover delete the delete marker originals will be recovered.

### Static Web-Hosting(only works for static) :

 - create a bucket-upload any code(GitHub-mario game)
- code has multiple urls but s3 as unique web hosting link.
  - properties-Static webhosting-Edit-Enable
  - hosting type - host a static website
  - index document - index.html
  - edit all permissions in permissions.(instead of this we can do with policy:S3 bucket policy for web-hosting)

  {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::Bucket-Name/*"
            ]
        }
    ]
}
 
---
* Always store the data close customer location .
--- 
#### Replication :

* if the customers changes his location then we have migrate all his storage then we have to download everthing it takes more memory ,rather than this process we have Replication.

  - Create a 2 in different regions new bucket
  - default everything - create.
  - choose one bucket which is not empty.
  - Go to management-Replication(Duplication)
      - create replication rule(enable bucket versioning)
      - Name
      - source bucket-Apply to all objects
      - Destination-choose a bucket in this account-Browse s3-choose path
      - create a new role-iam
      - remining Default.
                   -save
   - create batch operations job-job run options
        - Automatically run the job
        - permissions-create a new iam role
                                     -save
* after creation it will open replication dashboard in the minutues,after created once check the new bucket.(it will take time depending on file size)
---

### Lifecycle rules :
 - moving the files from one storage class to another storage class -Lifecycle rules
 - It helps to store the file cost effectively
 - It deletes the files after expiry of files instead delete by us.

- go to management-Lifecycle rule
   - create lifecycle rule
   - name
   - choose a rule scope - apply to all
   - life cycle actions- Transition current versions btw storage classes
                       - expire current versions of objects
   - Transition current versions of objects btw storage classes
                      - standard-IA(By default)
                      - Glacier Deep archive
                      - Glacier instant
              {this is will use in Hospitals medical records,Financial institutions}
     - Expire current  ersions of objects - 365
                                           - create rule
-----
1)How do you automatically setup transitioning of objects..?
Ans: LIFECYCLE RULES

### Aws Transfer Family :
 
* upload s3 files 160gb more than we can use -Transfer family
* aws transfer family whenever we want to transfer files into the cloud from local

* gO TO a transfer family
   - create a server-choose SFTP
   - Identity provider - service managed
   - End point - public
   - Next
   - Domain - S3 - next
   - loging - new log - skip all-Next
   - create

* create a s3 bucket(after created we have to give accesskey,create iam role to give access to bucket)
  - Go to IAM 
    - ROLES-Create role-use case : Transfer
                        - Next
    - permissions-S3 full access
    - Role name - create role
 - open  terminal
   - ssh-keygen -f "arunkey"
   - enter-enter
   - ls
   - cat arunkey.pub (copy)
   - go back to s3 add user(create)
       - name
       - role-s3 transfer family
       - Home directory - bucket name
       - ssh pub key(paste)
                     -Add
  * scroll up and check user
  * to exachange the data we need a sftp tool(WinSCP)
             - WinSCP
                - sftp
                -  hostname - copy endpoint and paste
                - port 22
                - username - arun
                 - advanced 
                    - ssh
                      - authentication
                          - updated private key (arunkey)
                                  - save and login

 * It will directly open your local and dragg files from local to cloud to local,if get any errors just skip






