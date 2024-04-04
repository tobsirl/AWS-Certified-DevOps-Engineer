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

- If X happens, or at Y time(s) ... do Z
- EventBridge is ... CloudWatch Events v2
- A **default** event bus for the account
- In CloudWatch Events this is the **only** event bus
- In EventBridge there can be **multiple** event buses
- Rules match incoming events ... (or scheduled events)
- Route the events to 1+ Targets ..e.g. Lambda

## Lambda

AWS Lambda is a serverless compute service that runs your code in response to events and automatically manages the underlying compute resources for you. You can use AWS Lambda to extend other AWS services with custom logic, or create your own back-end services that operate at AWS scale, performance, and security.

- Function as a Service (FaaS) - short running & focussed
- Lambda **function** - a **piece of code** lambda runs
- Functions use a **runtime** (e.g. Python 3.8)
- Functions are loaded and run in a **runtime environment**
- The environment has a _direct memory_ (indirect CPU) allocation
- You are billed for the **duration that a function runs**
- A key part of **Serverless** architectures

### Lambda - facts

- 900 seconds (15 minutes) max runtime
- 128MB - 10,240 MB memory in 64MB increments
- 512MB storage available in /tmp up to 10,240MB
- 1vCPU per 1,792 MB of memory

### Lambda - Common Use Cases

- Serverless Applications (S3, API Gateway, DynamoDB, Lambda)
- File Processing (S3, Lambda, S3 Events)
- Database Triggers (DynamoDB, Lambda, Streams)
- Serverless CRON Jobs (CloudWatch Events/EventBridge + Lambda)
- Realtime Stream Data Processing (Kinesis + Lambda)

### Lambda - Networking Public

- By deault lambda functions are given public networking.
- They can access public AWS services and the public internet.
- Public networking offers the best performance because no customer specific VPC networking is required.
- Lambda functions have **no access** to VPC based services unless public IPs are provided and secruity controls allow external access.

### Lambda - Networking VPC

- Lambda functions running in a VPC obey all networking rules of that VPC.
- However, this means they can't access the public internet.
- VPC Endpoints can be used to access public AWS services without public IPs.
- Nat Gateways and Internet Gateways are required for VPC Lambdas to access the public internet.

### Lambda - Security

- Lambda execution roles are IAM roles attached to lambda functions which control the PERMISSIONS the Lambda function RECEIVES...
- Lambda resource policy controls **WHAT** services and accounts can **INVOKE** lambda functions

### AWS Lambda - Logging

- Lambda uses CloudWatch Logs and X-Ray for logging and tracing
- Logs from Lambda execution are sent to CloudWatch Logs
- Metrics - invocation success/failure, retries, latency are stored in CloudWatch
- Lambda can by integrated with X-Ray for distributed tracing
- CloudWatch logs requires permissions via Execution Role

### Lambda - Invocation Types

#### Synchronous

- CLI / API **invokes** a lambda function, passing in data and **waiting for a response**
- Lambda function responds with data or fails

#### Asynchronous

- Typically used for **event driven** architectures
- AWS services invoke a lambda function and **do not wait for a response**

#### Event Source Mappings

- Typically used on streams or queues which don't support event generation to invoke lambda (Kinesis, DynamoDB streams, SQS)

#### Lambda Destinations

- Used to send the result of a lambda function to another service
- e.g. S3, SNS, SQS, EventBridge, Lambda

### Lambda - Versions

- Lambda functions can have multiple versions - v1, v2, v3
- A version is the code + configuration of the lambda function
- It's immutable - it never changes once published and has its own ARN
- $latest points at the latest version of the function
- Aliases (DEV, STAGE, PROD) can point at different versions - can be changed

### Lambda - Function Handler

[Function Handler](https://docs.aws.amazon.com/lambda/latest/dg/runtimes-context.html)

- Lambda executions have **lifecycles**
- **Execution Environment** is created
- **INIT** creates or Unfreezes the Execution Environment
- **INVOKE** runs the function handler (Cold start)
- Next **INVOKE(s)** reuses the Execution Environment (Warm start)
- **SHUTDOWN** - Terminate the Execution Environment

#### Lambda - Function Handler - Phases

- **INIT** - Execution Initialization, Runtime initialization, Function initialization
- **INVOKE** - Function handler, Function code
- **SHUTDOWN** - Runtime Shutdown, Execution Environment Shutdown

- Function Initialization code (outside of the handler) is executed once every cold start, during the function initialization phase. (or in advance if you use provisioned concurrency)
- Lambda attempts to reuse an execution environment for subsequent invocations, so the function initialization code is not executed again unless the execution environment is frozen by AWS Lambda due to inactivity or other reasons.
- Your lambda function should assume a cold start every time... but should be able to take advantage if it's an additional invoke in the same environment (warm start)
- Environment are shut down after a period of inactivity

### Lambda - Versions and Aliases

You can use versions to manage the deployment of your functions. For example, you can publish a new version of a function for beta testing without affecting users of the stable production version. Lambda creates a new version of your function each time that you publish the function. The new version is a copy of the unpublished version of the function.

- Unpublished functions - can be changed and deployed
- this is what you've used so far (Deploys to $LATEST)
- Functions can be published - this creates an immutable version
- locked, no editing of that published version
- Functions Code, Dependencies, Runtime, Settings & Environment Variables
- A unique ARN for that function version (uniquely identifies)
- Qualified ARN points at a specific version
- Unqualified ARN points at the function ($LATEST) - not a specific version

A function version includes the following information:

- The function code and all associated dependencies.
- The Lambda runtime that invokes the function.
- All of the function settings, including the environment variables.
- A unique Amazon Resource Name (ARN) to identify the specific version of the function.

### Lambda - Aliases

You can create one or more aliases for your Lambda function. A Lambda alias is like a pointer to a specific function version. Users can access the function version using the alias Amazon Resource Name (ARN).

Aliases can point at a single version, or be configured to perform weighted routing between 2 versions.

- An **Alias** is a pointer to a specific version of a function
- PROD => bestanimal:1, STAGE => bestanimal:2
- Each **Alias** has a **unique ARN** .. fixed for the alias
- Alias can be **updated**, changing **which version** they reference
- Useful for PROD/DEV, A/B Testing, Blue/Green deployments
- Alias Routing .. percentage at v1 & percentage at v2
- ... need same role, same dead-letter queue and not $LATEST

### Lambda - Environment Variables

An environment variable is a pair of strings that are stored in a function's version-specific configuration. The Lambda runtime makes environment variables available to your code and sets additional environment variables that contain information about the function and invocation request.

- KEY & VALUE pairs (0 or more)
- Associated with $LATEST (Can be edited)
- Associated with a version (Immutable)
- Can be accessed within the execution environment
- Can be encrypted using KMS
- Allow code execution to be adjusted based on variables

### Lambda - Monitoring, Logging and Tracing

AWS Lambda integrates with other AWS services to help you monitor and troubleshoot your Lambda functions. Lambda automatically monitors Lambda functions on your behalf and reports metrics through Amazon CloudWatch.
To help you monitor your code when it runs, Lambda automatically tracks the number of requests, the invocation duration per request, and the number of requests that result in an error.

- All Lambda metrics are available in CloudWatch
- ... directly or via monitoring tab on a specific function
- Dimensions - FunctionName, Resource (Alias/Version), Executed Version (combination of alias and version i.e weighted alias) adn ALL FUNCTIONS
- Invocation, Errors, Duration, Concurrent Executions
- DeadLetterErrors, DestinationDeliveryFailures

### Lambda - Logging

- Lambda Execution logs => CloudWatch Logs
- stdout or stderr
- Log Groups = /aws/lambda/function-name
- Log Streams = YYYY/MM/DD/[$LATEST||version]..random
- Permissions via Execution Role
- ... default role give logging permissions

### Lambda - Tracing

- AWS X-Ray shows the flow of requests through your application
- Enable 'Active Tracing' in the Lambda function
- aws lambda update-function-configuration --function-name my-function --tracing-config Mode=Active
- AWSXRayWriteOnlyAccess policy required
- Use X-Ray SDK within your function code
- AWS_XRAY_DAEMON_ADDRESS environment variable

### Lambda - Layers

You can configure your Lambda function to pull in additional code and content in the form of layers. A layer is a .zip file archive that contains libraries, a custom runtime, or other dependencies. With layers, you can use libraries in your function without needing to include them in your deployment package.

[Layers](https://aws.amazon.com/blogs/aws/new-for-aws-lambda-use-any-programming-language-and-share-common-components/)

### Lambda - Container Images

You can package your code and dependencies as a container image using tools such as the Docker command line interface (CLI). You can then upload the image to your container registry hosted on Amazon Elastic Container Registry (Amazon ECR).

AWS provides a set of open-source base images that you can use to build the container image for your function code. You can also use alternative base images from other container registries. AWS also provides an open-source runtime client that you add to your alternative base image to make it compatible with the Lambda service.

Additionally, AWS provides a runtime interface emulator for you to test your functions locally using tools such as the Docker CLI.

- Lambda is a Function as a Service (FaaS) product
- Create a function, upload code, it executes
- This is awesome... But has 2 problems
- ORG... use containers & CI/CD processes built for containers
- ...would like a way of locally testing lambda functions before deploying
- Lambda Runtime API - IN CONTAINER IMAGE
- AWS Lambda Runtime Interface Emulator - LOCAL TESTING

### Lambda - ALB Integration

You can use a Lambda function to process requests from an Application Load Balancer. Elastic Load Balancing supports Lambda functions as a target for an Application Load Balancer. Use load balancer rules to route HTTP requests to a function, based on path or header values. Process the request and return an HTTP response from your Lambda function.

Elastic Load Balancing invokes your Lambda function synchronously with an event that contains the request body and metadata.

### Lambda - Resource Policies

Two forms of security policy for Lambda

- Execution Role - Assumed by the function, determines **WHAT** the function **CAN DO**
- Resource Policy - **WHO** can do **WHAT** with the lambda function
- Cross Account Access - requires Identity (OUT) AND Resource Policy (IN)
- Required when a service needs to invoke a lambda function in another account
- Required cross-account (lambda has no trust)
- Not required for an identity in the same account
- Can view and perform limited edits in the UI
- .. also full control via CLI/API

## API Gateway

Amazon API Gateway is a fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale. APIs act as the "front door" for applications to access data, business logic, or functionality from your backend services.

[API Gateway Error Codes](https://docs.aws.amazon.com/apigateway/latest/api/CommonErrors.html)

- Create and manage APIs
- Endpoint/entry-point for applications to access data, business logic or functionality
- Sits between applications and integrations (services)
- Highly available, scalable, handles authorisation, throttling, caching, CORS, transformations, OpenAPI spec, direct integrations, Lambda, HTTP, AWS services, VPC links
- Can connect to services/endpoints in AWS or on-premises
- HTTP APIs, REST APIs and WebSocket APIs

### API Gateway - Endpoint Types

- **Edge Optimised** - for global clients - routed to the nearest CloudFront Point of Presence
- **Regional** - for clients in the same region
- **Private** - endpoint accessible only within a VPC via an interface endpoint

### API Gateway - Stages

- **Stages** - a logical reference to a lifecycle of an API
- APIs are deployed to stages, each stage has one deployment
- Stages can be enabled for canary deployments. If done, deployments are made to the canary not the stage
- Stages enabled for canary deployments can be configured so a certain percentage of traffic is sent to the canary. This can be adjusted over time - or the carary can be promoted to make it the new base 'stage'

### API Gateway - Errors

- 4XX - Client Errors - e.g. 400, 401, 403, 404 invalid request on client side
- 5XX - Server Errors - e.g. 500, 502, 503, 504 server side errors, valid request, backend error
- 400 - Bad Request - Generic client side error
- 403 - Forbidden - Client does not have permission e.g. Authorizer denies, WAF filter
- 429 - API Gateway can throttle requests- this means you've exceeded the rate limit
- 502 - Bad Gateway - API Gateway can't reach the backend, bad output returned by lambda
- 503 - Service Unavailable - API Gateway can't reach the backend, backend is down
- 504 - Gateway Timeout - API Gateway can't reach the backend, backend is taking too long to respond, integration failure/timeout - 29s limit

### API Gateway - Caching

- API Gateway can cache responses from the backend
- This can reduce the number of calls to the backend
- Cache can be configured per method
- Cache TTL default is 300 seconds
- Configurable from 0 to 3600 seconds
- Cache can be invalidated
- Cache can be encrypted
- Cache size 500MB to 237GB
- Cache is defined per stage

### API Gateway - Methods and Resources

- Invoke URL points at the _API Gateway Endpoint_, **stage** and `resource`

```bash
https://api-id.execute-api.region.amazonaws.com/stage/resource
```

- Stages are logical configurations which exist within API Gateway.
- APIs are deployed into stages
- Can be used for different versions or lifecycle stages of the API
- Think of resources as points in the API tree or bit of functionality within your API.
- Methods are desired action to be performed HTTP verbs (GET, POST, PUT, DELETE, PATCH, OPTIONS, HEAD)
- Methods are where integrations are configured which provide the functionality of the API e.g. lambda, HTTP and AWS services

### API Gateway - Integration Types

You choose an API integration type according to the types of integration endpoint you work with and how you want data to pass to and from the integration endpoint. For a Lambda function, you can have the Lambda proxy integration, or the Lambda custom integration. For an HTTP endpoint, you can have the HTTP proxy integration or the HTTP custom integration. For an AWS service action, you have the AWS integration of the non-proxy type only. API Gateway also supports the mock integration, where API Gateway serves as an integration endpoint to respond to a method request.

- API Methods (client) are integrated with a backend endpoint
- Different types of integration are available
- **Mock** - return a response without invoking a backend, used for testing
- **HTTP** - Backend HTTP endpoint
- **HTTP Proxy** - Pass through to integration unmodified, return to the client unmodified (backend needs to use supported format)
- **AWS** - Lets and API expose AWS service actions
- **AWS Proxy (Lambda)** - Low admin overhead Lambda endpoint

[Integration Types](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-api-integration-types.html)

### API Gateway - Mapping Templates

- Used for AWS and HTTP (non PROXY) integrations
- Modify of Rename Parameters
- Modify the body or headers of the request
- Filtering - removing anything which isn't needed
- Uses Velocity Template Language (VTL)
- Common exam scenario is REST API (on API Gateway) to a SOAP API ..transfrom the request using mapping template

### API Gateway - Stages and Deployments

A stage is a named reference to a deployment, which is a snapshot of the API. You use a Stage to manage and optimize a particular deployment. For example, you can configure stage settings to enable caching, customize request throttling, configure logging, define stage variables, or attach a canary release for testing.

- Changes made in API Gateway are not live until they are deployed
- The current API state needs to be deployed to a stage
- Stages can be environments (DEV, TEST, PROD)
- or versions (v1, v2, v3) - for breaking changes
- Each stage has its own configuration
- not immutable, can be overwritten

### API Gateway - Swagger and OpenAPI

You can use API Gateway to import a REST API from an external definition file into API Gateway. Currently, API Gateway supports OpenAPI v2.0 and OpenAPI v3.0 definition files. You can update an API by overwriting it with a new definition, or you can merge a definition with an existing API.

- OpenAPI (Swagger) is a specification for building APIs
- Swagger = v2.0, OpenAPI = v3.0
- OpenAPI v3.0 is the latest version
- API Description format for REST APIs
- Endpoints (/listcats) and Operations (GET, POST, PUT, DELETE)
- Input and Output Parameters and Authentication Methods
- Non tech infromaton - Contact Info, Licence, Terms of use
- API Gateway can export to Swagger/OpenAPI and import from Swagger/OpenAPI

## Simple Notification Service (SNS)

The Simple Notification Service (SNS) is a pub/sub system in AWS for the reliable delivery of notification style messages between AWS components or between AWS and external systems.

- Public AWS Service - network connectivity with Public Endpoint
- Coordinates the sending and delivery of messages
- Messages are <= 256KB payloads
- SNS Topics are base entity of SNS - permissions and configuration
- A Publisher sends messages to a Topic
- e.g. HTTP, Lambda, SQS, Email, SMS, Mobile Push, Lambda
- SNS used across AWS for notifications - e.g. CloudWatch and CloudFormation
- Delivery Status - Success, Failure, TimeOut (for Lambda, SQS, HTTP)
- Delivery Retries - 3 retries, 1 second, 5 seconds, 10 seconds
- HA and Scalable - 11 9's durability, 300 seconds retention
- Server Side Encryption (SSE) - KMS or AWS Managed Keys
- Cross Account via TOPIC Policy

## Simple Queue Service (SQS)

SQS queues are a managed message queue service in AWS which help to decouple application components, allow Asynchronous messaging or the implementation of worker pools.

- Public, Fully Managed, Highly Available Queues - Standard and FIFO
- Messages up to 256KB in size - link to large data
- Received messages are hidden (Visibility Timeout) - 12 hours max
- .. then either reappear (retry) or are explicitly deleted
- Dead-Letter Queues - messages which can't be processed
- ASGs can scale and Lambdas invoke based on queue length

### SQS - Standard Queue

- Standard = at least once delivery
- Billed based on number of requests
- 1 request = 1-10 messages (up to 256KB)
- Short Polling - returns immediately, even if no messages
- Long Polling - waits for messages, reduces cost and latency (waitTimeSeconds - up to 20 seconds)
- Encrypted at rest(KMS) and in transit
- Queue Policies - control who can send and receive messages
- Best Effort Ordering - not guaranteed
- At least once delivery - messages can be delivered more than once
- Decoupling, worker pools, Batch for future processing

### SQS - FIFO Queue

- FIFO = exactly once delivery
- Messages are delivered in order
- FIFO (Performance) **3,000 messages per second** with batching, or up to **300 messages per second** (individual messages)
- Message order is strictly preserved - First In, First Out
- Exactly Once Processing - Deduplicates are removed
- Must have .fifo suffix

### SQS - Extended Client Library

[Extended Client Library](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-extended-client.html)

- Used when handling message over SQS max (256KB)
- Allows large payloads - **stored in S3**
- **SendMessage**, uploads to S3, stores link in **message**
- **Receive message** loads large payload from S3
- **Delete message** also **deletes large S3 payload**
- Interface for SQS+S3 - handling the integration workload
- Exam often mentions **Java** with Extended Client Library

### SQS - Delay Queues

Delay queues provide an initial period of invisibility for messages. Predefine periods can ensure that processing of messages doesn't begin until this period has expired.

[Amazon SQS message timers](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-message-timers.html)

[Amazon SQS delay queues](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-delay-queues.html)

[Amazon SQS visibility timeout](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-visibility-timeout.html)

### SQS - Dead Letter Queues

Dead letter queues allow for messages which are causing repeated processing errors to be moved into a dead letter queue in this queue, different processing methods, diagnostic methods or logging methods can be used to identity message faults

- Redrive Policy - Specifies the source queue, the dead-letter queue and the condidtions where messages will be moved from one to the other Define **maxReceiveCount**
- When ReceiveCount > maxReceiveCount amd message isn't deleted, it's moved to the dead-letter queue
- Enqueue timestamp of message is unchanged. Retention period of a dead-letter queue is generally longer than the source queue (s)

## Step Functions

Step functions is a product which lets you build long running serverless workflow based applications within AWS which integrate with many AWS services.
Step functions help with the limitation of Lambda functions which can only run for 15 minutes. Step functions can run for up to a year.

- Lambda is FaaS - short running, focussed
- 15 minutes max runtime
- Can be chained together, but not ideal for long running workflows
- Gets messy at scale
- Runtime Environments are stateless

### Step Functions - State Machines

- Serverless workflow .. START -> STATE -> STATE -> END
- States are THINGS that happen
- Maximum Duration of 1 year
- Standard Workflow and Express Workflows
- Started via API Gateway, IOT Rules, EventBridge, Lambda...
- Amazon States Language - JSON based language to define state machines
- IAM Role is used for permissions

### Step Functions - States

- SUCCEED and FAIL are terminal states
- WAIT is a delay
- CHOICE is a conditional
- PARALLEL is a parallel execution
- MAP is a parallel execution with dynamic number of iterations
- TASK is a call to a service (Lambda, ECS, Batch, SNS, SQS, DynamoDB, Glue, S3, SSM, Fargate, Step Functions, SageMaker, EMR, EC2, API Gateway, HTTP, etc)

## Elastic Container Service (ECS)

[ContainerDefinition](https://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_ContainerDefinition.html)

[ECS TaskDefinition](https://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_TaskDefinition.html)

### ECS Concepts

- **Container Definition** - Image and Ports
- **Task Definition** - Security(Task Role), IAM, Volumes, Network, Placement
- **Task Role** - IAM Role which the TASK assumes
- **Service** - How many compies, HA, Restarts

### ECS - Cluster Types

- ECS is capable of running in EC2 mode or Fargate mode.

#### EC2 Mode

- EC2 mode deploys EC2 instances into your AWS account which can be used to deploy tasks and services.
- With EC2 mode you pay for the EC2 instances regardless of container usage

#### Fargate Mode

- Fargate mode uses shared AWS infrastructure, and ENI's which are injected into your VPC
- You pay only for container resources used while they are running.

## Kubernetes (EKS)

Amazon Elastic Kubernetes Service (Amazon EKS) is a managed service that makes it easy for you to run Kubernetes on AWS without needing to install, operate, and maintain your own Kubernetes control plane or nodes.

### Kubernetes Cluster Structure

- Highly available cluster of compute resources which are **organised** to work as **one unit**
- Cluster Control Plane manages the cluster, scheduling, applications, scaling and deploying
- Cluster Nodes - A VM or Physical server which functions as a worker in the cluster
- containerd or Docker Software for handling container operations - Container Runtime
- kubelet - agent to interact with the cluster control plane
- Kubernetes API used for communication between the control plane and kubelet agent
- Pods are the smallest unit of computing in Kubernetes Shared storage and networking "one-container-one-pod" is very common PODS ARE NONPERMANENT
- kube-apiserver - the frond-end for the Kubernetes control plane. It's what nodes and other cluster elements interact with. Can be horizontally scaled for HA and performance.
- etcd provides a highly-available key value store used within the cluster. It's used as the main backing store fro the cluster.
- kube-scheduler identifies any pods within the cluster with no assigned node and assigns a node based on resource requirements, deadlines, affinity/anti affinity, data locality and any constraints.
- cloud-controller-manager provides cloud-specific control logic. It allows you to link Kubernetes with a cloud providers APIs (i.e AWS/Azure/GCP)
- kube-controller-manager cluster controller processes
- Node Controller - monitoring and responding to node conditions
- Job Controller - one-off tasks (jobs) => PODS
- Endpoint Controller - populates endpoints (Services <=> Pods)
- Service Account and Token Controllers - create default accounts and API access tokens for new namespaces
- kube-proxy is a network proxy. Running on each node, it coordinates networking with the control plane. It helps implement "services" and configures rules allowing communications with pods from inside or outside of the cluster.

### Elastic Kubernetes - EKS

Amazon Elastic Kubernetes Service (Amazon EKS) is a fully-managed, Kubernetes implementation that simplifies the process of building, securing, operating, and maintaining Kubernetes clusters on AWS.

- AWS Managed Kubernetes Service - open source and cloud agnostic
- AWS, Outposts, EKS Anywhere, EKS Distro
- Controle plane scales and runs on multiple AZs
- Integrates with AWS Services - IAM, VPC, EBS, EFS, ELB, CloudWatch, CloudTrail, KMS, Secrets Manager, Cognito
- EKS Cluster = EKS Control Plane + EKS Worker Nodes
- etcd distributed across multiple AZs
- Nodes - Self Managed, Managed node groups or Fargate pods
- windows, GPU, Inferentia, Graviton2, ARM, x86
- Storage Providers - include.. EBS, EFS, FSx, S3, RDS, DynamoDB, Aurora, Neptune, DocumentDB, ElastiCache, Redshift, S3, EBS, EFS, FSx, S3, RDS, DynamoDB, Aurora, Neptune, DocumentDB, ElastiCache, Redshift
- EKSCTL - CLI for EKS

[Amazon EKS nodes](https://docs.aws.amazon.com/eks/latest/userguide/eks-compute.html)
[AWS Fargate](https://docs.aws.amazon.com/eks/latest/userguide/fargate.html)

## AWS OpsWorks

AWS OpsWorks provides managed implementations of Puppet and Chef in a product which integrates with other AWS Products and services.

AWS OpsWorks has three modes:

- **Puppet Enterprise** AWS Managed Puppet Master Server
- **Chef Automate** AWS Managed Chef Server
- **OpsWorks** AWS Integrated Chef, No Servers
- Use when you already have one of these
- Requirement to automate...
- See Recipes, Cookbooks or Manifests for more information

### OpsWorks - Stacks

- Stacks - Core Component ...container of resources
- Layers - each layer is a specific function within a stack
- Recipes & Cookbooks - Chef or Puppet
- Lifecycle Events - Setup, Configure, Deploy, Undeploy, Shutdown
- Instances - 24/7, Time-Based of Load-Based
- Apps - Deployed to instances

## SSM - Parameter Store

The SSM Parameter store is a service which is part of Systems Manager which allows the storage and retrieval of parameters - string, stringlist or secure string.

The service supports encryption which integrates with KMS, versioning and can be secured using IAM.

The service integrates natively with many AWS services - and can be accessed using the CLI/APIs from anywhere with access to the AWS Public Space Endpoints.

## SSM - Secrets Manager

AWS Secrets manager is a product which can manage secrets within AWS. There is some overlap between it and the SSM Parameter Store - but Secrets manager is specialised for secrets.

Additionally Secrets managed is capable of automatic credential rotation using Lambda.

For supported services it can even adjust the credentials of the service itself.

- It does share functionality with SSM Parameter Store
- Designed for secrets - passwords, API keys, tokens
- Usable via Console, CLI, SDK, API
- Automatic rotation of secrets ...this uses Lambda
- Directly integrates with some AWS products e.g. RDS, Redshift

## Security Token Service (STS)

STS is a fundamental AWS Service which is used within many other identity related services.

- Generates temporary credentials for IAM users or roles (sts:AssumeRole)
- Similar to access keys
- ..they expire and don't belong to the identity
- Limited Access
- Requested by an identity (AWS or EXTERNAL)

### STS - How it works

- The Trush policy controls who can assume the role. Conceptually this is a wall around the role.
- If an identity isn't ALLOWED to assume the role, based on the TRUST policy.. AssumeRole will fail
- sts:AssumeRole calls are made by and existing identity ..either AWS or External(federation)
- Premissions Policy controls what the identity can do once it has assumed the role
- STS generates temporary credentials which can access AWS resources until expiration. They authorise access based on the permissions policy.
- Temporary credentials consists of AccessKeyId (unique ID of the credentials), SecretAccessKey(used to sign requests), SessionToken(unique token which must be passed with all requests) and Expiration(date and time of credentials expiration)
- Credentials are returned to the identity which requested them. Another sts:AssumeRole is required when credentials expire.

## Policy Interpretation Deep Dive - Example 1

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:PutObject",
        "s3:PutObjectAcl",
        "s3:GetObject",
        "s3:GetObjectAcl",
        "s3:DeleteObject"
      ],
      "Resource": "arn:aws:s3:::holidaygifts/*"
    },
    {
      "Effect": "Deny",
      "Action": ["s3:GetObject", "s3:GetObjectAcl"],
      "Resource": "arn:aws:s3:::holidaygifts/*",
      "Condition": {
        "DateGreaterThan": {
          "aws:CurrentTime": "2022-12-01T00:00:00Z"
        },
        "DateLessThan": {
          "aws:CurrentTime": "2022-12-25T06:00:00Z"
        }
      }
    }
  ]
}
```

- Number of statements: 2 (Counted by the brackets)
- Statements are always Allow or Deny
- AWS defaults to Deny
- Explicit Deny always overrides Allow
- Resource is the S3 bucket and the paths are the same so are overlapping

## Policy Interpretation Deep Dive - Example 2

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "DenyNonApprovedRegions",
      "Effect": "Deny",
      "NotAction": ["cloudfront:*", "iam:*", "route53:*", "support:*"],
      "Resource": "*",
      "Condition": {
        "StringNotEquals": {
          "aws:RequestedRegion": ["ap-southeast-2", "eu-west-1"]
        }
      }
    }
  ]
}
```

- Inverted logic - NotAction
- StringNotEquals - aws:RequestedRegion

## Policy Interpretation Deep Dive - Example 3

[IAM policy elements: Variables and tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_variables.html)

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["s3:ListAllMyBuckets", "s3:GetBucketLocation"],
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": "arn:aws:s3:::cl-animals4life",
      "Condition": {
        "StringLike": {
          "s3:prefix": ["", "home/", "home/${aws:username}/*"]
        }
      }
    },
    {
      "Effect": "Allow",
      "Action": "s3:*",
      "Resource": [
        "arn:aws:s3:::cl-animals4life/home/${aws:username}",
        "arn:aws:s3:::cl-animals4life/home/${aws:username}/*"
      ]
    }
  ]
}
```

- 3 statements
- 1st statement - ListAllMyBuckets and GetBucketLocation
- 2nd statement - ListBucket - with a condition
- 3rd statement - All actions on the home directory and subdirectories

## Permission Boundaries

Permission boundaries are an advanced feature of AWS IAM which can be used to limit the maximum permissions which can be granted to an identity.

- Only Identity-based policies can be limited by a permission boundary
- Boundaries can be applied to IAM Users or IAM Roles
- Permissions boundaries don't GRANT any access on their own. They define maximum permissions that can be granted

## Policy Evaluation Logic

- Explicit Deny are evaluated first
- Organisations SCPs are evaluated next
- Resource Policies are evaluated next
- Permissions Boundaries are evaluated next
- Session Policies are evaluated next
- Identity-based policies are evaluated last

## Route 53 Fundamentals

Amazon Route 53 is a scalable and highly available Domain Name System (DNS) web service. It is designed to give developers and businesses an extremely reliable and cost effective way to route end users to Internet applications by translating human readable names like www.example.com into the numeric IP addresses like

- Route 53 is a global service
- Register and manage domain names
- Host Zones.. managed nameservers
- Globally Resilient and Highly Available

### Route 53 - Hosted Zones

- Zone files in AWS
- Hosted on four managed name servers
- Can be public
- Can be private ..linked to VPCs
- ..stores records(recordsets) - A, AAAA, CNAME, MX, NS, PTR, SOA, SPF, SRV, TXT

### Route 53 - Record Sets

DNS is capable of handling a number of different record types - which perform different tasks.

Name servers are responsible for resolving the domain name to an IP address.

- A - Address Record - maps a domain name to an IP address
- AAAA - IPv6 Address Record - maps a domain name to an IPv6 address
- CNAME - Canonical Name Record - maps an alias to another name
- MX - Mail Exchange Record - maps a domain name to a list of mail exchange servers for that domain
- NS - Name Server Record - maps a domain name to a list of DNS servers authoritative for that domain
- TXT - Text Record - used to associate some text with a domain

### Route 53 - Public Hosted Zones

A public hosted zone is a container that holds information about how you want to route traffic on the internet for a specific domain which is accessible from the public internet

- A Hosted Zone is a DNS database for a domain name
- Globally Resilient and Highly Available (multiple DNS servers)
- Created with domain registration via Route 53 - can be created separately
- Host DNS Records - A, AAAA, CNAME, MX, NS, PTR, SOA, SPF, SRV, TXT
- Hosted Zones are what the DNS system references - Authoritative for a domain name

- DNS Database (zone file) hosted by Route 53 (Public Name Servers)
- Accessible from the public internet & VPCs
- Hosted on 4 Route 53 Name Servers specific for the zone
- use "NS records" to point at these NS (connect to global DNS)
- Resource Records (RR) created within the Hosted Zone
- Externally registed domains can point at Route 53 Public Zone

### Route 53 - Private Hosted Zones

A private hosted zone is a container that holds information about how you want Amazon Route 53 to respond to DNS queries for a domain and its subdomains within one or more VPCs that you create with the Amazon VPC service

- A Public Hosted Zone which isn't public
- Associated with VPCs
- ..only accessible from those VPCs
- ..Using different accounts is supported via CLI/API
- Split-view (overlapping public and private zones) for Public and Internal use with the same domain name

### Route 53 - CNAME vs Alias

#### CNAME

- "A" maps a NAME to an IP Address
- ..catagram.io => 1.3.3.7
- CNAME maps a NAME to another NAME
- ..www.catagram.io => catagram.io
- CNAME is invalid for naked/apex domains (catagram.io)
- Many AWS services use a DNS Name (ELBs)
- With just CNAME, catagram.io => ELB would be invalid

#### Alias

- ALIAS records map a NAME to an AWS resource
- Can be used both for naked/apex and normal records
- For non apex/naked - functions like a CNAME
- There is no charge for ALIAS requests pointing at AWS resources
- For AWS Services - default to pick ALIAS over CNAME
- Should be the same "Type" as what the record is pointing at
- API Gateway, CloudFront, ELB, S3, S3 Static Website Hosting, VPC Endpoints, Global Accelerator

### Route 53 - Routing Policies

#### Simple Routing

Simple routing lets you configure standard DNS records, with no special Route 53 routing such as weighted or latency. With simple routing, you typically route traffic to a single resource, for example, to a web server for your website.

- Use Simple Routing when you want to route requests towards one service such as a web server
- Simple Routing doesn't support health checks or failover routing - all values are returned for a record when queried

#### Failover Routing

Failover routing lets you route traffic to a resource when the resource is healthy or to a different resource when the first resource is unhealthy. You might use failover routing when you want to configure an active-passive failover setup.

- Use Failover Routing when you want to route requests towards one service such as a web server
- Failover Routing supports health checks and failover routing - you can specify a primary and secondary record
- Failover Routing can be used for active-passive failover

#### Multi Value Routing

Multivalue answer routing lets you configure Amazon Route 53 to return multiple values, such as IP addresses for your web servers, in response to DNS queries. You can specify multiple values for almost any record, but multivalue answer routing also lets you check the health of each resource, so Route 53 returns only values for healthy resources.

- Multi Value Routing supports multiple records for a single record set
- Up to 8 healthy records returned for a single record set, if more than 8 are healthy, a random 8 are returned
- Each record is independent and can have its own health check
- Any records which are unhealthy are not returned
- Multi Value Routing improves availability and fault tolerance. It is NOT a replacement for a load balancer

#### Weighted Routing

Weighted routing lets you associate multiple resources with a single domain name (catagram.io) and choose how much traffic is routed to each resource. This can be useful for a variety of purposes, including load balancing and testing new versions of software.

- Simple load balancing or testing new software versions
- You can assign a weight to each record set
- A "0" weight record is never returned unless all other records have a weight of "0"
- Each record is returned based on its record weight vs the total weight of all records
- If a chosen record is Unhealthy, the process of selection is repeated until a healthy record is chosen

#### Latency Based Routing

If your application is hosted in multiple AWS Regions, you can improve performance for your users by serving their requests from the AWS Region that provides the lowest latency.

- Use latency-based routing when optimizing for performance and user experience
- Latency-based routing support one record with the same name in each AWS Region
- AWS maintains a database of latency between the user general location and the regions tagged in records
- The record returned is the one which offers the lowest estimated latency and is healthy

#### Geolocation Routing

Geolocation routing lets you choose the resources that serve your traffic based on the geographic location of your users, meaning the location that DNS queries originate from.

- With Geolocation Routing, records are tagged withh locatoin. Either "US state", "country", "continent" or "default"
- An IP check verifies the location of the user (normally the resolver)
- Geoloaction doesn't return "closest" records, only relevant records
- Route 53 checks the records 1) US State 2) Country 3) Continent 4) Default - it returns the most specific record or "NO AWSWER"
- Geolocation can be used for compliance, legal or performance reasons

#### Geo Proximity Routing

Geoproximity routing lets Amazon Route 53 route traffic to your resources based on the geographic location of your users and your resources. You can also optionally choose to route more traffic or less to a given resource by specifying a value, known as a bias. A bias expands or shrinks the size of the geographic region from which traffic is routed to a resource.

- Records can be tagged with an AWS Region or lat and long coordinates
- "+" or "-" bias can be added to expand or shrink the region
- Routing is distance based (including bias)

### Route 53 - Health Checks

Amazon Route 53 health checks monitor the health and performance of your web applications, web servers, and other resources. Each health check that you create can monitor one of the following:

- The health of a specified resource, such as a web server
- The status of other health checks
- The status of an Amazon CloudWatch alarm
- Health check are separate from, but are used by records
- Health checkers located globally
- Health checkers check every 30s (every 10s costs extra)
- TCP, HTTP, HTTPS, HTTP with string matching
- Healthy or Unhealthy
- Endpoint, CloudWatch Alarm, Checks of Checks (calculated health)

### Route 53 - Interoperability

- Route 53 can be used as Domain Registrar and Domain Hosting
- Route 53 can do Both, or either one

## SDLC AUTOMATION

CI/CD is handled within AWS by CodeCommit, CodeBuild, CodeDeploy and CodePipeline.

[CodeDeploy AppSpec file reference](https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-appspec-file.html)
[Build specification reference for CodeBuild](https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html)

### CodePipeline

AWS CodePipeline is a continuous delivery service you can use to model, visualize, and automate the steps required to release your software. You can quickly model and configure the different stages of a software release process. CodePipeline automates the steps required to release your software changes continuously

- CodePipeline is a CI/CD service
- Pipeline is a Continuous Delivery tool
- Controls the flow from source, through build towards deployment
- Pipelines are built from STAGES
- STAGES can have sequential or parallel ACTIONS
- Movement between stages can require manual approval
- Artifacts can be loaded into an action, and generated from an action
- State Changes => Event bridge (e.g. Success, Failure, Cancelled)
- Cloudtrail or Console UI can be used to view / interact

### CodeBuild

AWS CodeBuild is a fully managed continuous integration service that compiles source code, runs tests, and produces software packages that are ready to deploy. With CodeBuild, you don’t need to provision, manage, and scale your own build servers. CodeBuild scales continuously and processes multiple builds concurrently, so your builds are not left waiting in a queue

- Code Build as a service - fully managed
- Pay only for the resources consumed during builds
- Alternative to part of Jenkins functionality
- Used for builds and tests
- Uses docker for build environment, can be customised
- Integrates with AWS services ..KMS, IAM, VPC, CloudTrail, S3
- Architecture - Gets source from GitHub, CodeCommit, S3, ECR, CodePipeline
- Builds and tests
- Customised via buildspec.yml file (in the root of the source code)
- Logs => S3 and CloudWatch Logs
- Metrics => CloudWatch Metrics
- Events => EventBridge (event-driven response)
- Java, Ruby, Python, Node.js, Go, Docker, .NET, PHP, Android, Linux, Windows
- buildspec.yml - customise the build process
- Four main phases - install, pre_build, build, post_build
- install - install packages in the build environment (frameworks)
- pre_build - sign-in to things or install dependencies
- build - commands run during the build process
- post_build - e.g. package things up, push docker image, explicit notifications
- Environment variables - shell, variables, parameter store, secrets manager
- Artifacts - what stuff to put where

### CodeDeploy

CodeDeploy is a deployment service that automates application deployments to Amazon EC2 instances, on-premises instances, serverless Lambda functions, or Amazon ECS services.

- CodeDeploy is a deployment service
- There are alternatives - Jenkins, Ansible, Chef, Puppet, CloudFormation and more...
- Deploys code ... not resources
- EC2, On-Premises, Lambda, ECS
- Code, Web, Configuration, EXE files, Packages, Scripts, media and more
- CodeBuild integrates with AWS services & AWS Code tools
- CodeDeploy agent (on premises or EC2)
- Appspec.yml (YAML or JSON formatted)
- Manage Deployments - config + lifecycle event hooks
- Files (EC2/ON-PREMISES), Resources (LAMBDA, ECS), Permissions (EC2/ON-PREMISES)
- ApplicationStop, DownloadBundle, BeforeInstall, Install, AfterInstall, ApplicationStart, ValidateService

### Elastic Container Registry (ECR)

- Managed Container image registry service
- like docker hub ..but for AWS
- Each AWS account has a public and private registry
- Each repository can have multiple images
- Images can be tagged
- Public = public R/O ... R/W requires permissions
- Private = permissions required for any R/O or R/W
- Integrated with IAM - Permissions
- Image scanning, basic and enhanced (inspector)
- Near real-time Metrics => CW (auth, push, pull, scan)
- API Actions = CloudTrail
- Events => EventBridge
- Replication ... Cross-Region AND Cross-Account

## CloudWatch

Amazon CloudWatch is a monitoring and observability service built for DevOps engineers, developers, site reliability engineers (SREs), and IT managers. CloudWatch provides you with data and actionable insights to monitor your applications, respond to system-wide performance changes, optimize resource utilization, and get a unified view of operational health.

- Ingestion, Storage and Management of Metrics
- Public Service - public space endpoints
- ..AWS Service integration - management plane
- ..Agent integration .. e.g. EC2 - richer metrics
- ..Application Integration via API/Agents (custom metrics)
- View data via console UI, CLI, API, dashboards and anomaly detection
- Alarms ... react to metrics, can be used to notify or perform actions

### CloudWatch - Data

- Namespace = container for metrics e.g. AWS/EC2, AWS/S3, AWS/RDS, AWS/Lambda
- Datapoint = timestamp, value, unit
- Metric = time ordered set of data points
- .. CPUUtilization, NetworkIn, NetworkOut, DiskWriteBytes, DiskReadBytes
- Every metric has a MetricName (CPUUtilization) and a Namespace (AWS/EC2)
- Dimensions = name/value pairs which identify the metric e.g. CPUUtilization Name=InstanceID Value=i-1234567890abcdef0
- AutoScalingGroupName, ImageId, InstanceId, InstanceType, ServiceName
- Resolution ..Standard (1 minute) or High Resolution (1 second)
- Retention .. sub 60s = 3 hours, 60s = 15 days, 300s = 63 days, 3600s = 455 days
- As data ages, its aggregated and stored for longer with less resolution
- Statistics aggregation over a period of time - Sum, Average, Minimum, Maximum, SampleCount
- Percentile - e.g. p90, p95, p99

### CloudWatch - Alarms

- Alarm - watches a metric over a time period
- Alarm State - OK, ALARM, INSUFFICIENT_DATA
- ...value of metric vs threshold .. overtime
- ...one or more actions
- Alarm Resolution - how often to check the metric
- Alarm Actions - SNS, EC2, AutoScaling, Lambda, SQS, SSM, Kinesis, Step Functions

### CloudWatch - Logs

CloudWatch logs is a product which can store, manage and provide access to logging data for on-premises and AWS environments including systems and applications it can also via subscription filters stream the data to Lambda, Elasticsearch, Kinesis streams and firehose for further delivery
Metric filters can be used to generate Metrics within Cloudwatch, alarms and eventual events within Eventbridge.

#### CloudWatch Logs - Ingestion

- Public Service - Store, Monitor, Access logging data
- AWS, On-Premises, IOT, Custom Applications
- CWAgent - system or custom application logs
- VPC Flow Logs
- CloudTrail Logs ... Account events and AWS API Calls
- Elastic Beanstalk, ECS Container Logs, API Gateway, Lambda, RDS, Route 53, VPC Flow Logs
- Route53 - Log DNS Requests

### CloudTrail Essentials

CloudTrail Is a product which logs API calls and account events.
It's very often used to diagnose security or performance issues, or to provide quality account level traceability.
It is enabled by default in AWS accounts and logs free information with a 90 day retention.
It can be configured to store data indefinitely in S3 or CloudWatch Logs.
In this lesson I detail the theory and architecture of the product.

- Logs API calls/activities as a CloudTrail Event
- 90 days stored by default in Event History
- Enabled by default - no cost for 90 day history
- To customise the service .. create 1 or more Trails
- Management Events and Data Events
- Enabled by default .. but 90 days .. no S3
- Trails are how you configure S3 and CWLogs
- Management events only by default
- IAM, STS, CloudFront => Global Service Events
- Not realtime - 15 minute delay

## Amazon Kinesis Data Streams

Kinesis data streams are a streaming service within AWS designed to ingest large quantities of data and allow access to that data for consumers.
Kinesis is ideal for dashboards and large scale real time analytics needs.
Kinesis data firehose allows the long term persistent storage of kinesis data onto services like S3

- Kinesis is a scalable streaming service
- Producers send data into a kinesis stream
- Streams can scale from low to near infinite data rates
- Public service & highly available by design
- Stream store a 24-hour moving window of data
- .. can be increased to a maximum of 365 days (additional cost)
- Multiple consumers access data from that moving window

### Kinesis Data Streams SQS vs Kinesis

- SQS 1 production group, 1 comsumption group
- Decoupling and Asynchronous communications
- No persistence of messages, no window
- Kinesis - designed for huge scale ingestion
- .. and multiple consumers .. rolling window
- Data ingestion, Analytics, Monitoring, App Clicks

### Amazon Kinesis Data Firehose

Kinesis Data Firehose is a stream based delivery service capable of delivering high throughput streaming data to supported destinations in near realtime.

- Fully managed service to load data for data lakes, data stores and analytics services
- Automatic scaling ... fully serverless ..resilient
- Near Real Time delivery (60 seconds)
- Supports transformation of data on the fly (Lambda)
- Billing - volume through firehouse
- Firehose offers near realtime delivery of data when buffer size in 1MB fills or Buffer interval in 60 seconds

### Amazon Kinesis Data Analytics

Amazon Kinesis Data Analytics is the easiest way to analyze streaming data, gain actionable insights, and respond to your business and customer needs in real time.

- Real time processing of data
- .. Using Structured Query Language (SQL)
- Ingest from Kinisis Data Streams or Firehose
- Destination can be S3, Redshift, ElasticSearch, Lambda, Kinesis Data Streams
- Firehose (S3, Redshift, ElasticSearch, Splunk)
- AWS Lambda (custom processing)
- Kinesis Data Streams (re-ingest or further processing)
- Use Cases - Real Time Dashboards, Anomaly Detection, Real Time Metrics, Real Time Alerts
- Streaming data needing real time SQL processing
- Time-series analytics ... elections / e-sports
- Real-time dashboards - leaderboards, stock prices
- Real-time metrics - monitoring, health checks, security

## AWS MapReduce

- Data Analysis Architecture - huge scale, parallel processing
- Two Main Phases - Map and Reduce
- Optional - Combine & Partition
- Data is separated into 'splits' .. each assigned to a mapper
- Perform Operations at scale - Customisable
- Recombine Data into Results

### HDFS - Hadoop Distributed File System

- Hadoop Distributed File System
- Traditional File Systems - Stored across multiple nodes
- Highly Fault Tolerant - Data Replication between nodes
- Name Node - provides the `namespace` for the file system and controls access to HDFS
- Block .. segment of data on HDFS .. generally 64MB

### Elastic Map Reduce

Elastic Map Reduce (EMR) is the AWS Managed implementation of EMR/Hadoop within AWS.

- AWS Managed implementation of Apache Hadoop
- and Spark, HBase, Presto, Flink, Zeppelin, Jupyter, Pig
- Can be operated long term .. or use ad-hoc (transient) clusters
- Runs in ONE AZ in a VPC using EC2 instances for compute
- Auto scales - Spot, Instance Fleet, Reserved, On-Demand
- Big data processing, manipulation, analytics, indexing, transformation and more .. (data pipeline)

### Amazon Redshift (Data Warehouse)

Redshift is a column based, petabyte scale, data warehousing product within AWS.
Its designed for OLTP products within AWS/on-premises to add data to for long term processing, aggregation and tending.

- Petabyte-scale data warehousing
- Designed for analytics and reporting
- OLAP - Online Analytical Processing (Column based) not OLTP (row/tranactional)
- Pay as you use ... similar structure to RDS
- Direct Query S3 using Redshift Spectrum
- Direct Query other DBs using Redshift Federated Query
- Integrates with AWS tooling such as Quicksight
- SQL-like interface JDBC/ODBC connections

#### Redshift - Architecture

- Server based (not serverless)
- One AZ in a VPC - network cost/performance
- Leader Node - manages connections, query planning, optimisation
- Compute Nodes - store data, perform queries
- VPC Security, IAM Permissions, KMS at rest encryption, CW Monitoring
- Redshift Enhanced VPC Routing - VPC Networking

## Amazon QuickSight

QuickSight is a a BA/BI Visualisation and Dashboard tool which is capable of integrating with AWS and external data sources.

- Business Analytics and Intelligence tool (BA/BI)
- Visualisation and Dashboard tool
- Ad-hoc Analysis
- Discovery and Integration with AWS Data sources
- .. and works with external data sources

### QuickSight - Data Sources

- Athena, Aurora, RDS, Redshift, S3, Salesforce, Snowflake, SQL Server, TeraData
- S3, AWS IOT
- Jira, GitHub, Twitter, ServiceNow, Zendesk
- Microsoft SQL Server, MySQL, PostgreSQL, MariaDB, Oracle, IBM DB2, SAP HANA
- Apache Spark, Snowflake, Presto, Teradata, Cloudera, Databricks, Google BigQuery, IBM Netezza, Microsoft Azure SQL Data Warehouse, Microsoft Azure Synapse Analytics, Oracle Exadata, SAP HANA, Snowflake, Teradata

## Amazon Athena

Amazon Athena is an interactive query service that makes it easy to analyze data in Amazon S3 using standard SQL. Athena is serverless, so there is no infrastructure to manage, and you pay only for the queries that you run.

Athena is easy to use. Simply point to your data in Amazon S3, define the schema, and start querying using standard SQL. Most results are delivered within seconds. With Athena, there’s no need for complex ETL jobs to prepare your data for analysis.

- Serverless Interactive Querying Service
- Ad-hoc queries on data - pay only data consumed
- Schema on Read - table like translation of data
- Original data never changed - remains on S3
- Schema translates data => relational-like when read
- Output can be sent to other services - S3, QuickSight, Lambda, SNS, Kinesis, CloudWatch
- Supports standard formats of structured, semi-structured and unstructured data
- Source data is stored on S3
- Athena can directly read many AWS data formats such as CloudTrail, ELB, S3, VPC Flow Logs, CloudFront, Route 53
- Tables are defined in advance in a data catalog and data is projected through when read.
- It allows SQL like queries on data without transforming source data

### Athena - Use Cases

- Queries where loading/transformation is too slow
- Occasional / Ad-hoc queries on data in S3
- Serverless querying scenarios - cost conscious
- Querying AWS logs - VPC Flow Logs, CloudTrail, ELB, S3, CloudFront, Route 53
- AWS Glue Data Catalog - metadata store for Athena
- Web Server Logs, Application Logs, IoT Data, Clickstream Data, Data Lakes
- With Athena Federated Query .. other data sources can be queried

## AWS Systems Manager

Systems Manager uses an agent architecture to allow communications between the systems manager service and managed instances.

- View and control AWS and on-premises infrastructure.
- Agent based - installed on windows and Linux AWS AMI's
- Manage Inventory and Patch Assets
- Run commands and Manage Desired State
- Parameter Store ... configuration and secrets
- Session Manager - Securely connect to Ec2 instances .. even in private VPCs

### AWS Systems Manager - Run Command

Systems Manager Run Command is a foundational feature of Systems manager which allows for commands to be executed on managed instances at scale.

[AWS Systems Manager Documents](https://docs.aws.amazon.com/systems-manager/latest/userguide/documents.html)

- Run `Command documents` on managed instances
- No SSH/RDP Access required
- Instance, Tag or Resource Groups
- Command documents can be reused adn can have parameters
- Rate Control - Concurrency and Error Threshold
- Output Options - S3, CloudWatch Logs, SSM
- EventBridge - Events for Success, Failure, Cancelled

### AWS SSM Documents

An AWS Systems Manager document (SSM document) defines the actions that Systems Manager performs on your managed instances. Systems Manager includes more than 100 pre-configured documents that you can use by specifying parameters at runtime. Documents use JavaScript Object Notation (JSON) or YAML, and they include steps and parameters that you specify.

- JSON or YAML
- Stored in the SSM Document Store
- Ask for Parameters and include Steps
- Command Documents - Run Command, Maintenance Windows, State Manager
- Automation Documents - Runbooks, Remediation, Workflow
- Package Documents - Distribute Software, Install Software

### AWS Systems Manager - Patch Manager

Patch Manager, a capability of AWS Systems Manager, automates the process of patching managed instances with both security related and other types of updates.

- Patch Baselines - define rules for patching
- Patch Groups - define which instances to patch
- Maintenance Windows - define when to patch
- Run Command - execute the patching
- Concurrency and Error Thresholds - control patching
- Compliance Reporting - Patch Compliance

### AWS Systems Manager - Patch Manager Concepts

- Predinfined Patch Baselines - Various OS types (you can create your own)
- For Linux - AWS-[OS]-DefaultPatchBaseline, explicitly defined patches
- AWS-AmazonLinux2DefaultPatchBaseline
- AWS-UbuntuDefaultPatchBaseline
- Windows - AWS-WindowsDefaultPatchBaseline - Critical, Security, Definition, Feature, Update Rollups
- AWS-WindowsPredefinedPatchBaselineOS
- AWS-WindowsPredefinedPatchBaseline-OS-Applications - Microsoft, Adobe, Java, Chrome, Firefox, etc

## AWS Config

AWS Config is a service which records the configuration of resources over time (configuration items) into configuration histories.
All the information is stored regionally in an S3 config bucket.
AWS Config is capable of checking for compliance .. and generating notifications and events based on compliance.

- Record configuration changes over time on resources
- Auditing of changes, compliance with standards
- Does not prevent changes happening ... no protection
- Regional Service ... supports cross-region and account aggregation
- Changes can generate SNS notifications and near-realtime events via EventBridge and Lambda
