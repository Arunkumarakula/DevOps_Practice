#### AWS-S3(Amazon simple storage service)

* S3-Amazon `Simple Storage Service` (Amazon S3) is an object storage service that offers industry-leading scalability, data availability, security, and performance. You can use Amazon S3 to store and retrieve any amount of data at any time, from anywhere.

#### Key Features :

1. Object Storage: Store and retrieve any type of data (e.g., files, images, videos).
2. Scalability: Store unlimited amounts of data.
3. Durability: Data is stored redundantly across multiple servers.
4. Security: Data encryption, access controls, and versioning.
5. High Availability: Data is available 99.999999999% of the time.

* S3 is a global service
* s3 is a serverless storage(No need to create any server)


#### Benefits:

1. Low Cost: Pay only for stored data and data transfer.
2. Flexible: Store and retrieve data from anywhere.
3. Reliable: Data is duplicated and stored across multiple servers.
4. Secure: Data encryption and access controls.
5. Compliant: Meets regulatory requirements (e.g., HIPAA, PCI-DSS).

#### Use Cases:

1. Data Backup and Recovery: Store backups of critical data.
2. Media Storage: Store and stream media files (e.g., videos, images).
3. Static Website Hosting: Host static websites.
4. Data Analytics: Store and process large datasets.
5. Cloud-Native Applications: Store and retrieve data for cloud-native apps.

#### S3 Storage Classes:

1. S3 Standard: High availability and durability for frequently accessed data.
2. S3 Infrequent Access (IA): Lower cost for less frequently accessed data.
3. S3 One Zone-IA: Lower cost for data stored in a single Availability Zone.
4. S3 Glacier: Low-cost, long-term archival storage.
5. S3 Glacier Deep Archive: Lowest-cost, long-term archival storage.


#### S3 Security Features:

1. Data Encryption: Server-side encryption (SSE) and client-side encryption.

(`Server-Side Encryption` (SSE) is a feature in Amazon S3 that automatically encrypts data at rest, ensuring that only authorized users can access the encrypted data.)

(`Client-Side Encryption` (CSE) is a method where data is encrypted on the client-side (before uploading to S3), ensuring that data remains encrypted throughout its lifecycle.)

2. Access Controls: IAM policies, bucket policies, and ACLs.

(An `Access Control List` (ACL) is a list of permissions attached to an S3 object or bucket, defining which users or groups can access or modify it)

3. Versioning: Track changes to objects.

(`Versioning `is a feature in AWS S3 that allows you to store multiple versions of an object in a bucket. Each version is a unique copy of the object, and S3 maintains a history of all versions.)

4. Cross-Region Replication: Replicate data across regions.(CRR)

(`Cross-Region Replication` (CRR) is a feature in AWS S3 that automatically replicates objects from a source bucket in one AWS Region to a destination bucket in another AWS Region.)

#### S3 components :

`Buckets `: Buckets is a container that stores objects (files, data, etc.) 

1. Buckets contain  must be unique name across global
2. Buckets are region-specific.
3. Stores objects (up to 5 TB each).
4. Must be Define settings like versioning, replication, and lifecycle.
5. There is Unlimited Storage. 100 Buckets per an account

#### `Objects`: objects is known as Files/folders

1. An Objects are static files contain Meta-Data information. 
2. All objects are Private by default. 
3. When the object is in the bucket, you can open it, download it, and move it. 
4. Objects can: 
*   Be as small as 0 bytes and as large as 5Tb. 
* 	Be made publicly available via a URL. 


 `Bucket Settings `: Bucket settings is used to control various asspects of an s3 bucket

1. Versioning: Enable/disable versioning.
2. Replication: Configure cross-region replication.
3. Lifecycle: Define object lifecycle rules(moving files from one storage class to another storage class)

(An S3 `Lifecycle `configuration is a set of rules that define the lifecycle of objects in an S3 bucket. It enables automatic management of objects, reducing storage costs and simplifying data management.)

4. Access Control: Set bucket-level permissions.
5. Tags: Assign metadata tags.
6. Encryption.

`Replication:`Replication is a feature in AWS S3 that automatically copies objects from a source bucket to a destination bucket, ensuring data durability and availability.

#### Benefits:

1. Disaster Recovery: Protects against regional outages or disasters.
2. Compliance: Meets regulatory requirements for data redundancy.
3. Performance: Reduces latency for global users.
4. Data Availability: Ensures data availability across regions.

`Web hosting :`S3 Web Hosting allows you to host static websites directly from an S3 bucket, without the need for a separate web server

1. S3 buckets can be used to host static content (not dynamic) websites. 
2. Content can be HTML pages, images, videos, client-side scripts such as java scripts. 


* `Pre-assinged URL`: A pre-assigned URL, also known as a Presigned URL, is a temporary URL generated by AWS S3 that allows users to access or upload objects to a bucket without requiring AWS credentials.

Q: How will you automatically setup the transitioning of objects.?
A: using lifecycle rule.
