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
