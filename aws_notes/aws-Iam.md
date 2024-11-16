### AWS IAM (Identity and Access Management) :

* IAM : AWS IAM is a web service that helps you manage access to AWS resources by creating and managing AWS users, groups, and roles.

* It provides fine-grained control over access to AWS resources, enabling you to specify what actions can be performed on which resources.

#### Key Features of AWS IAM :

1. Users: Create and manage AWS users, including passwords, access keys, and permissions.
2. Groups: Create and manage groups of users, making it easier to manage permissions.
3. Roles: Create and manage roles that define a set of permissions, allowing users or services to assume those roles.
4. Policies: Create and manage policies that define permissions for users, groups, and roles.
5. Multi-Factor Authentication (MFA): Add an extra layer of security to user accounts.
6. Access Keys: Manage access keys for users, including creation, rotation, and deletion.
7. Password Policies: Define password requirements and expiration policies.

#### Benefits of AWS IAM :

1.` Security:` Fine-grained control over access to AWS resources.

2. `Compliance:` Meet regulatory requirements for access control and auditing.
3. `Scalability:` Easily manage access for large numbers of users and resources.
4. `Flexibility:` Support for multiple identity providers and federation.
5. `Cost-Effective:` No additional costs for IAM, included with AWS account.

#### IAM Components :

* `IAM User:`

An IAM user is an entity that represents a person or application that interacts with AWS resources.

1. Each user has a unique username and password.
2. Users have permanent access keys and passwords.
3. Users can be creates its own Customizable Permissions assigned specific permissions and policies.

* `IAM Role`:

An IAM role is an entity that defines a set of permissions.

1.  Roles are assumed for a specific duration.
2.  Roles don't have long-term access keys or passwords.
3.  Roles can be reassigned or removed as needed.
4. Roles reduce the risk of credential compromise.

##### Common Use Cases:

1. EC2 Instances: Grant instances access to resources without storing credentials.
2. Lambda Functions: Allow functions to interact with resources without credentials.
3. Cross-Account Access: Enable access to resources across multiple AWS accounts.

##### Benefits:

1. Improved Security: Reduce credential risk.
2. Simplified Access: Easily manage access to resources.
3. Flexibility: Adapt to changing access requirements.

`IAM Group:`

An IAM group is a collection of IAM users that share common permissions and policies.
 1. Manage permissions for multiple users at once.
 2. Assign policies to groups, not individual users
 3. Users can be added or removed from groups as needed.

##### Benefits:

1. Easy Permission Management: Simplify user permissions.
2. Reduced Administrative Burden: Manage fewer policies.
3. Improved Scalability: Easily add or remove users from groups.

##### Common Use Cases:

1. `Departmental Access:` Create groups for departments (e.g., IT, Marketing).
2. `Job Function Access:` Create groups for job functions (e.g., Developers, Admins).
3. `Project-Based Access:` Create groups for project teams.

##### IAM Group Features:

1.` Policy Attachment:` Attach policies to groups.

2. `User Membership:` Add or remove users from groups.
3. `Group Nesting:` Create groups within groups.
##### IAM Policy Types :

1. Managed Policies: Pre-defined policies provided by AWS.
2. Custom Policies: User-defined policies.
3. Inline Policies: Policies attached directly to users, groups, or roles.

##### IAM Best Practices :

1. Use Strong Passwords: Enforce strong password policies.
2. Enable MFA: Require multi-factor authentication.
3. Rotate Access Keys: Regularly rotate access keys.
4. Use Least Privilege: Grant minimum necessary permissions.
5. Monitor Activity: Regularly review IAM activity logs.

##### IAM Troubleshooting :

1. Access Denied: Verify permissions and policies.
2. Invalid Credentials: Check access keys and passwords.
3. Policy Conflicts: Resolve policy conflicts.
-----
1. Q: What is the difference between IAM roles and users?
A: Roles define a set of permissions, while users are entities that interact with AWS resources.
2. Q: Can I use IAM with other AWS services?
A: Yes, IAM integrates with most AWS services.
3. Q: How do I manage IAM policies?
A: Use the AWS Management Console, AWS CLI, or SDKs.
4. Who need iam..?
A: all employees, users and contractors associated with the organization's infrastructure
----

##### AWS IAM Pricing :
 
IAM is included with your AWS account, and there are no additional costs for using the service.

 #### Creating user :
* Go to IAM-dashboard
  - create user - Name
  - provide user access to console(optional)
      - create an iam user
      - custom password-next
  - permissions policy(give as per requirement)   
  - copy a new user console paswd.
(user can modify it's own Policies)
c
* we can caluclate aws billings through `aws pricing caluclator`-Browser

 * account id is same user and admin billing should be added into admin id.

#### creating Groups
 - create Groups - Name
   - add user
   - attach permissions
                - create
 * one user can be a part of multiple groups

1-In one aws account how many users can create..?
Ans : 300 groups and 5000 users.
 * create roles and attach policys            


