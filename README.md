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

Service-

- Modular roles are predefined IAM roles that are used by AWS services to enable integration with other AWS services. Each service-linked role delegates permissions to an AWS service so that the service can access resources in another service on your behalf.

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

#### AWS Organizations Consolidated Billing

Consolidated billing enables you to consolidate payment for multiple AWS accounts or multiple Amazon Internet Services Pvt. Ltd (AISPL) accounts within your organization by designating a single account to pay for all charges. Consolidated billing is offered at no additional charge.

Consolidation of reservations and volume discounts

### Service Control Policies

Service control policies (SCPs) are a type of organization policy that you can use to manage permissions in your organization. SCPs offer central control over the maximum available permissions for all accounts in your organization. SCPs are available only in organizations that have all features enabled.

Service control policies can be attached to the root, organizational units (OUs), and accounts. SCPs are applied in the following order:

- SCPs that are attached to the root of the organization
- SCPs that are attached to an OU
- SCPs that are attached to an account

- SCPs are account permissions boundaries
- SCPs limit what the account (including the account root user) can do
- SCPs do not grant permissions
- SCPs determine what permissions are available to the account

#### SCPs Allow list vs Deny list

- SCPs default to FullAWSAccess
- SCPs therefore must deny access to services

Using an allow list is the recommended approach for using SCPs. An allow list is a list of services, actions, or resources that are allowed. All other services, actions, or resources are denied. Using an allow list is more secure because it is easier to maintain and less likely to be misconfigured.

First step is to remove FullAWSAccess

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "DenyFullAWSAccess",
      "Effect": "Deny",
      "Action": "iam:*",
      "Resource": "*"
    }
  ]
}
```

Second step is to allow only the services you need

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowEC2AndS3",
      "Effect": "Allow",
      "Action": ["ec2:*", "s3:*"],
      "Resource": "*"
    }
  ]
}
```

## CloudFormation

AWS CloudFormation provides a common language for you to describe and provision all the infrastructure resources in your cloud environment. CloudFormation allows you to use a simple text file to model and provision, in an automated and secure manner, all the resources needed for your applications across all regions and accounts. This file serves as the single source of truth for your cloud environment. CloudFormation provisions your resources in a safe, repeatable manner, allowing you to build and rebuild your infrastructure and applications, without having to perform manual actions or write custom scripts.

Physical Resources: AWS resources that are created and managed by CloudFormation. e.g. EC2 Instance, S3 Bucket, RDS Database
Logical Resources: Resources that are part of the CloudFormation template. e.g. EC2 Instance, S3 Bucket, RDS Database

### CloudFormation Template

A CloudFormation template is a JSON or YAML formatted text file that describes your AWS infrastructure. The template contains sections that describe the AWS resources that you want to create and configure. You can also use the template to specify values for template parameters, to pass values between resources, and to output values.

Contains logical resources - the "WHAT"

Templates are used to create Stacks

1 stack, 100 stacks, 20.. stacks in each region

stacks create physical resources from the logical resources in the template

If a stacks template is changed, physical resources are changed

If a stack is deleted, normally, the physical resources are deleted

### CloudFormation Template Anatomy

- AWSTemplateFormatVersion
- Description
- Metadata
- Parameters
- Mappings
- Conditions
- Transform
- Resources
- Outputs

Example of a CloudFormation Template

```yaml
Resources:
  MyEC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      ImageId: ami-0ff8a91507f77f867
      InstanceType: t2.micro
      KeyName: mykey
      SecurityGroupIds:
        - sg-78a54011
      SubnetId: subnet-0e5dce72
```

### Template Parameters and Pseudo Parameters

Template parameters are used to pass values into a template at runtime. Parameters enable you to input custom values to your template each time you create or update a stack. Parameters are important for reusability, because they enable you to customize your templates for various environments.

- Template parameters accept input - console, API, CLI
- when a stack is created or updated
- Can be referenced from whithin logical resources
- influence physical resources and/or configuration
- Can be configured with Default, AllowedValues, MaxLength, MinLength, MaxValue, MinValue, NoEcho, Description, ConstraintDescription

Example of a Template Parameter

```yaml
Parameters:
  InstanceType:
    Description: EC2 instance type
    Type: String
    Default: t2.micro
    AllowedValues:
      - t2.micro
      - t2.small
      - t2.medium
    ConstraintDescription: must be a valid EC2 instance type.
```

Example of a Pseudo Parameter

```yaml
!Ref MyEC2Instance
!Ref AWS::Region
!Ref AWS::StackName
!Ref AWS::StackId
!Ref AWS::AccountId
!Ref AWS::NotificationARNs
!Ref AWS::NoValue
!Ref AWS::Partition
!Ref AWS::URLSuffix
```

### Cloudformation Intrinsic Functions

Intrinsic functions enable you to assign values to properties that are not available until runtime. You can use intrinsic functions for built-in functions, such as conditionals, and for creating your own functions. You can also use intrinsic functions to insert values into a stack from elsewhere in the template.

- Ref: Returns the value of the specified parameter or resource.
- Fn::GetAtt: Returns the value of an attribute from a resource in the template.
- Fn::Join: Appends a set of values into a single value, separated by the specified delimiter.
- Fn::Split: Splits a string into a list of string values so that you can select an element from the resulting string list.
- Fn::GetAZs: Returns an array that lists Availability Zones for a specified region.
- Fn::Select: Returns a single object from a list of objects by index.
- Condition Functions: Returns one value if the specified condition evaluates to true and another value if the specified condition evaluates to false.
- Fn::Base64: Returns the Base64 representation of the input string.
- Fn::Sub: Substitutes variables in an input string with values that you specify.
- Fn::Cidr: Returns an array of CIDR address blocks.

### CloudFormation Mappings

Mappings are a set of key-value pairs that you can use to specify conditional parameter values, similar to a lookup table. You can match a key to a corresponding value by using the Fn::FindInMap intrinsic function in the Resources and Outputs section.

- Templates can contain Mappings object
- which can contain many mappings
- which map keys to values, allowing lookup
- Can have one key, or Top & Second level keys
- Mappings use !FindInMap intrinsic function
- Common use ... retrieve AMI for a given region & architecture
- Improve Template Portability

Example of a Mapping

```yaml
Mappings:
  RegionMap:
    us-east-1:
      "32": "ami-6411e20d"
      "64": "ami-7a11e213"
    us-west-1:
      "32": "ami-c9c7978c"
      "64": "ami-cfc7978a"
    eu-west-1:
      "32": "ami-37c2f643"
      "64": "ami-31c2f645"
    ap-southeast-1:
      "32": "ami-66f28c34"
      "64": "ami-60f28c32"
    ap-northeast-1:
      "32": "ami-9c03a89d"
      "64": "ami-a003a8a1"
```

Example of FindInMap

```yaml
!FindInMap [MapName, TopLevelKey, SecondLevelKey]

!FindInMap [RegionMap, !Ref "AWS::Region", 32]
```

### CloudFormation Outputs

Outputs are optional and can be used to export values from the stack to make them available for other stacks to import. For example, you can output the Amazon S3 bucket name for a stack, and then use the Name attribute of the AWS::S3::Bucket resource in another stack by using the { "Fn::ImportValue" : "stack-output-name" } function.

- Templates can have an _optional_ Outputs section
- Values can be declared in this section
- visible as outputs when using the CLI
- visible as outputs in the console UI
- accessible from a parent stack when using nesting
- Can be exported, allowing cross-stack references

Example of an Output

```yaml
Outputs:
  WordPressURL:
    Description: "Instance Web Url"
    Value: !Join ["", ["http://", !GetAtt EC2Instance.PublicDnsName]]
```

### CloudFormation Conditions

Conditions are optional and can be used to control whether certain resources are created or whether certain resource properties are assigned a value during stack creation or update. For example, you can conditionally create a resource based on the environment to which the stack is being deployed.

- Created in the optional Conditions section of a template
- Conditions are evaluated to True or False
- processed before resources are created
- Use the other intrinsic functions AND, OR, NOT, IF, EQUALS
- associated with logical resources to control if they are created or not
- e.g. ONEAZ, TWOAZ, THREEAZ - how many AZs to create resources in
- e.g. PROD, TEST, DEV - what environment to create resources in

Example of a Condition

```yaml
Parameters:
  Environment:
    Description: "Environment"
    Type: String
    Default: "PROD"
    AllowedValues:
      - PROD
      - TEST
      - DEV
    ConstraintDescription: "must specify PROD, TEST, or DEV."
```

```yaml
Conditions:
  CreateProdResources: !Equals [!Ref Environment, "PROD"]
  CreateTestResources: !Equals [!Ref Environment, "TEST"]
  CreateDevResources: !Equals [!Ref Environment, "DEV"]
```

```yaml
Resources:
  MyEC2Instance:
    Type: AWS::EC2::Instance
    Condition: CreateProdResources
    Properties:
      ImageId: ami-0ff8a91507f77f867
      InstanceType: t2.micro
      KeyName: mykey
      SecurityGroupIds:
        - sg-78a54011
      SubnetId: subnet-0e5dce72
```

### CloudFormation DependsOn

The DependsOn attribute is used to specify that the creation of a specific resource follows another. When you add a DependsOn attribute to a resource, that resource is created only after the creation of the resource specified in the DependsOn attribute.

- CloudFormation tries to be efficient
- It will create resources in **parallel** if it can (create, update, delete)
- tries to determine a **dependency order** (VPC -> Subnet -> EC2)
- **reference** or **function** create these
- DependsOn lets you _explicitly_ define these dependencies
- if Resource B and C depends on Resource A, then Resource A is created first
- both wait for A to complete before starting

Example of DependsOn a VPC and Internet Gateway

```yaml
Resources:
  VPC:
    Type: AWS::EC2::VPC
    Properties:
      CidrBlock: 10.16.0.0/16
      EnableDnsSupport: true
      EnableDnsHostnames: true
      Tags:
        - Key: Name
          Value: a4l-vpc1
```

```yaml
InternetGateway:
  Type: AWS::EC2::InternetGateway
  Properties:
    Tags:
      - Key: Name
        Value: a4l-vpc1-igw1
```

```yaml
InternetGatewayAttachment:
  Type: AWS::EC2::VPCGatewayAttachment
  Properties:
    VpcId: !Ref VPC
    InternetGatewayId: !Ref InternetGateway
```

An Elastic IP requires an Internet Gateway attached to a VPC in order to work ... but there is no dependency in the template - implicit
(e.g. !Ref) or explicit (e.g. DependsOn)

```yaml
EIP:
  Type: AWS::EC2::EIP
  Properties:
    Domain: vpc
  DependsOn: InternetGatewayAttachment
```

### CloudFormation WaitConditions, CreationPolicy, and cfn-signal

CreationPolicy, WaitConditions and cfn-signal can all be used together to prevent the status if a resource from reaching create complete until AWS CloudFormation receives a specified number of success signals or the timeout period is exceeded.The cfn-signal helper script signals AWS CloudFormation to indicate whether Amazon EC2 instances have been successfully created or updated.

#### CloudFormation Provisioning

- Logical resources in the **template**
- Used to create a **Stack**
- creates **physical resources** in AWS
- Logical resource CREATE_COMPLETE does not mean physical resource is ready

#### CloudFormation Signal

- Configure CloudFormation to hold
- Wait for X number of success signals
- Wait for Timeout H:M:S for those signals (12 hour max)
- If success signals received, then CREATE_COMPLETE
- If failure signal received, creation fails
- If timeout is reached creation fails
- CreationPolicy or WaitCondition

#### CloudFormation CreationPolicy

- CreationPolicy is used to prevent the status of a resource from reaching create complete until AWS CloudFormation receives a specified number of success signals or the timeout period is exceeded.
- CreationPolicy is used with the WaitCondition and cfn-signal helper script to signal AWS CloudFormation to indicate whether Amazon EC2 instances have been successfully created or updated.
- CreationPolicy is used to prevent the status of a resource from reaching create complete until AWS CloudFormation receives a specified number of success signals or the timeout period is exceeded.

Example of a CreationPolicy

```yaml
AutoScalingGroup:
  Type: "AWS::AutoScaling::AutoScalingGroup"
  CreationPolicy:
    ResourceSignal:
      Count: "1"
      Timeout: "PT15M"
  Properties:
    AvailabilityZones:
      - us-east-1a
      - us-east-1b
    LaunchConfigurationName: !Ref LaunchConfig
    MinSize: "1"
    MaxSize: "5"
    DesiredCapacity: "3"
  CreationPolicy:
    ResourceSignal:
      Count: "3"
      Timeout: "PT15M"
```

LaunchConfigue

```yaml
LaunchConfig:
  Type: "AWS::AutoScaling::LaunchConfiguration"
  Properties:
    ImageId: "ami-0ff8a91507f77f867"
    InstanceType: "t2.micro"
    UserData:
      Fn::Base64: !Sub |
        #!/bin/bash -xe
        yum update -y aws-cfn-bootstrap
        /opt/aws/bin/cfn-init -v 
        --stack ${AWS::StackName} 
        --resource LaunchConfig 
        --region ${AWS::Region}
```

#### CloudFormation WaitCondition

- WaitCondition is used to block the creation of a resource until a specified condition is met.
- WaitCondition can be used to block the creation of a resource until a specified condition is met. For example, you can use a WaitCondition to block the creation of an Amazon EC2 instance until the instance has been configured and is ready to use.
- WaitCondition can depend on other resources. Other resources can depend on the WaitCondition.

Example of a WaitCondition

```yaml
Resources:
  WaitHandle:
    Type: "AWS::CloudFormation::WaitConditionHandle"
  WaitCondition:
    Type: "AWS::CloudFormation::WaitCondition"
    DependsOn: "WebServer"
    Properties:
      Handle: !Ref WaitHandle
      Timeout: "300"
```

Generates a Presigned URL for resources signals

```yaml
WaitHandle:
  Type: "AWS::CloudFormation::WaitConditionHandle"
```

JSON passed back in signal response

```json
{
  "Status": "SUCCESS",
  "Reason": "Configuration Complete",
  "UniqueId": "MyEC2Instance",
  "Data": "Configuration Complete"
}
```

Accessible via Fn::GetAtt on the WaitCondition

```json
{
  "Signal1": "Some amazing thing has happened"
}
```

### CloudFormation Nested Stacks

Nested stacks allow for a hierarchy of related templates to be combined to form a single product
A root stack can contain and create nested stacks .. each of which can be passed parameters and provide back outputs.
Nested stacks should be used when the resources being provisioned share a lifecycle and are related.
Resources in a single stack should **share a lifecycle** and be related.

- Nested stacks are a way to create a hierarchy of stacks
- A root stack can contain and create nested stacks
- Nested stacks can be passed parameters
- Nested stacks can provide outputs
- Nested stacks should be used when the resources being provisioned share a lifecycle and are related

Limitations

- Stack resource limits (500)
- Can't easily **reuse** resources e.g. VPC

Example of a Stack

```yaml
VPCStack:
  Type: "AWS::CloudFormation::Stack"
  Properties:
    TemplateURL: "https://s3.amazonaws.com/mybucket/vpc.template"
    TimeoutInMinutes: "60"
    Parameters:
      Param1: !Ref "AWS::Region"
      Param2: !Ref "AWS::AccountId"
      Param3: !Ref "SomeParameter"
```

Parameters must be passed to the nested stack

```yaml
Parameters:
  Param1:
    Description: "Region"
    Type: "String"
  Param2:
    Description: "Account ID"
    Type: "String"
  Param3:
    Description: "Some Parameter"
    Type: "String"
```

VPCStack.Outputs.VPCID

```yaml
Outputs:
  VPCID:
    Description: "VPC ID"
    Value: !GetAtt VPCStack.Outputs.VPCID
```

ADSTACK that DependsOn VPCStack

```yaml
ADStack:
  Type: "AWS::CloudFormation::Stack"
  DependsOn: VPCStack
  Properties:
    TemplateURL: "https://s3.amazonaws.com/mybucket/ad.template"
    TimeoutInMinutes: "60"
    Parameters:
      VPCID: !GetAtt VPCStack.Outputs.VPCID
```

APPSTACK that DependsOn VPCStack and ADStack

```yaml
AppStack:
  Type: "AWS::CloudFormation::Stack"
  DependsOn:
    - VPCStack
    - ADStack
  Properties:
    TemplateURL: "https://s3.amazonaws.com/mybucket/app.template"
    TimeoutInMinutes: "60"
    Parameters:
      VPCID: !GetAtt VPCStack.Outputs.VPCID
      ADID: !GetAtt ADStack.Outputs.ADID
```

### Difference between Nested Stacks and Cross-Stack References

#### Nested Stacks

- Nested Stacks: A nested stack is a stack that is created as a resource within a root stack. You can use nested stacks to create a reusable template that you can use to create common sets of resources. You can also use nested stacks to create a hierarchy of stacks that are managed as a single unit. Nested stacks are useful when you want to reuse a template that represents a set of resources that are used in multiple applications or environments. Nested stacks are also useful when you want to create a hierarchy of stacks that are managed as a single unit.
  - Nested Stacks reuses the template, not the resources
  - Used when the stacks form part of a single solution - lifecycle linked
  - Modular and reusable
  - Overcome the 500 resource limit of one stack
  - Modular templates ...code reuse
  - Make the installation process easier
  - nested stacks created by the root stack
  - Use only when everything is lifecycle linked

#### Cross-Stack References

- Cross-Stack References: A cross-stack reference is a way to export values from one stack and use them in another stack. You can use cross-stack references to create a dependency between two stacks. For example, you can use a cross-stack reference to create a dependency between a stack that contains a VPC and a stack that contains an EC2 instance. Cross-stack references are useful when you want to create a dependency between two stacks.
  - Cross-Stack References reuses the resources, not the template
  - Cross stack references allow one stack to reference another
  - Outputs in one stack reference logical resources or attributes in that stack
  - They can be exported, and then using the `!ImportValue` intrinsic function, referenced from another stack.
  - CloudFormation stacks are designed to be isolated and self-contained
  - Outputs are normally **not visible** to other stacks
  - Nested stacks can reference them
  - Outputs can be **exported** making them visiable to other stacks
  - Exports must have a **unique name** within the region
  - `Fn::ImportValue` can be used to reference the exported value, this is used instead of !Ref

Example of a Cross-Stack Reference shared VPC

```yaml
Outputs:
  SHAREDVPCID:
    Description: "Shared Services VPC"
    Value: !Ref VPC
    Export:
      Name: "SHAREDVPCID"
```

Export is used to export the output of a stack ... to a unique name in that region of that account
`ImportValue` can be used to reference the exported value, this is used instead of !Ref

```yaml
VPCID:
  Type: "String"
  Description: "VPC ID"
  Value: !ImportValue "SHAREDVPCID"
```

### CloudFormation StackSets

AWS CloudFormation StackSets extends the functionality of stacks by enabling you to create, update, or delete stacks across multiple accounts and regions with a single operation. StackSets are useful when you want to create, update, or delete stacks across multiple accounts and regions. StackSets are useful when you want to create, update, or delete stacks across multiple accounts and regions.

StackSets are a feature of CloudFormation allowing infrastructure to be deployed and managed across multiple regions and multiple accounts from a single location.

Additionally it adds a dynamic architecture - allowing automatic operations based on accounts being added or removed from the scope of a StackSet.

- Deploy CFN stacks across **many accounts** and **regions**
- StackSets are **container** in an admin account
- ...conain **stack instances** ..which **reference stacks**
- **Stack instances** and **stacks** are in **target accounts**
- Each stack = 1 region in 1 account
- ⚠️ Security = self-managed or service-managed

#### CFN StackSets - Terms

- StackSet: A container for stack instances
- StackInstance: A reference to a stack in a target account and region
- Stack: A collection of resources that are created, updated, or deleted together
- Concurrent Accounts: The number of accounts in which stack operations can occur at the same time
- Failure Tolerance: The number of accounts for which stack operations can fail before the stack set operation stops
- Retain Stacks: Whether to retain stacks in accounts when they are removed from a stack set

### CloudFormation DeletionPolicy

DeletionPolicy is an optional attribute that you can use with AWS CloudFormation resources. You can use DeletionPolicy to specify how AWS CloudFormation handles the deletion of a resource when a stack is deleted. You can use DeletionPolicy to specify how AWS CloudFormation handles the deletion of a resource when a stack is deleted. You can use DeletionPolicy to specify how AWS CloudFormation handles the deletion of a resource when a stack is deleted.

With the DeletionPolicy attribute you can preserve or (in some cases) backup a resource when its stack is deleted. You specify a DeletionPolicy attribute for each resource that you want to control. If a resource has no DeletionPolicy attribute, AWS CloudFormation deletes the resource by default.

- If you delete a logical resource from a template
- by default, the physical resource is also deleted
- This can cause data loss
- With deletion policy, you can define on each resource
- ...Delete (default), Retain or (if supported) Snapshot
- EBS Volumes, ElastiCache Clusters, RDS Databases, Neptune, Redshift
- Snapshots continue on past Stack lifetime - you have to clean up manually
- ONLY APPLIES TO DELETE STACKS ... NOT REPLACE

#### Delete

The Default process is that when logical resources are removed (individually or via stack delete) the physical resources are also deleted

#### Retain

The Retain process is that when logical resources are removed (individually or via stack delete) the physical resources are retained
Physical resources remain untouched when the Stacks logical resources are removed

#### Snapshot

The Snapshot process is that when logical resources are removed (individually or via stack delete) the physical resources are snapshotted
Physical resources are snapshotted when the Stacks logical resources are removed
Not supported for EC2

### CloudFormation Stack Roles

- Stack Roles: A stack role is an AWS Identity and Access Management (IAM) role that is used to create, update, or delete a stack. You can use a stack role to specify the permissions that are required to create, update, or delete a stack.
- Stack roles allow an IAM role to be passed into the stack via PassRole
- A stack uses this role, rather than the identity interacting with the stack to create, update and delete AWS resources.
- ⚠️ It allows role separation and is a powerful security feature.
- When you create a stack - CFN creates physical resources
- CFN uses the **permissions** of the **logged in identity**
- Which means **you need permissions for AWS**
- CFN can **assume a role** to gain the permissions it needs
- This lets you implement **role separation**
- The identity creating the stack **does not need permissions** - only **PassRole**

### CloudFormation CFN-Init

CloudFormationInit and cfn-init are tools which allow a desired state configuration management system to be implemented within CloudFormation
Use the AWS::CloudFormation::Init type to include metadata on an Amazon EC2 instance for the cfn-init helper script. If your template calls the cfn-init script, the script looks for resource metadata rooted in the AWS::CloudFormation::Init metadata key. cfn-init supports all metadata types for Linux systems & It supports some metadata types for Windows

- Simple configuration management system
- Configuration **directives** are stored in the template
- AWS::CloudFormation::Init part of logical resource
- Procedural - HOW (user data)
- ...vs Desired State - WHAT (cfn-init)
- cfn-init helper script - installed on EC2 OS image

Example of a cfn-init

```yaml
Resources:
  MyEC2Instance:
    Type: "AWS::EC2::Instance"
    Metadata:
      AWS::CloudFormation::Init:
        config:
          packages:
            yum:
              httpd: []
          files:
            /var/www/html/index.html:
              content: !Sub |
                <html>
                <body>
                <h1>Hello, World</h1>
                </body>
                </html>
              mode: "000644"
              owner: "apache"
              group: "apache"
          services:
            sysvinit:
              httpd:
                enabled: "true"
                ensureRunning: "true"
```

Example of UserData

```yaml
UserData:
  Fn::Base64: !Sub |
    #!/bin/bash -xe
    yum update -y aws-cfn-bootstrap
    /opt/aws/bin/cfn-init -v 
    --stack ${AWS::StackName} 
    --resource MyEC2Instance 
    --region ${AWS::Region}
```

- packages: Install and upgrade packages
- groups: Create and manage user and group accounts
- users: Create and manage user and group accounts
- sources: Download and extract archives
- files: Create and manage files
- commands: Execute commands
- services: Manage services

### CloudFormation cfn-hup

cfn-hup is a daemon that detects changes in the metadata and runs user-specified hooks. You can use cfn-hup to detect changes in the metadata and run user-specified hooks.

The cfn-hup helper is a daemon that detects changes in resource metadata and runs user-specified actions when a change is detected. This allows you to make configuration updates on your running Amazon EC2 instances through the UpdateStack API action.

- cfn-init is run once as part of bootstrapping (user data)
- ...if CloudFromation::init is updated, cfn-init is not run again
- cfn-hup is a daemon that can be installed on an EC2 instance
- it detects changes in resource metadata
- running configurable actions when a change is detected
- UpdateStack -> updated config on EC2 instance

### CloudFormation Change Sets

A change set is a summary of the changes that AWS CloudFormation will make to a stack when you execute the change set. You can use a change set to understand the changes that will be made to a stack before you execute the change set.

When you need to update a stack, understanding how your changes will affect running resources before you implement them can help you update stacks with confidence. Change sets allow you to preview how proposed changes to a stack might impact your running resources, for example, whether your changes will delete or replace any critical resources, AWS CloudFormation makes the changes to your stack only when you decide to execute the change set, allowing you to decide whether to proceed with your proposed changes or explore other changes by creating another change set.

- Template => Stack => Physical Resources (Create)
- Stack (Delete) => (Delete) Physical Resources
- v2 Template => Existing Stack => Resources Change
- No Interruption, ⚠️ Some Interruption ⚠️, 🚨 Replacement 🚨
- Change Sets let you preview changes (A Change Set)
- ... multiple different versions (lots of change sets)
- Chosen changes can be applied by executing the change set

### CloudFormation Custom Resources

Custom resources enable you to write custom provisioning logic in templates that AWS CloudFormation runs anytime you create, update (if you changed the custom resource), or delete stacks. For example, you might want to include resources that aren't available as AWS CloudFormation resource types. You can include those resources by using custom resources.

Custom resources enable you to write custom provisioning logic in templates that AWS CloudFormation runs anytime you create, update (if you changed the custom resource), or delete stacks

- Logical Resources in a template - WHAT you want
- CFN uses them to CREATE, UPDATE, DELETE physical resources
- CloudFormation doesn't support everything
- Custom Resources lets CFN integrate with anything it doesn't yet, or doesn't naturally support
- Passes data to something, gets data back from something

## Elastic Beanstalk (EB)

Elastic Beanstalk is a Platform as a Service environment which can create and manage infrastructure for application code.

- Platform as a service (PaaS)
- Developer Focssed - not end user
- High level - Managed Application Environments
- User Provide code and EB handles the environment
- Focus on code, low infrastructure overhead
- Fully customisable - use AWS products under the covers
- Requires app changes ... doesn't come for free

### Elastic Beanstalk (EB) - Platforms

Types

- Built in languages
- Docker
- Custom platforms

Examples

- Go. Java SE, Tomcat
- .NET Core (Linux) & .NET (Windows)
- Node.js, PHP, Python and Ruby
- Single Container Docker & Multicontainer Docker
- Preconfigured Docker
- Custom via packer

Elastic Beanstalk Application - an application is a collection of things relating to an application - a container / folder
EB Application Versions - a specific labeled version of deployable code for an application. The source bundle is store on S3.
EB Environments - containers of infrastructure and configuration for a specific application version.
Each environment is either a web server tier or a worker tier. This controls the structure & function of the environment.

### Elastic Beanstalk (EB) - Deployment Options

AWS Elastic Beanstalk provides several options for how deployments are processed, including deployment policies (All at once, Rolling, Rolling with additional batch, Immutable, and Traffic splitting) and options that let you configure batch size and health check behavior during deployments

- All at once: Deploys the new version to all instances simultaneously. This results in a temporary outage while the deployment is in process.
- Rolling: Deploys the new version in batches. Each batch is taken out of service while the remaining batches continue to serve traffic. This reduces the impact on your application's availability during deployment.
- Rolling with additional batch: Similar to rolling, but adds capacity to the environment before the deployment and reduces capacity after the new version is deployed. This means that both the new and old versions of your application are running on the same environment at the same time.
- Immutable: Deploys the new version to a fresh group of instances in a separate environment, then swaps the fresh group of instances with the current group. This results in no downtime during the deployment.
- Traffic splitting: Deploys the new version to a separate fleet of instances and then gradually shifts traffic from the old to the new version. This results in no downtime during the deployment.
- Blue/Green: Deploys the new version to a separate environment, then swaps CNAMEs. This results in no downtime during the deployment.

### Elastic Beanstalk (EB) - Lifecycle and RDS

Elastic Beanstalk can create and manage an RDS database for you. It can also manage the lifecycle of the RDS database. This includes creating, updating, and deleting the RDS database.

Create RDS Database in EB Environment

- You can create and RDS instance within an EB environment
- It's then linked to the EB environment
- Delete the environment = delete RDS = data loss
- Different environments = different RDS = different data
- Environment Properties: RDS_DB_NAME, RDS_USERNAME, RDS_PASSWORD, RDS_HOSTNAME, RDS_PORT

Create RDS Database outside of EB Environment

- You can also create an RDS instance outside of an EB environment
- Add environment properties to point at RDS instance: RDS_HOSTNAME, RDS_PORT, RDS_DB_NAME, RDS_USERNAME, RDS_PASSWORD
- Environment can be changed at will - data is outside of the lifecycle of that environment

Decoupling the RDS from the EB environment allows for the RDS to be managed independently of the EB environment.

- Create an RDS Snapshot
- Enable Delete Protection
- Create a new Environment with the same app version
- Ensure new environment can connect to the DB
- Swap CNAMEs to the new environment (CNAME or DNS change)
- Terminate the old environment - this will try and terminate the RDS instance
- Locate DELETE_FAILED Stack, manually delete and pick to retain stuck resources

### Elastic Beanstalk (EB) - Advanced Customisation via .ebextensions

You can add AWS Elastic Beanstalk configuration files (.ebextensions) to your web application's source code to configure your environment and customize the AWS resources that it contains. Configuration files are YAML- or JSON-formatted documents with a .config file extension that you place in a folder named .ebextensions and deploy in your application source bundle.

- .ebextensions are a way to customise the environment
- Inside application source bundle (zip/war)
- .ebextensions folder at the root
- Add YAML or JSON files ending in .config
- Uses CFN format to create additional resources within the EB environment
- `options_settings` - allows you to set options of resources
- Resources allow entirely new resources to be created
- ...packages, sources, files, commands, users, groups, container commands

### Elastic Beanstalk (EB) - HTTPS

- Apply the SSL certificate to the load balancer
- via EB Console => Environment => Load Balancer Configuration
- Or via .ebextensions/securelistener-alb.config
- Make sure you configure the security group to allow HTTPS traffic

### Elastic Beanstalk (EB) - Environment Cloning

You can use an existing Elastic Beanstalk environment as the basis for a new environment by cloning the existing environment. For example, you might want to create a clone so that you can use a newer version of the platform branch used by the original environment's platform. Elastic Beanstalk configures the clone with the same environment settings used by the original environment. By cloning an existing environment instead of creating a new environment, you don't have to manually configure option settings, environment variables, and other settings. Elastic Beanstalk also creates a copy of any AWS resource associated with the original environment. However, during the cloning process, Elastic Beanstalk doesn't copy data from Amazon RDS to the clone. After you create the clone environment, you can modify environment configuration settings as needed.

- Create a NEW environment, by cloning an EXISTING environment
- PROD-ENV to a new TEST-ENV (for testing and Q/A)
- new version of platform branch
- Copies options, env vars, resources and other settings
- Includes RDS in ENV, but no data is copied
- unmanaged changes are NOT included
- Console UI, API or "eb clone EXISTING-ENVNAME"

### Elastic Beanstalk (EB) - Docker

AWS Elastic Beanstalk can launch Docker environments by building an image described in a Dockerfile or pulling a remote Docker image. If you're deploying a remote Docker image, you don't need to include a Dockerfile. Instead, if you are also using Docker Compose, use a docker-compose.yml file, which specifies an image to use and additional configuration options. If you are not using Docker Compose with your Docker environments, use a Dockerrun.aws.json file instead.

- Single Docker Container
- This mode uses EC2 with docker, Not ECS
- Provide 1 of 3 things
- Dockerfile: EB will build a docker image use this to run a container
- Dockerrun.aws.json (version 1): Use and existing docker image - configues image, ports, volumes and other docker attributes
- Docker-compose.yml - if you use docker compose

- Multi Docker Container
- Multiple container applications
- Create an ECS Cluster
- EC2 instance provisioned in the cluster and an ELB for high availability
- You need to provide a Dockerrun.aws.json (version 2) file in the application source bundle (root level)
- Any images need to be stored ina a container registry (ECR, Docker Hub, etc)

## CloudWatch Events and EventBridge

CloudWatch Events and EventBridge have visibility over events generated by supported AWS services within an account.

They can monitor the default account event bus - and pattern match events flowing through and deliver these events to multiple targets.

They are also the source of scheduled events which can perform certain actions at certain times of day, days of the week, or multiple combinations of both - using the Unix CRON time expression format.

Both services are one way how event driven architectures can be implemented within AWS.
