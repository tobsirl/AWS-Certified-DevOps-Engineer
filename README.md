# AWS-Certified-DevOps-Engineer

## IAM, ACCOUNTS & ORGANIZATIONS

### IAM Identity Policies

IAM Identity Policies are JSON documents that define permissions for an IAM principal (user or role). They are attached to IAM principals and define what the principal can and cannot do. They are evaluated when a principal makes a request to AWS.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Stmt1234567890",
      "Effect": "Allow",
      "Action": ["s3:ListAllMyBuckets", "s3:GetBucketLocation"],
      "Resource": "*"
    }
  ]
}
```

#### IAM Identity Policy Elements

- Version: The version of the policy language. This is always 2012-10-17.
- Statement: The main element of the policy. It is an array of one or more individual statements.
- Sid: A statement identifier. This is an optional field that you can use to identify the statement.
- Effect: The effect of the statement. This can be either Allow or Deny.
- Principal: The principal to which this policy applies. This is optional and when not specified, the policy applies to the user or role that the policy is attached to.
- Action: The action or actions that this policy allows or denies. This is an array of one or more actions.
- Resource: The resource or resources that the statement covers. This is an array of one or more resources.
- Condition: Conditions that must be met for the statement to be in effect. This is an optional field.
- Policy Variables: Variables that you can use in your policy. This is an optional field.
- Policy Types: Types of policies that you can create. This is an optional field.
- Policy Evaluation Logic: How policies are evaluated. This is an optional field.
- Policy Evaluation: How policies are evaluated. This is an optional field.

#### IAM Identity Policy Evaluation

- Identity-based policies are evaluated when a principal (user or role) makes a request to AWS.
- Resource-based policies are evaluated when a request is made to the resource that the policy is attached to.

1. If there is an explicit deny in any of the policies, the request is denied.
2. If there is an explicit allow in any of the policies, the request is allowed.
3. If there is no explicit allow or deny, the request is denied.

- Policies are evaluated in the following order:
  - Identity-based policies
  - Resource-based policies
  - SCPs
  - Session policies
  - ACLs
  - Organizations service control policies (SCPs)

#### IAM Identity Policy Types

##### AWS Managed Policies

AWS managed policies are standalone identity-based policies that are created and managed by AWS. They are designed to be widely useful for many scenarios and are maintained by AWS. When you use an AWS managed policy, you can be sure that the policy is up-to-date and allows access to the specified AWS services and resources.

- Reusable
- Low Management Overhead
- Maintained by AWS

##### Customer Managed Policies

Customer managed policies are standalone identity-based policies that are created and managed by you. You have full control over these policies and can attach them to multiple users, groups, and roles within your AWS account. You can also choose to share your customer managed policies across accounts.

- Reusable
- Managed by you
- Shared across accounts
- Version controlled

##### Inline Policies

Inline policies are identity-based policies that are embedded directly into a single user, group, or role. Inline policies are useful for granting permissions to perform a specific task for a user, group, or role. An inline policy exists only as long as the user, group, or role exists.

- Reusable
- Managed by you
- Embedded directly into a single user, group, or role
- Special or Exceptional Allow or Deny

### IAM Users

IAM users are entities that you create in AWS to represent the people and services that you work with. You use IAM users to control authentication (sign-in) and authorization (permissions) to AWS resources in your account. IAM users can be grouped together into IAM groups and roles, and these IAM principals can be assigned permissions to create a logical grouping of users.

IAM User are an identity used for anything requiring long-term access to AWS resources. e.g. a person, an application, or a service.

#### Principal

Person or application that can make a request to IAM to perform and action or obtain information.

IAM users are required to authenticate with AWS before they can make requests to AWS services. Authentication is performed by signing in with a username and password or by using access keys.

Authenticated Identity: IAM User, IAM Role, AWS Account Root User, Federated User

Once authenticated, the user is authorized to perform actions and obtain information based on the permissions that are attached to the IAM user.

IAM checks to see if the authenticated principal is authorized to perform the requested action or obtain the requested information. Authorization is performed by evaluating the policies that are attached to the IAM user.

#### Amazon Resource Name (ARN)

Amazon Resource Names (ARNs) uniquely identify AWS resources. We require an ARN when you need to specify a resource unambiguously across all of AWS, such as in IAM policies, Amazon Relational Database Service (Amazon RDS) tags, and API calls.

An ARN is a unique identifier for an AWS resource. It is a string of characters that follow a specific format. The format of an ARN is:

```bash
arn:partition:service:region:account-id:resource-id
arn:partition:service:region:account-id:resource-type/resource-id
arn:partition:service:region:account-id:resource-type:resource-id

arn:aws:s3:::pictures # S3 Bucket no need to specify region or account-id due to global namespace
arn:aws:s3:::pictures/* # all objects in the S3 Bucket
```

#### IAM User limits

- 5000 IAM Users per AWS Account
- IAM User can be a member of up to 10 groups
- Internet-scale applications
- Large organizations
- IAM Roles & IAM Federation can fix this

### IAM Groups

IAM groups are a collection of IAM users. Groups let you specify permissions for multiple users, which can make it easier to manage the permissions for those users. For example, you could have a group called Admins and give that group the types of permissions that administrators typically need. Any user in that group automatically has the permissions that are assigned to the group. If a new user joins your organization and needs administrator privileges, you can assign the appropriate permissions by adding the user to that group. Similarly, if a person changes jobs in your organization, instead of editing that user's permissions, you can remove him or her from the old groups and add him or her to the appropriate new groups.

#### IAM Group Limits

- No nested groups
- 300 groups per AWS Account
- Groups are _not_ a _true identity_. They can't be referenced as a _principal_ in a policy

### IAM Roles

IAM roles are a secure way to grant permissions to entities that you trust. Examples of entities include the following:

- IAM user in another account
- Application code running on an EC2 instance that needs to perform actions on AWS resources
- An AWS service that needs to act on resources in your account to provide its features
- Users from a corporate directory who use identity federation with SAML
- IAM roles issue keys that are valid for short durations, making them a more secure way to grant access.
- IAM roles do not have any credentials (password or access keys) associated with them.
- Instead, IAM roles have a trust policy that specifies who can assume the role.
- IAM roles are not associated with a specific user or group.
- Instead, trusted entities assume roles, such as IAM users, applications, or AWS services such as EC2.
- IAM roles can be used to delegate access within your account or between accounts you own.
- IAM roles can be used to delegate access to services that do not normally support IAM users, such as Amazon EC2.
- IAM roles can be used to delegate access to services that you do not own.
- IAM roles can be used to delegate access to services outside of AWS.

#### IAM Role Types

IAM Roles have two types of policies attached to them:

- Trust Policy: Specifies who can assume the role
  IAM Roles have a Trust Policy that specifies who can assume the role. The Trust Policy is a JSON document that defines the trusted entities that are allowed to assume the role. The Trust Policy is attached to the role and is evaluated when a principal attempts to assume the role.
  Which identities can assume the role?

- Permissions Policy: Specifies what the role can do
  IAM Roles have a Permissions Policy that specifies what the role can do. The Permissions Policy is a JSON document that defines the permissions that are allowed or denied when the role is assumed. The Permissions Policy is attached to the role and is evaluated when a principal attempts to assume the role.

#### Temporary Security Credentials

IAM roles issue temporary security credentials that are valid for a specified duration. These credentials are generated dynamically and provided to the user or application that assumes the role. The user or application can then use the temporary security credentials to make requests to AWS resources.

##### sts:AssumeRole

sts:AssumeRole is an AWS Security Token Service (AWS STS) API operation that grants an IAM user permission to assume a role. The IAM user must have permission to call the sts:AssumeRole API operation and the role must have a trust policy that allows the IAM user to assume the role.

### Service-Linked Roles

Service-linked roles are predefined IAM roles that are used by AWS services to enable integration with other AWS services. Each service-linked role delegates permissions to an AWS service so that the service can access resources in another service on your behalf.

Service-linked roles are predefined by the service and include all the permissions that the service requires to call other AWS services on your behalf.

A service-linked role makes setting up an integration between two AWS services easier because you don't have to manually add the necessary permissions. AWS creates a service-linked role only when you create a resource that requires a service-linked role to manage your resource on your behalf.

example:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "iam:CreateServiceLinkedRole",
      "Resource": "arn:aws:iam::*:role/aws-service-role/SERVICE-NAME.amazonaws.com/SERVICE-LINKED-ROLE-NAME-PREFIX*",
      "Condition": {
        "StringLike": { "iam:AWSServiceName": "SERVICE-NAME.amazonaws.com" }
      }
    },
    {
      "Effect": "Allow",
      "Action": ["iam:AttachRolePolicy", "iam:PutRolePolicy"],
      "Resource": "arn:aws:iam::*:role/aws-service-role/SERVICE-NAME.amazonaws.com/SERVICE-LINKED-ROLE-NAME-PREFIX*"
    }
  ]
}
```

#### Service-Linked Role Pass Role

Some services require you to pass a service-linked role to the service. This is because the service must delegate permissions to the service-linked role to access resources on your behalf. When you pass a service-linked role to a service, the service can assume the service-linked role only if the service-linked role has a trust policy that allows the service to assume the role.

example:

```json
{
  "Sid": "PolicyStatementToAllowUserToListRoles",
  "Effect": "Allow",
  "Action": ["iam:ListRoles"],
  "Resource": "*"
},
{
  "Sid": "PolicyStatementToAllowUserToPassOneSpecificRole",
  "Effect": "Allow",
  "Action": [ "iam:PassRole" ],
  "Resource": "arn:aws:iam::account-id:role/my-role-for-XYZ"
}
```

### AWS Organizations

AWS Organizations is an account management service that enables you to consolidate multiple AWS accounts into an organization that you create and centrally manage. AWS Organizations includes account management and consolidated billing capabilities that enable you to better meet the budgetary, security, and compliance needs of your business.

As an administrator of an organization, you can create accounts in your organization and invite existing accounts to join the organization. You can organize those accounts into groups and attach policy-based controls. You can apply policies across your organization to control access to AWS services, resources, and regions, and you can automate the creation of new accounts for your organization.

#### AWS Organizations Terminology

- Organization: An organization is a collection of AWS accounts that you have consolidated into a single bill. You can create an organization by inviting existing AWS accounts to join your organization, or by creating new accounts in your organization.
- Organizational unit (OU): An organizational unit (OU) is a group of AWS accounts within an organization. You can use OUs to group accounts together to more easily manage your AWS resources. You can create OUs and add accounts to them.
- Service control policy (SCP): A service control policy (SCP) is a type of policy that you can use to manage permissions in your organization. SCPs offer central control over the maximum available permissions for all accounts in your organization. SCPs are available only in organizations that have all features enabled.
- Management account: A management account is the AWS account that you use to create an organization. The management account is automatically created when you create an organization. The management account has full permissions to all AWS services and resources in the organization. You can use the management account to create OUs, invite accounts to join the organization, and apply policies to OUs or accounts.
- Member account: A member account is an AWS account that is part of an organization. Member accounts are invited to join an organization by the management account. Member accounts can be moved to different OUs, and policies can be applied to them.
- Organization Root: The root is the email address and password that you use to sign in to the management account. The root user has full permissions to all AWS services and resources in the organization. You can use the root user to create OUs, invite accounts to join the organization, and apply policies to OUs or accounts.
