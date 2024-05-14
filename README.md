# AWS-Certified-DevOps-Engineer

- [AWS-Certified-DevOps-Engineer](#aws-certified-devops-engineer)
  - [IAM, ACCOUNTS \& ORGANIZATIONS](#iam-accounts--organizations)
    - [IAM Identity Policies](#iam-identity-policies)
      - [IAM Identity Policy Elements](#iam-identity-policy-elements)
      - [IAM Identity Policy Evaluation](#iam-identity-policy-evaluation)
      - [IAM Identity Policy Types](#iam-identity-policy-types)
        - [AWS Managed Policies](#aws-managed-policies)
        - [Customer Managed Policies](#customer-managed-policies)
        - [Inline Policies](#inline-policies)
    - [IAM Users](#iam-users)
      - [Principal](#principal)
      - [Amazon Resource Name (ARN)](#amazon-resource-name-arn)
      - [IAM User limits](#iam-user-limits)
    - [IAM Groups](#iam-groups)
      - [IAM Group Limits](#iam-group-limits)
    - [IAM Roles](#iam-roles)
      - [IAM Role Types](#iam-role-types)
      - [Temporary Security Credentials](#temporary-security-credentials)
        - [sts:AssumeRole](#stsassumerole)
    - [Service-Linked Roles](#service-linked-roles)
      - [Service-Linked Role Pass Role](#service-linked-role-pass-role)
    - [AWS Organizations](#aws-organizations)
      - [AWS Organizations Terminology](#aws-organizations-terminology)
      - [AWS Organizations Consolidated Billing](#aws-organizations-consolidated-billing)
    - [Service Control Policies](#service-control-policies)
      - [SCPs Allow list vs Deny list](#scps-allow-list-vs-deny-list)
  - [CloudFormation](#cloudformation)
    - [CloudFormation Template](#cloudformation-template)
    - [CloudFormation Template Anatomy](#cloudformation-template-anatomy)
    - [Template Parameters and Pseudo Parameters](#template-parameters-and-pseudo-parameters)
    - [Cloudformation Intrinsic Functions](#cloudformation-intrinsic-functions)
    - [CloudFormation Mappings](#cloudformation-mappings)
    - [CloudFormation Outputs](#cloudformation-outputs)
    - [CloudFormation Conditions](#cloudformation-conditions)
    - [CloudFormation DependsOn](#cloudformation-dependson)
    - [CloudFormation WaitConditions, CreationPolicy, and cfn-signal](#cloudformation-waitconditions-creationpolicy-and-cfn-signal)
      - [CloudFormation Provisioning](#cloudformation-provisioning)
      - [CloudFormation Signal](#cloudformation-signal)
      - [CloudFormation CreationPolicy](#cloudformation-creationpolicy)
      - [CloudFormation WaitCondition](#cloudformation-waitcondition)
    - [CloudFormation Nested Stacks](#cloudformation-nested-stacks)
    - [Difference between Nested Stacks and Cross-Stack References](#difference-between-nested-stacks-and-cross-stack-references)
      - [Nested Stacks](#nested-stacks)
      - [Cross-Stack References](#cross-stack-references)
    - [CloudFormation StackSets](#cloudformation-stacksets)
      - [CFN StackSets - Terms](#cfn-stacksets---terms)
    - [CloudFormation DeletionPolicy](#cloudformation-deletionpolicy)
      - [Delete](#delete)
      - [Retain](#retain)
      - [Snapshot](#snapshot)
    - [CloudFormation Stack Roles](#cloudformation-stack-roles)
    - [CloudFormation CFN-Init](#cloudformation-cfn-init)
    - [CloudFormation cfn-hup](#cloudformation-cfn-hup)
    - [CloudFormation Change Sets](#cloudformation-change-sets)
    - [CloudFormation Custom Resources](#cloudformation-custom-resources)
  - [Elastic Beanstalk (EB)](#elastic-beanstalk-eb)
    - [Elastic Beanstalk (EB) - Platforms](#elastic-beanstalk-eb---platforms)
    - [Elastic Beanstalk (EB) - Deployment Options](#elastic-beanstalk-eb---deployment-options)
    - [Elastic Beanstalk (EB) - Lifecycle and RDS](#elastic-beanstalk-eb---lifecycle-and-rds)
    - [Elastic Beanstalk (EB) - Advanced Customisation via .ebextensions](#elastic-beanstalk-eb---advanced-customisation-via-ebextensions)
    - [Elastic Beanstalk (EB) - HTTPS](#elastic-beanstalk-eb---https)
    - [Elastic Beanstalk (EB) - Environment Cloning](#elastic-beanstalk-eb---environment-cloning)
    - [Elastic Beanstalk (EB) - Docker](#elastic-beanstalk-eb---docker)
  - [CloudWatch Events and EventBridge](#cloudwatch-events-and-eventbridge)
  - [Lambda](#lambda)
    - [Lambda - facts](#lambda---facts)
    - [Lambda - Common Use Cases](#lambda---common-use-cases)
    - [Lambda - Networking Public](#lambda---networking-public)
    - [Lambda - Networking VPC](#lambda---networking-vpc)
    - [Lambda - Security](#lambda---security)
    - [AWS Lambda - Logging](#aws-lambda---logging)
    - [Lambda - Invocation Types](#lambda---invocation-types)
      - [Synchronous](#synchronous)
      - [Asynchronous](#asynchronous)
      - [Event Source Mappings](#event-source-mappings)
      - [Lambda Destinations](#lambda-destinations)
    - [Lambda - Versions](#lambda---versions)
    - [Lambda - Function Handler](#lambda---function-handler)
      - [Lambda - Function Handler - Phases](#lambda---function-handler---phases)
    - [Lambda - Versions and Aliases](#lambda---versions-and-aliases)
    - [Lambda - Aliases](#lambda---aliases)
    - [Lambda - Environment Variables](#lambda---environment-variables)
    - [Lambda - Monitoring, Logging and Tracing](#lambda---monitoring-logging-and-tracing)
    - [Lambda - Logging](#lambda---logging)
    - [Lambda - Tracing](#lambda---tracing)
    - [Lambda - Layers](#lambda---layers)
    - [Lambda - Container Images](#lambda---container-images)
    - [Lambda - ALB Integration](#lambda---alb-integration)
    - [Lambda - Resource Policies](#lambda---resource-policies)
  - [API Gateway](#api-gateway)
    - [API Gateway - Endpoint Types](#api-gateway---endpoint-types)
    - [API Gateway - Stages](#api-gateway---stages)
    - [API Gateway - Errors](#api-gateway---errors)
    - [API Gateway - Caching](#api-gateway---caching)
    - [API Gateway - Methods and Resources](#api-gateway---methods-and-resources)
    - [API Gateway - Integration Types](#api-gateway---integration-types)
    - [API Gateway - Mapping Templates](#api-gateway---mapping-templates)
    - [API Gateway - Stages and Deployments](#api-gateway---stages-and-deployments)
    - [API Gateway - Swagger and OpenAPI](#api-gateway---swagger-and-openapi)
  - [Simple Notification Service (SNS)](#simple-notification-service-sns)
  - [Simple Queue Service (SQS)](#simple-queue-service-sqs)
    - [SQS - Standard Queue](#sqs---standard-queue)
    - [SQS - FIFO Queue](#sqs---fifo-queue)
    - [SQS - Extended Client Library](#sqs---extended-client-library)
    - [SQS - Delay Queues](#sqs---delay-queues)
    - [SQS - Dead Letter Queues](#sqs---dead-letter-queues)
  - [Step Functions](#step-functions)
    - [Step Functions - State Machines](#step-functions---state-machines)
    - [Step Functions - States](#step-functions---states)
  - [Elastic Container Service (ECS)](#elastic-container-service-ecs)
    - [ECS Concepts](#ecs-concepts)
    - [ECS - Cluster Types](#ecs---cluster-types)
      - [EC2 Mode](#ec2-mode)
      - [Fargate Mode](#fargate-mode)
  - [Kubernetes (EKS)](#kubernetes-eks)
    - [Kubernetes Cluster Structure](#kubernetes-cluster-structure)
    - [Elastic Kubernetes - EKS](#elastic-kubernetes---eks)
  - [AWS OpsWorks](#aws-opsworks)
    - [OpsWorks - Stacks](#opsworks---stacks)
  - [SSM - Parameter Store](#ssm---parameter-store)
  - [SSM - Secrets Manager](#ssm---secrets-manager)
  - [Security Token Service (STS)](#security-token-service-sts)
    - [STS - How it works](#sts---how-it-works)
  - [Policy Interpretation Deep Dive - Example 1](#policy-interpretation-deep-dive---example-1)
  - [Policy Interpretation Deep Dive - Example 2](#policy-interpretation-deep-dive---example-2)
  - [Policy Interpretation Deep Dive - Example 3](#policy-interpretation-deep-dive---example-3)
  - [Permission Boundaries](#permission-boundaries)
  - [Policy Evaluation Logic](#policy-evaluation-logic)
  - [Route 53 Fundamentals](#route-53-fundamentals)
    - [Route 53 - Hosted Zones](#route-53---hosted-zones)
    - [Route 53 - Record Sets](#route-53---record-sets)
    - [Route 53 - Public Hosted Zones](#route-53---public-hosted-zones)
    - [Route 53 - Private Hosted Zones](#route-53---private-hosted-zones)
    - [Route 53 - CNAME vs Alias](#route-53---cname-vs-alias)
      - [CNAME](#cname)
      - [Alias](#alias)
    - [Route 53 - Routing Policies](#route-53---routing-policies)
      - [Simple Routing](#simple-routing)
      - [Failover Routing](#failover-routing)
      - [Multi Value Routing](#multi-value-routing)
      - [Weighted Routing](#weighted-routing)
      - [Latency Based Routing](#latency-based-routing)
      - [Geolocation Routing](#geolocation-routing)
      - [Geo Proximity Routing](#geo-proximity-routing)
    - [Route 53 - Health Checks](#route-53---health-checks)
    - [Route 53 - Interoperability](#route-53---interoperability)
  - [SDLC AUTOMATION](#sdlc-automation)
    - [CodePipeline](#codepipeline)
    - [CodeBuild](#codebuild)
    - [CodeDeploy](#codedeploy)
    - [Elastic Container Registry (ECR)](#elastic-container-registry-ecr)
  - [CloudWatch](#cloudwatch)
    - [CloudWatch - Data](#cloudwatch---data)
    - [CloudWatch - Alarms](#cloudwatch---alarms)
    - [CloudWatch - Logs](#cloudwatch---logs)
      - [CloudWatch Logs - Ingestion](#cloudwatch-logs---ingestion)
    - [CloudTrail Essentials](#cloudtrail-essentials)
  - [Amazon Kinesis Data Streams](#amazon-kinesis-data-streams)
    - [Kinesis Data Streams SQS vs Kinesis](#kinesis-data-streams-sqs-vs-kinesis)
    - [Amazon Kinesis Data Firehose](#amazon-kinesis-data-firehose)
    - [Amazon Kinesis Data Analytics](#amazon-kinesis-data-analytics)
  - [AWS MapReduce](#aws-mapreduce)
    - [HDFS - Hadoop Distributed File System](#hdfs---hadoop-distributed-file-system)
    - [Elastic Map Reduce](#elastic-map-reduce)
    - [Amazon Redshift (Data Warehouse)](#amazon-redshift-data-warehouse)
      - [Redshift - Architecture](#redshift---architecture)
  - [Amazon QuickSight](#amazon-quicksight)
    - [QuickSight - Data Sources](#quicksight---data-sources)
  - [Amazon Athena](#amazon-athena)
    - [Athena - Use Cases](#athena---use-cases)
  - [AWS Systems Manager](#aws-systems-manager)
    - [AWS Systems Manager - Run Command](#aws-systems-manager---run-command)
    - [AWS SSM Documents](#aws-ssm-documents)
    - [AWS Systems Manager - Patch Manager](#aws-systems-manager---patch-manager)
    - [AWS Systems Manager - Patch Manager Concepts](#aws-systems-manager---patch-manager-concepts)
  - [AWS Config](#aws-config)
  - [AWS Service Catalog](#aws-service-catalog)
  - [Amazon Inspector](#amazon-inspector)
  - [Amazon GuardDuty](#amazon-guardduty)
  - [AWS Trusted Advisor](#aws-trusted-advisor)
    - [AWS Trusted Advisor - Core Checks (Basic/Developer)](#aws-trusted-advisor---core-checks-basicdeveloper)
    - [AWS Trusted Advisor - Core Checks (Business/Enterprise)](#aws-trusted-advisor---core-checks-businessenterprise)
  - [STORAGE](#storage)
    - [Elastic Block Store (EBS)](#elastic-block-store-ebs)
      - [EBS - Volume Types General Purpose SSD (gp2)](#ebs---volume-types-general-purpose-ssd-gp2)
      - [EBS - Volume Types General Purpose SSD (gp3)](#ebs---volume-types-general-purpose-ssd-gp3)
      - [EBS - Volume Types Provisioned IOPS SSD (io1/2)](#ebs---volume-types-provisioned-iops-ssd-io12)
      - [EBS - Volume Types Throughput Optimised HDD (st1/sc1)](#ebs---volume-types-throughput-optimised-hdd-st1sc1)
        - [Throughput Optimised HDD st1](#throughput-optimised-hdd-st1)
        - [Cold HDD sc1](#cold-hdd-sc1)
    - [Instance Store](#instance-store)
      - [Instance Store - Volume Types](#instance-store---volume-types)
    - [Storage Gateway - Volume Gateway](#storage-gateway---volume-gateway)
      - [Volume Gateway - Stored Volumes](#volume-gateway---stored-volumes)
      - [Volume Gateway - Cached Volumes](#volume-gateway---cached-volumes)
    - [Storage Gateway - Tape Gateway - Virtual Tape Library (VTL)](#storage-gateway---tape-gateway---virtual-tape-library-vtl)
    - [Storage Gateway - File Gateway - File Mode](#storage-gateway---file-gateway---file-mode)
  - [S3 Security (Resource Policies \& ACLs)](#s3-security-resource-policies--acls)
    - [S3 - Bucket Policies](#s3---bucket-policies)
    - [S3 - Bucket Policy Example](#s3---bucket-policy-example)
    - [S3 - Access Control Lists(ACLs)](#s3---access-control-listsacls)
    - [Block Public Access](#block-public-access)
  - [S3 Static Website Hosting](#s3-static-website-hosting)
    - [S3 - Static Website Hosting - Offloading](#s3---static-website-hosting---offloading)
    - [S3 - Static Website Hosting - Out-of-band pages](#s3---static-website-hosting---out-of-band-pages)
    - [S3 - Object Versioning \& MFA Delete](#s3---object-versioning--mfa-delete)
    - [S3 - MFA Delete](#s3---mfa-delete)
    - [S3 - Performance Optimisation](#s3---performance-optimisation)
      - [Single PUT Upload](#single-put-upload)
      - [Multipart Upload](#multipart-upload)
      - [S3 Accelerated Transfer (S3 Transfer Acceleration)](#s3-accelerated-transfer-s3-transfer-acceleration)
  - [AWS Key Management Service (KMS)](#aws-key-management-service-kms)
    - [KMS Keys](#kms-keys)
    - [KMS - Data Encryption Keys (DEK)](#kms---data-encryption-keys-dek)
    - [KMS - Key Concepts](#kms---key-concepts)
    - [KMS - Key Policies and Security](#kms---key-policies-and-security)
  - [S3 Object Encryption CSE/SSE](#s3-object-encryption-csesse)
    - [S3 - Client Side Encryption (CSE)](#s3---client-side-encryption-cse)
    - [S3 - Server Side Encryption (SSE)](#s3---server-side-encryption-sse)
      - [S3 - Server Side Encryption with Customer Provided Keys (SSE-C)](#s3---server-side-encryption-with-customer-provided-keys-sse-c)
      - [S3 - Server Side Encryption with S3 Managed Keys (SSE-S3 AES256) (Default)](#s3---server-side-encryption-with-s3-managed-keys-sse-s3-aes256-default)
      - [S3 - Server Side Encryption with KMS Managed Keys (SSE-KMS)](#s3---server-side-encryption-with-kms-managed-keys-sse-kms)
  - [S3 - Bucket Keys](#s3---bucket-keys)
    - [Without Bucket Keys](#without-bucket-keys)
    - [With Bucket Keys](#with-bucket-keys)
      - [S3 - Bucket Keys - things to remember](#s3---bucket-keys---things-to-remember)
  - [S3 - Object Storage Classes](#s3---object-storage-classes)
    - [S3 - Standard](#s3---standard)
    - [S3 - Standard-IA (Infrequent Access)](#s3---standard-ia-infrequent-access)
    - [S3 - One Zone-IA (Infrequent Access)](#s3---one-zone-ia-infrequent-access)
    - [S3 - S3 Glacier - Instant Retrieval](#s3---s3-glacier---instant-retrieval)
    - [S3 - Glacier - Flexible Retrieval](#s3---glacier---flexible-retrieval)
    - [S3 - Glacier Deep Archive](#s3---glacier-deep-archive)
    - [S3 - Intelligent Tiering](#s3---intelligent-tiering)
  - [S3 Lifecycle Configuration](#s3-lifecycle-configuration)
    - [S3 - Lifecycle Configuration - Transition Actions](#s3---lifecycle-configuration---transition-actions)
  - [S3 Replication](#s3-replication)
    - [S3 - Replication - Cross Region Replication (CRR)](#s3---replication---cross-region-replication-crr)
    - [S3 - Replication - Same Region Replication (SRR)](#s3---replication---same-region-replication-srr)
      - [S3 - Replication Options](#s3---replication-options)
      - [S3 - Replication Considerations](#s3---replication-considerations)
      - [S3 - Replication - Why use replication?](#s3---replication---why-use-replication)
  - [S3 Pre-Signed URLs](#s3-pre-signed-urls)
  - [S3 Select and Glacier Select](#s3-select-and-glacier-select)
    - [S3 Select and Glacier Select - How it works](#s3-select-and-glacier-select---how-it-works)
  - [Cross-Origin Resource Sharing (CORS)](#cross-origin-resource-sharing-cors)
  - [S3 Event Notifications](#s3-event-notifications)
  - [S3 Access Logs](#s3-access-logs)
  - [S3 Object Lock](#s3-object-lock)
    - [S3 Object Lock - Retention Period](#s3-object-lock---retention-period)
    - [S3 Object Lock - Legal Hold](#s3-object-lock---legal-hold)
  - [S3 Access Points](#s3-access-points)
  - [S3 Inventory](#s3-inventory)
  - [Elastic File System (EFS)](#elastic-file-system-efs)
  - [FSx for Windows File Server](#fsx-for-windows-file-server)
    - [FSx for Windows File Server - Features and Benefits](#fsx-for-windows-file-server---features-and-benefits)
  - [FSx for Lustre](#fsx-for-lustre)
    - [FSx for Lustre - Information](#fsx-for-lustre---information)
    - [FSx for Lustre - Scratch](#fsx-for-lustre---scratch)
  - [CloudFront](#cloudfront)
    - [CloudFront - Behaviours](#cloudfront---behaviours)
    - [CloudFront - TTL](#cloudfront---ttl)
    - [CloudFront - Invalidations](#cloudfront---invalidations)
  - [AWS Certificate Manager (ACM)](#aws-certificate-manager-acm)
  - [CloudFront and SSL](#cloudfront-and-ssl)
  - [CloudFront - Origin Types and Origin Architecture](#cloudfront---origin-types-and-origin-architecture)
  - [CloudFront - Security](#cloudfront---security)
    - [CloudFront - Origin Access Identity (OAI) - S3 Origins](#cloudfront---origin-access-identity-oai---s3-origins)
    - [CloudFront - Origin Access Identity (OAI) - Custom Origins](#cloudfront---origin-access-identity-oai---custom-origins)
    - [CloudFront - Private Distributions](#cloudfront---private-distributions)
    - [CloudFront - Signed URLs and Signed Cookies](#cloudfront---signed-urls-and-signed-cookies)
  - [CloudFront - Geo Restriction](#cloudfront---geo-restriction)
    - [CloudFront - Geo Restriction - White List / Black List](#cloudfront---geo-restriction---white-list--black-list)
    - [CloudFront - 3rd Party Geolocation](#cloudfront---3rd-party-geolocation)
  - [CloudFront - Lambda@Edge](#cloudfront---lambdaedge)
    - [CloudFront - Lambda@Edge - Use Cases](#cloudfront---lambdaedge---use-cases)
  - [Amazon DynamoDB](#amazon-dynamodb)
    - [DynamoDB - Tables](#dynamodb---tables)
    - [DynamoDB - On-Demand Backups](#dynamodb---on-demand-backups)
    - [DynamoDB - Reading and Writing](#dynamodb---reading-and-writing)
    - [DynamoDB - Query](#dynamodb---query)
    - [DynamoDB - Scan](#dynamodb---scan)
    - [DynamoDB - Consistency Model](#dynamodb---consistency-model)
    - [DynamoDB - Indexes (LSI and GSI)](#dynamodb---indexes-lsi-and-gsi)
      - [DynamoDB - LSI](#dynamodb---lsi)
      - [DynamoDB - GSI](#dynamodb---gsi)
      - [DynamoDB - Considertions](#dynamodb---considertions)
  - [DynamoDB - Streams and Triggers](#dynamodb---streams-and-triggers)
    - [DynamoDB - Trigger Concepts](#dynamodb---trigger-concepts)
  - [DynamoDB - Accelerator (DAX)](#dynamodb---accelerator-dax)
    - [Traditional Cache](#traditional-cache)
    - [DAX SDK](#dax-sdk)
    - [DAX Architecture](#dax-architecture)
      - [DAX Considerations](#dax-considerations)
  - [DynamoDB Global Tables](#dynamodb-global-tables)
  - [DynamoDB TTL](#dynamodb-ttl)
  - [High Availability vs Fault Tolerance vs Disaster Recovery](#high-availability-vs-fault-tolerance-vs-disaster-recovery)
    - [High Availability](#high-availability)
    - [Fault Tolerance](#fault-tolerance)
    - [Disaster Recovery](#disaster-recovery)
  - [Disaster Recovery / Business Continuity](#disaster-recovery--business-continuity)
    - [Disaster Recovery / Business Continuity - Types](#disaster-recovery--business-continuity---types)
      - [Backup and Restore](#backup-and-restore)
      - [Pilot Light](#pilot-light)
      - [Warm Standby](#warm-standby)
      - [Multi-Site Active/Active](#multi-site-activeactive)
    - [Disaster Recovery / Business Continuity - Considerations](#disaster-recovery--business-continuity---considerations)
      - [Disaster Recovery Storage](#disaster-recovery-storage)
        - [DR - Instance Store](#dr---instance-store)
        - [DR - EBS](#dr---ebs)
        - [DR - S3](#dr---s3)
        - [DR - EFS](#dr---efs)
        - [DR - S3 Snapshot Copy](#dr---s3-snapshot-copy)
      - [Disaster Recovery - Compute](#disaster-recovery---compute)
        - [DR - EC2](#dr---ec2)
        - [DR - ECS](#dr---ecs)
        - [DR - Lambda](#dr---lambda)
      - [Disaster Recovery - Databases](#disaster-recovery---databases)
        - [DR - RDS](#dr---rds)
        - [DR - Aurora](#dr---aurora)
        - [DR - DynamoDB](#dr---dynamodb)
      - [Disaster Recovery - Networking](#disaster-recovery---networking)
        - [DR - VPC](#dr---vpc)
  - [EC2 - Launch Configurations and Launch Templates](#ec2---launch-configurations-and-launch-templates)
  - [EC2 - Auto Scaling Groups](#ec2---auto-scaling-groups)
    - [Auto Scaling - Scaling Policies](#auto-scaling---scaling-policies)
    - [ASG + Load Balancer](#asg--load-balancer)
    - [Scaling Processes](#scaling-processes)
    - [ASG - Scaling Policies](#asg---scaling-policies)
    - [ASG - Lifecycle Hooks](#asg---lifecycle-hooks)
    - [ASG - Health Checks](#asg---health-checks)
  - [Elastic Load Balancer (ELB)](#elastic-load-balancer-elb)
    - [Elastic Load Balancer Architecture (ELB)](#elastic-load-balancer-architecture-elb)
      - [IMPORTANT](#important)
    - [Elastic Load Balancer Architecture - Three Tier Architecture (Web, Worker, Database)](#elastic-load-balancer-architecture---three-tier-architecture-web-worker-database)
    - [Elastic Load Balancer - Cross Zone Load Balancing](#elastic-load-balancer---cross-zone-load-balancing)
    - [Application and Network Load Balancer (ALB vs NLB)](#application-and-network-load-balancer-alb-vs-nlb)
      - [Load Balancer Consolidation](#load-balancer-consolidation)
      - [Application Load Balancer (ALB)](#application-load-balancer-alb)
      - [Application Load Balancer - Rules](#application-load-balancer---rules)
      - [Network Load Balancer (NLB)](#network-load-balancer-nlb)
      - [ALB vs NLB](#alb-vs-nlb)
  - [User Sessoin State](#user-sessoin-state)
    - [User Session State - Session Stickiness](#user-session-state---session-stickiness)
      - [Stickiness Key Points](#stickiness-key-points)
  - [Gateway Load Balancer (GWLB)](#gateway-load-balancer-gwlb)
    - [Why do we need a GWLB?](#why-do-we-need-a-gwlb)
    - [Gateway Load Balancer - what is it?](#gateway-load-balancer---what-is-it)
    - [Gateway Load Balancer - how it works](#gateway-load-balancer---how-it-works)
  - [Devops Security](#devops-security)
    - [Web Application Firewall (WAF)](#web-application-firewall-waf)
    - [Web Access Control Lists (WEBACL)](#web-access-control-lists-webacl)
    - [Rule groups](#rule-groups)
    - [WAF Rules](#waf-rules)
    - [WAF Pricing](#waf-pricing)
  - [AWS Network Firewall](#aws-network-firewall)
    - [AWS Network Firewall - Components](#aws-network-firewall---components)
    - [AWS Network Firewall - Rule Groups](#aws-network-firewall---rule-groups)
      - [AWS Network Firewall - Stateless](#aws-network-firewall---stateless)
      - [AWS Network Firewall - Stateful](#aws-network-firewall---stateful)
  - [Connection Draining](#connection-draining)
  - [Deregistration Delay](#deregistration-delay)
  - [X-Forwarded-For and PROXY Protocol](#x-forwarded-for-and-proxy-protocol)
    - [X-Forwarded-For](#x-forwarded-for)
    - [PROXY Protocol](#proxy-protocol)
  - [Question Technique](#question-technique)
    - [Keyword Identification](#keyword-identification)
      - [Question 1](#question-1)
      - [Answers 1](#answers-1)
      - [Question 2](#question-2)
      - [Answers 2](#answers-2)

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

## AWS Service Catalog

AWS Service Catalog is an AWS implementation of a Service Catalog system,
It provides an end-user portal where products and portfolios can be deployed in a self-service way as defined by technical administrators.

- Document or Database created by an IT team
- Organised collection of products
- Offered by the IT Team
- Key Product Information: Product Owner, Cost Requirements, Dependencies, Constraints, Support Information
- Defines approval of provisioning from IT and Customer side
- Manage costs and scale service delivery
- Self-Service Portal for 'end users'
- ..launch predefined (by admin) products
- End user permissions can be controlled
- Admins can define those products...
- ..and the permissoins required to launch them
- Build products into portfolios

## Amazon Inspector

Amazon Inspector is an automated security assessment service that helps improve the security and compliance of applications deployed on AWS. Amazon Inspector automatically assesses applications for exposure, vulnerabilities, and deviations from best practices.

- Scans EC2 instances and the instances OS
- Also containers and applications
- Vulnerabilities and deviations against best practice
- Length 15mins, 1 hour, 24 hours
- Provides a report of findings ordered by priority
- Network Assessment (Agentless) - EC2, VPC, Subnets, Security Groups, NACLs
- Network and Host Assessment (Agent Based) - EC2, OS, Applications
- Rules packages determine what is checked
- Network Reachability (Agentless) - EC2, VPC, Subnets, Security Groups, NACLs
- Agent can provide additional OS visibility
- Check reachability end to end. EC2, VPC, Subnets, Security Groups, NACLs, VPC Peering, IGW, ACLs, Route Tables
- RecongnizedPortWithListener, RecongnizedPortNoListener, RecongnizedPortNoAgent
- UnrecongizedPortWithListener, UnrecongizedPortNoListener, UnrecongizedPortNoAgent
- Packages (.. Host Assessments, Agent required)
- Common vulnerabilities and exposures (CVE)
- Center for Internet Security (CIS) Benchmarks
- Security Best Practices for Amazon Inspector

## Amazon GuardDuty

Amazon GuardDuty is a threat detection service that continuously monitors for malicious activity and unauthorized behavior to protect your AWS accounts and workloads.

- Continuous Monitoring for malicious activity
- Analyses supported Data Sources - VPC Flow Logs, CloudTrail, DNS Logs
- Uses Machine Learning to detect anomalies, plus threat intelligence feeds
- Identifies unexpected and unauthorized behaviour
- Generates Findings - High, Medium, Low
- Notify or Event driven protection/remediation
- Supports multiple accounts (master/member)

## AWS Trusted Advisor

AWS Trusted Advisor is an online tool that provides you real time guidance to help you provision your resources following AWS best practices.
Trusted Advisor checks help optimize your AWS infrastructure, increase security and performance, reduce your overall costs, and monitor service limits.

- Account level - no agents to install
- Cost Optimisation, Performance, Security, Fault Tolerance, Service Limits
- 7 Core checks with basic and developer support plans
- Anything beyond requires Business or Enterprise support

### AWS Trusted Advisor - Core Checks (Basic/Developer)

- S3 Bucket Permissions - Public Read, Public Write, Cross Account Access
- Security Groups - Unrestricted Access, Specific Ports, Specific IPs
- IAM Use - Access Keys, MFA, Root Account Use
- MFA on Root Account - Not Enabled
- EBS Public Snapshots - Public Snapshots
- RDS Public Snapshots - Public Snapshots
- Service Limits - EC2, EBS, VPC, RDS, Route 53, SES, Lambda, etc

### AWS Trusted Advisor - Core Checks (Business/Enterprise)

- Core 7 checks plus additional checks
- 115 Further checks (14 cost, 17 security, 24 fault tolerance, 10 performance, 50 service limits)
- Access via the AWS Support API
- CloudWatch Integration - react to changes

## STORAGE

### Elastic Block Store (EBS)

Amazon Elastic Block Store (Amazon EBS) provides block level storage volumes for use with EC2 instances. EBS volumes behave like raw, unformatted block devices. You can mount these volumes as devices on your instances. EBS volumes that are attached to an instance are exposed as storage volumes that persist independently from the life of the instance. You can create a file system on top of these volumes, or use them in any way you would use a block device (such as a hard drive).

- Block Storage - raw disk allocations (volume) for EC2 instances
- Can be encrypted at rest using KMS
- instances see block device and create file system on this device (ext3/4, xfs)
- Storage is provisioned in ONE AZ (Resilient in that AZ)
- Attached to one EC2 instance (or other service) over a storage network (See Multi-Attach)
- Detached and reattached, not lifecycle linked to one instance .. persistent
- Snapshot (backup) into S3. Create volume from snapshot (migrate between AZs)
- Different physical storage types, different sizes, different performance profiles
- Billed based on GB-month (and in some cases performance)

#### EBS - Volume Types General Purpose SSD (gp2)

- General Purpose SSD (gp2)
- 3 IOPS per GB, 3000 IOPS max, 16TB max, 1GB-16TB, 1GB increments
- Burst to 3000 IOPS, 99.9% of the time 3 IOPS per GB
- An IOPS is a measure of performance (Input/Output Operations Per Second)
- An IO Credit is 16KB IOPS assume 16KB, 1 IOPS is 1 IO in 1 second
- IO `Credit` Bucket Capacity - 5.4 million IOs Credits, Fills at rate of Baseline Performance
- Bucket fills with min 100 IO Credits per second, regardless of volume size
- Beyond the 100 minimum the bucket fills with 3 IO credits per second per GB of volume size (Baseline Performance)
- Burst up to 3000 IOPS by depleting the bucket
- All volumes get an initial 5.4 million IO credits. 30 minutes @ 3000 IOPS. Greate for boots and initial workloads

#### EBS - Volume Types General Purpose SSD (gp3)

- General Purpose SSD (gp3) - 3000 IOPS, 16TB max, 1GB-16TB, 1GB increments
- 3000 IOPS, 125MB/s, 16TB max, 1GB-16TB, 1GB increments
- Baseline Performance - 3000 IOPS, 125MB/s
- More economical than gp2

#### EBS - Volume Types Provisioned IOPS SSD (io1/2)

- Provisioned IOPS SSD (io1/io2)
- With io1/io2 BlockExpress IOPS can be adjusted independently of volume size
- Consistent Low latency and jitter
- Up to 64,000 IOPS, 1000MB/s, 16TB max, 4GB-16TB, 4GB increments
- Up to 256,000 IOPS, 4000MB/s, 64TB max, 4GB-64TB, 4GB increments with BlockExpress
- io1 50 IOPS per GB, io2 500 IOPS per GB
- BlockExpress 1000 IOPS per GB

#### EBS - Volume Types Throughput Optimised HDD (st1/sc1)

##### Throughput Optimised HDD st1

- A low-cost HDD designed for frequently accessed, throughput-intensive workloads.
- 125 GB - 16 TB
- Max IOPS 500
- Max Throughput 500 MB/s
- Baseline Throughput 40 MB/s per TB
- Burst to 250 MB/s
- Big data, Data Warehousing, Log Processing

##### Cold HDD sc1

- A low-cost HDD designed for less frequently accessed workloads.
- Max IOPS 250
- 125 GB - 16 TB
- Max Throughput 250 MB/s
- Baseline Throughput 12 MB/s per TB
- Burst to 80 MB/s
- Scenarios where the lowest storage cost is important
- File Servers, Infrequently accessed workloads

### Instance Store

An instance store provides temporary block-level storage for your instance. This storage is located on disks that are physically attached to the host computer. Instance store is ideal for temporary storage of information that changes frequently, such as buffers, caches, scratch data, and other temporary content, or for data that is replicated across a fleet of instances, such as a load-balanced pool of web servers.

An instance store consists of one or more instance store volumes exposed as block devices. The size of an instance store as well as the number of devices available varies by instance type.

The virtual devices for instance store volumes are ephemeral[0-23]. Instance types that support one instance store volume have ephemeral0. Instance types that support two instance store volumes have ephemeral0 and ephemeral1, and so on.

- Block Storage Devices
- Physical Disks attached to an EC2 instance
- Instances on that host can access them
- Highest storage performance in AWS
- Included in instance price
- Attached at launch time

#### Instance Store - Volume Types

- D3 = 4.6 GB/s throughput
- I3 = 16 GB/s throughput
- More IOPS and Throughput than EBS
- Local on EC2 Host
- Add at launch time ONLY
- Lost on instance move, resize or hardware failure
- High Performance, Low Latency, Temporary Storage

### Storage Gateway - Volume Gateway

Storage gateway is a product which integrates local infrastructure and AWS storage such as S3, EBS Snapshots and Glacier.

- Virtual machine or hardware appliance
- Presents storage using iSCSI protocol, NFS or SMB
- Integrates with S3, Glacier, EBS Snapshots
- Migrations, Extensions, Storage Tiering, DR and Replacement of backup systems

#### Volume Gateway - Stored Volumes

- Entire dataset is stored on site and asynchronously backed up to S3
- Low latency access to the entire dataset
- Data is stored in S3 as EBS snapshots
- 1GB - 16TB volumes
- 32 volumes per gateway
- 512TB per gateway
- All data is stored on site, S3 is backup
- Doesn't improve datacenter storage capacity
- Main copy of data is stored on the gateway

#### Volume Gateway - Cached Volumes

- Entire dataset is stored in S3 and the most frequently accessed data is cached on site
- Low latency access to the most frequently accessed data
- 1GB - 32TB volumes
- 32 volumes per gateway
- 1PB per gateway
- All data is stored in S3, cache is on site
- Improves datacenter storage capacity
- Storage appears on-premises, but is stored in S3

### Storage Gateway - Tape Gateway - Virtual Tape Library (VTL)

Storage gateway in VTL mode allows the product to replace a tape based backup solution with one which uses S3 and Glacier rather than physical tape media.

- Large backups => tape backups
- LTO-9 Media can hold 24TB of raw data
- Up to 60TB compressed
- 1 Tape Drive can use 1 tape at a time
- Loaders (robotics) can hold multiple tapes
- A Library is 1+ drives, 1+ slots and loaders
- Drive ... library ... shelf (anywhere but the library)

### Storage Gateway - File Gateway - File Mode

File gateway bridges local file storage over NFS and SMB with S3 Storage
It supports multi site, maintains storage structure, integrates with other AWS products and supports S3 object lifecycle Management

[NotifyWhenUploaded](https://docs.aws.amazon.com/storagegateway/latest/APIReference/API_NotifyWhenUploaded.html)

- Bridges on-premises file storage with S3
- Mount Points(shares) available over NFS and SMB
- Map directly onto an S3 bucket
- Files stored into a mount point, are visible as objects in an S3 bucket
- Read and Write Caching ensure LAN-like performance
- File Gateway doesn't support Object Locking- use read only mode on other shares or tightly control file access

## S3 Security (Resource Policies & ACLs)

S3 Security is controlled via a combination of Identity Policies, Bucket Policies (Resource Policies) and Legacy Bucket and Object ACLs

- S3 is private by default

### S3 - Bucket Policies

- A form of resource policy
- Like identity policies, but attached to a bucket
- Resource perspective permissons
- ALLOW/DENY same or different accounts
- ALLOW/DENY Anonymous principals

### S3 - Bucket Policy Example

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::mybucket/*"
    }
  ]
}
```

### S3 - Access Control Lists(ACLs)

- ACLs on objects and buckets
- A subresource
- Legacy - use Bucket Policies instead
- Inflexible and only allow basic permissions

### Block Public Access

- Block Public Access is a setting on a bucket
- Blocks all public access to the bucket
- Overrides any public access settings on objects

## S3 Static Website Hosting

S3 can be used to host static websites, this is a cost effective way to host a website with low traffic.

- Normal access is via AWS APIs
- This feature allows access via HTTP/HTTPS
- Index and Error documents can be set
- Website endpoint is in the format `bucketname.s3-website-region.amazonaws.com`
- Custom domain via Route 53 or CloudFront

[Amazon S3 pricing](https://aws.amazon.com/s3/pricing/)

### S3 - Static Website Hosting - Offloading

- Offload static content from web servers
- Reduce load on web servers
- Reduce latency for users
- Reduce costs for serving static content
- Use CloudFront for global distribution
- Use S3 for storage

### S3 - Static Website Hosting - Out-of-band pages

- Out-of-band pages - 404, 403, 500
- Custom error pages
- Use case - maintenance, error, compliance

### S3 - Object Versioning & MFA Delete

Object versioning is a feature which can be enabled on an S3 bucket - allowing the bucket to store multi versions of objects
These objects can be referenced by their version ID to interact directly - or omit this to reference the latest version of an object
Objects aren't deleted - object deletion markers are put in place to hide objects.

Versioning lets you store multiple versions of objects within a bucket. Operations which would modify objects generate a new version.

- cannot be disabled once enabled - only suspended
- Space is consumed by ALL versions
- You are billed for All versions
- Only way to 0 costs - is to delete the bucket

### S3 - MFA Delete

- Enabled in versioning configuration
- MFA is required to change bucket versioning state
- MFA is required to delete versions of objects
- Serial number (MFA) + Code passed with API Calls

### S3 - Performance Optimisation

#### Single PUT Upload

- Single data stream to S3
- Stream fails - entire upload fails
- Retry entire upload
- Speed and reliability = limit of 1 stream
- Any upload up to 5GB

#### Multipart Upload

- Data is split into parts
- Min data size 100MB for multipart
- 10000 parts max, 5MB -> 5GB
- Last part can be smaller than 5MB
- Parts can fail, and be restarted
- Transfer rate = speeds of all parts

#### S3 Accelerated Transfer (S3 Transfer Acceleration)

- Use of CloudFront Edge Locations
- Speeds up uploads to S3

## AWS Key Management Service (KMS)

AWS Key Management Service (AWS KMS) makes it easy for you to create and manage cryptographic keys and control their use across a wide range of AWS services and in your applications. AWS KMS is a secure and resilient service that uses hardware security modules that have been validated under FIPS 140-2, or are in the process of being validated, to protect your keys.

- Regional and Public Service
- Create, Store and Manage Keys
- **Symmetric** and **Asymmetric** Keys
- Cryptographic Operations - Encrypt, Decrypt, Sign, Verify
- Keys never leave KMS - Provides FIPS 140-2 Level 2

### KMS Keys

- KMS Keys are logical - ID, date, policy, description
- Backed by physical key material
- Generated or Imported
- KMS Keys can be used for up to 4KB of data

### KMS - Data Encryption Keys (DEK)

- GenerateDataKey - works on > 4KB
- Plaintext Version
- Ciphertext Version
- Plaintext Version is used to encrypt data
- Discard Plaintext Version
- Store Ciphertext Version with data

### KMS - Key Concepts

- KMS Keys are isolated to a region and never leave
- Multi-region keys are possible
- AWS Owned Keys - Customer Owned
- With Customer Owned Keys AWS Managed or Customer Managed Keys
- Customer managed keys are more configurable
- KMS Keys can be rotated
- Backing Key (and previous backing keys)
- Aliases - friendly names for keys

### KMS - Key Policies and Security

- Key Policies - IAM like policies for keys
- Every Key has one
- Key Policies + IAM Policies = Access Control
- Key Policies + Grants

## S3 Object Encryption CSE/SSE

[Configuring default encryption](https://docs.aws.amazon.com/AmazonS3/latest/userguide/default-bucket-encryption.html)

[How Amazon Simple Storage Service (Amazon S3) uses AWS KMS](https://docs.aws.amazon.com/kms/latest/developerguide/services-s3.html)

[Using server-side encryption with AWS KMS keys (SSE-KMS)](https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingKMSEncryption.html)

[Using server-side encryption with Amazon S3 managed keys (SSE-S3)](https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingServerSideEncryption.html)

[Using server-side encryption with customer-provided keys (SSE-C)](https://docs.aws.amazon.com/AmazonS3/latest/userguide/ServerSideEncryptionCustomerKeys.html)

### S3 - Client Side Encryption (CSE)

- Encrypt data client side before upload
- Decrypt data client side after download
- Data is encrypted before it reaches S3
- Data is decrypted after it leaves S3
- Data is encrypted in transit

### S3 - Server Side Encryption (SSE)

- Data is encrypted at rest
- Data is decrypted when accessed
- Data is encrypted in transit

#### S3 - Server Side Encryption with Customer Provided Keys (SSE-C)

- Customer provides the key
- Key is used to encrypt data
- Key is not stored by AWS
- Key is not stored with the data
- Cipher text object and Key Hash are stored

#### S3 - Server Side Encryption with S3 Managed Keys (SSE-S3 AES256) (Default)

- AWS Managed Keys
- Key is used to encrypt data
- Key is not stored by AWS
- Plaintext Key is not stored with the data
- Object Key is not stored with the data
- Cipertext object and Encrypted Object Key are stored

#### S3 - Server Side Encryption with KMS Managed Keys (SSE-KMS)

- KMS Managed Keys
- Created by you within KMS
- Managed by you within KMS
- Isoalted Permissions Configurable
- Plaintext and Ciphertext Data Encryption Key (DEK)
- Only generates keys doesn't store them
- Logging and Auditing with CloudTrail

| **Method**             | **Key Management** | **Encryption** | **Extras**                           |
| ---------------------- | ------------------ | -------------- | ------------------------------------ |
| Client Side Encryption | You                | You            | S3 never sees plaintext              |
| SSE-C                  | You                | S3             |                                      |
| SSE-S3                 | S3                 | S3             | No Key control No role separation    |
| SSE-KMS                | S3 & KMS           | S3             | Key rotation control Role separation |

## S3 - Bucket Keys

Amazon S3 Bucket Keys reduce the cost of Amazon S3 server-side encryption using AWS Key Management Service (SSE-KMS). Bucket-level keys for SSE can reduce AWS KMS request costs by up to 99 percent by decreasing the request traffic from Amazon S3 to AWS KMS.

### Without Bucket Keys

- Each Object "Put" using sse-kms uses a unique DEK
- Unique DEK stored with the object
- Each Data Encryption Key (DEK) is an API call to KMS
- Calls to KMS have a cost & levels where throttling can occur
- 5,500 requests per second per account
- 10,000 or 50,000 requests per second per region

### With Bucket Keys

- Time Limited Bucket key used to generate DEKs within S3
- Bucket Kesy significantly reduce the number of KMS requests which reduces the cost of using SSE-KMS
- Increases scalability and performance of SSE-KMS
- Not Retroactice, only effects objects added after the bucket key is enabled

#### S3 - Bucket Keys - things to remember

- CloudTrail KMS events now show the bucket not the object
- Works with replication ..the object encryption is maintained
- If replicating plaintext to a bucket using bucket keys the object is encrypted at the destination side (ETAG changes)

## S3 - Object Storage Classes

Amazon S3 offers a range of storage classes designed for different use cases.

[Amazon S3 pricing](https://aws.amazon.com/s3/pricing/)

[Amazon S3 Storage Classes](https://aws.amazon.com/s3/storage-classes/)

### S3 - Standard

- Objects are replicated across at least 3 AZs in the AWS region
- 11 9s of durability, 1 object loss in 10000 years
- Replication over 3 AZs & Content-MDS Checksums and Cyclic Redundancy Checks (CRCs) are used to detect and fix any data corruption
- When objects are stored a HTTP/1.1 200 OK response is provided by the S3 API Endpoint
- S3 Standard, you are billed a GB-month rate for the amount of data stored in your S3 buckets
- A $ per GB for transfer OUT (IN is free) and a price per 1,000 requests.
- No specific retrieval fee, no minimum storage duration, no minimum storage size
- S3 Standard has a millisecond first byte latency and objects can be made publicly accessible

### S3 - Standard-IA (Infrequent Access)

- Reduction in storage cost
- Standard-IA has a per GB data retrieval fee, overall cost increases with frequent data access.
- Standard-IA is designed for data that is accessed less frequently, but requires rapid access when needed.
- Standard-IA has a minimum duration charge of 30 days, objects can be stored for less but the minimum billing always applies.
- Standard-IA has a minimum capacity charge of 128KB per object, objects smaller than this are charged at this rate.
- Standard-IA should be used for long-lived data, which is important but where access is infrequent.

### S3 - One Zone-IA (Infrequent Access)

- One Zone-IA is similar to Standard-IA but data is stored in a single AZ
- One Zone-IA has a per GB data retrieval fee, overall cost increases with frequent data access.
- One Zone-IA jas a minimum duration charge of 30 days, objects can be stored for less but the minimum billing always applies.
- One Zone-IA has a minimum capacity charge of 128KB per object, objects smaller than this are charged at this rate.
- One Zone-IA does not provide the multi-AZ resilience of Standard-IA. Instead only one AZ is used within the region.
- 11 9s of durability, 1 object loss in 10000 years but reduced resilience compared to Standard-IA
- One Zone-IA should be used for **long lived data**, which is **NON-CRITICAL** and **REPLACABLE** and where access is **infrequent**.

### S3 - S3 Glacier - Instant Retrieval

- S3 Glacier is designed for long term storage of data that is infrequently accessed.
- Like S3 Standard-IA, cheaper storage, more expensive retrieval, longer minimum storage duration.
- Glacier Instant should be used for long-lived data, accessed once per quarter or less with millisecond access times.
- Glacier Instant has a minimum storage duration of 90 days, objects can be stored for less but the minimum billing always applies.
- Glacier Instant has a per GB data retrieval fee, overall cost increases with frequent data access.

### S3 - Glacier - Flexible Retrieval

- S3 Glacier Flexible Retrieval is designed for long term storage of data that is infrequently accessed.
- Cold storage, cheaper storage, more expensive retrieval, longer minimum storage duration.
- Objects cannot be made publicly accessible, any access of data requires a retrieval request.
- Data in Glacier Flexible Retrieval is stored in Glacier and can be restored to S3 Standard or S3 Standard-IA.
- Expedited retrieval is available for a higher cost
- Standard retrieval is available for a lower cost
- Bulk retrieval is available for the lowest cost
- Faster is more expensive, slower is cheaper
- First byte latency is 1-5 minutes for expedited, 3-5 hours for standard and 5-12 hours for bulk
- Best for archival data, backups, long term storage, data that is accessed once per quarter or less

### S3 - Glacier Deep Archive

- S3 Glacier Deep Archive is designed for long term storage of data that is infrequently accessed.
- 40KB minimum object size and 180 day minimum storage duration
- Data is in a frozen state and can take 12 hours to restore
- Objects cannot be made publicly accessible, any access of data requires a retrieval request.
- Data in Glacier Deep Archive is retrieved to S3 Standard or S3 Standard-IA temporarily.
- Standard 12 hour retrieval time, 180 day minimum storage duration
- Bulk 48 hour retrieval time, 180 day minimum storage duration
- First byte latency is 12 hours for standard and 48 hours for bulk

### S3 - Intelligent Tiering

- Intelligent Tiering is designed for data that has changing access patterns.
- S3 Intelligent Tiering moves objects between the different storage classes based on access patterns.
- Intelligent Tiering monitors and automatically moves any objects not accessed for 30 days to a low cost infrequent acess tier.
- The avaiable tiers are
- Frequent Access - Standard
- Infrequent Access - Standard-IA
- Archive Instant Access - Glacier - moved after 90 days
- Archive Access - Glacier Deep Archive - moved after 90 -> 270 days - optional
- Deep Archive Access - Glacier Deep Archive - moved after 180 -> 730 days - optional
- Intelligent Tiering has a monitoring and automation cost per 1,000 objects.
- The frequent access tier costs the same as S3 Standard, the infrequent access tier costs the same as S3 Standard-IA.
- Archive Instant Access costs the same as S3 Glacier Instant, Archive Access costs the same as S3 Glacier Flexible Retrieval and Deep Archive Access costs the same as S3 Glacier Deep Archive.

## S3 Lifecycle Configuration

S3 Lifecycle Configuration allows you to define rules to automatically transition objects between storage classes, archive objects and delete objects.

- A Lifecycle Configuration is a set of rules
- Rules consist of actions and conditions
- On a Bucket or group of objects
- Transition Actions - Move objects between storage classes
- Expiration Actions - Delete objects

### S3 - Lifecycle Configuration - Transition Actions

- Transition Actions - Move objects between storage classes
- Transitions travel down like a waterfall

## S3 Replication

S3 Replication allows you to replicate objects between S3 buckets in different regions.

### S3 - Replication - Cross Region Replication (CRR)

- Cross Region Replication (CRR) - Replicate objects between S3 buckets in different regions

### S3 - Replication - Same Region Replication (SRR)

- Same Region Replication (SRR) - Replicate objects between S3 buckets in the same region

#### S3 - Replication Options

- All objects or a subset
- Storage Class - default is to maintain
- Ownership - default is the source account
- Replication Time Control - default is as fast as possible

#### S3 - Replication Considerations

- By Default Not retroactive & Versioning need to be ON
- Batch replication can be used to replicate existing objects
- One-way replication Source to Destination (or bi-directional)
- Unencrypted, SSE-S3, SSE-KMS (with extra config), SSE-C
- Source bucket owner needs permissions to objects
- No system events, Glacier or Glacier Deep Archive
- No Deletes (But this can be added - DeleteMarkerReplication)

#### S3 - Replication - Why use replication?

- SRR - Log Aggregation, Data Processing, Data Sharing
- SRR - PROD and TEST Sync
- SRR - Resilience with strict sovereignty requirements
- CRR - Global Resilience Improvements
- CRR - Latency Reduction

## S3 Pre-Signed URLs

S3 Pre-Signed URLs allow you to generate a URL which can be used to access an object in S3 for a limited time.

- You can create a URL for an object you have no access to
- When using the URL, the permissions match the identity of the creator
- Access denied could mean the generating ID never had access or doesn't now
- Don't generate with a role URL stops working when temporary credentials expire

## S3 Select and Glacier Select

S3 and Glacier Select allow you to use a SQL-Like statement to retrieve partial objects from S3 and Glacier.

- S3 can store HUGE objects (up to 5TB)
- You often want to retrieve the entire object
- Retrieving a 5TB object takes time, uses 5TB of data transfer
- Filtering at the client side doesn't redcue the amount of data transferred
- S3/Glacier Select let you use SQL-Like statements to filter the data
- To select part of the object, pre-filtered by S3
- CSV, JSON, Parquet, BZIP2 compression for CSV and JSON

### S3 Select and Glacier Select - How it works

- SQL-like expression provided to S3 Select, selection happens at the S3 service
- With S3 Select, filtering occurs on the service side and only the filtered data is returned
- Up to 400% faster and 80% cheaper than full object retrieval

## Cross-Origin Resource Sharing (CORS)

Cross-origin resource sharing (CORS) defines a way for client web applications that are loaded in one domain to interact with resources in a different domain. With CORS support, you can build rich client-side web applications with Amazon S3 and selectively allow cross-origin access to your Amazon S3 resources.

[Cross-Origin Resource Sharing (CORS)](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)

- Simple Requests
- Preflight Requests and Preflighted requests
- Access-Control-Allow-Origin - Origin
- Access-Control-Max-Age - Time
- Access-Control-Allow-Methods - Methods
- Access-Control-Allow-Headers - Headers
- Define Origin (original URL used) other domains need CORS

## S3 Event Notifications

The Amazon S3 notification feature enables you to receive notifications when certain events happen in your bucket. To enable notifications, you must first add a notification configuration that identifies the events you want Amazon S3 to publish and the destinations where you want Amazon S3 to send the notifications. You store this configuration in the notification subresource that is associated with a bucket.

- Notifications generated when events occur in a bucket
- Can be delivered to SNS, SQS and Lambda functions
- Object Created (Put, Post, Copy, CompleteMultipartUpload)
- Object Delete (\*, Delete, DeleteMarkerCreated)
- Object Restore (Post(Initiated), Completed)
- Replication (OperationMissedThreshold, OperationReplicatedAfterThreshold, OperationNotTracked, OperationFailedReplication)

## S3 Access Logs

Server access logging provides detailed records for the requests that are made to a bucket. Server access logs are useful for many applications. For example, access log information can be useful in security and access audits. It can also help you learn about your customer base and understand your Amazon S3 bill.

- Access logs are stored in another bucket
- Logs are delivered in a common log format
- Bucket and Object Access
- Access Logging can be enabled via the console UI or via PUT Bucket logging
- S3 Log Delivery - S3, CloudWatch Logs, Kinesis Firehose
- Best Efforts log delivery, accesses to Source Bucket are usually logged in Target bucket within a few hours
- Logs Files consists of Log Records, Records are newline delimited, Attributes are space delimited
- Bucket ACL Allows "S3 Log Delivery" permission to the target bucket

## S3 Object Lock

You can use S3 Object Lock to store objects using a _write-once-read-many_ (WORM) model. It can help you prevent objects from being deleted or overwritten for a fixed amount of time or indefinitely. You can use S3 Object Lock to meet regulatory requirements that require WORM storage, or add an extra layer of protection against object changes and deletion.

- Object Lock enabled on `new` buckets (Support req for existing)
- Write-Once-Read-Many (WORM) model - No Delete, No Overwrite
- Requires versioning - individual versions are locked
- 1 - Retention Period
- 2 - Legal Hold
- Both, One or the other, or none
- A Bucket can have default Object Lock Settings

### S3 Object Lock - Retention Period

- Specify Days or Years - A Retention Period
- COMPLIANCE - Can't be adjusted, deleted or overwritten
- Even by the account root user until retention period expires
- GOVERNANCE - special permissions can be granted allowing lock settings to be adjusted
- s3:BypassGovernanceRetention - Allows objects to be deleted or overwritten
- x-amz-bypass-governance-retention:true - Header to bypass governance retention (console default)

### S3 Object Lock - Legal Hold

- Set on an object version - ON or OFF
- no retention period
- No Deletes or Changes until removed
- s3:PutObjectLegalHold is required to add or remove
- Prevent accidental deletion of critical object versions

## S3 Access Points

Amazon S3 Access Points, a feature of S3, simplifies managing data access at scale for applications using shared data sets on S3. Access points are unique hostnames that customers create to enforce distinct permissions and network controls for any request made through the access point.

[Creating access points](https://docs.aws.amazon.com/AmazonS3/latest/userguide/creating-access-points.html#access-points-policies)

- Simplify managing access to S3 Buckets/Objects
- Rather than 1 bucket with 1 bucket policy
- Create many access points with different policies
- each with different network access controls
- multiple access points with multiple policies
- each access point has its own endpoint address
- Created via Console or `aws s3control create-access-point --name secretcats --account-id 123456789012 --bucket catpics`

## S3 Inventory

Amazon S3 inventory provides a flat file list of your objects and metadata, which is a scheduled alternative to the Amazon S3 synchronous List API operation. Amazon S3 inventory provides comma-separated values (CSV) or Apache optimized row columnar (ORC) or Apache Parquet (Parquet) output files that list your objects and their corresponding metadata on a daily or weekly basis for an S3 bucket or for objects that share a prefix.

- Helps you manage your storage
- Inventory of objects & various optional fields
- Encryption, Size, Last Modified, Storage Class, ETag, Version ID, Replication Status, Object Lock, etc..
- Generate daily or weekly (can't be forced)
- Output - CSV, ORC, Parquet
- Multiple inventories can be set up, and they go to a target bucket
- Same account or different account ... needs a bucket policy
- Audit, Compliance, Cost Management or any specific regulatory requirements

## Elastic File System (EFS)

The Elastic File System (EFS) is an AWS managed implementation of NFS which allows for the creation of shared 'filesystems' which can be mounted within multi EC2 instances.

EFS can play an essential part in building scalable and resilient systems.

[File-system permissions](https://en.wikipedia.org/wiki/File-system_permissions)

[Amazon EFS performance](https://docs.aws.amazon.com/efs/latest/ug/performance.html)

[What is Amazon Elastic File System?](https://docs.aws.amazon.com/efs/latest/ug/whatisefs.html)

[Managing file system storage](https://docs.aws.amazon.com/efs/latest/ug/lifecycle-management-efs.html)

- EFS is an implementation of NFSv4
- EFS Filesystems can be mounted in Linux
- Shared between many EC2 instances
- Private service, via mount targets inside a VPC
- Can be accessed from on-premises via Direct Connect or VPN
- Only supported for Linux systems
- General Purpose and Max I/O Performance Modes
- General Purpose - default for most workloads
- Bursting and Provisioned Throughput Modes
- Bursting - 1TB-8TB, 50MB/s per TB, Burst to 100MB/s
- Provisioned - 1TB-8TB, 50MB/s per TB, 100MB/s-1000MB/s
- Standard and Infrequent Access Storage Classes
- Standard - default, Infrequent Access - cost effective
- Lifecycle Management - move files to IA after 30 days
- Lifecycle Policies - move files between storage classes

## FSx for Windows File Server

FSx for Windows Servers provides a native windows file system as a service which can be used within AWS, or from on-premises environments via VPN or Direct Connect

FSx is an advanced shared file system accessible over SMB, and integrates with Active Directory (either managed, or self-hosted).

It provides advanced features such as VSS, Data de-duplication, backups, encryption at rest and forced encryption in transit.

- Fully managed native windows file servers/shares
- Designed for integration with windows environments
- Integrates with Directory Service or Self-Managed AD
- Single or Multi-AZ within a VPC
- On-demand and Scheduled backups
- Accessible using VPC, Peering, VPN, Direct Connect

### FSx for Windows File Server - Features and Benefits

- VSS - User-Driven Restores
- Native file system accessible over SMB
- Windows permission model
- Supports DFS .. scale-out file share structure
- Managed - no file server admin
- Integrations with DS AND your own directory

## FSx for Lustre

FSx for Lustre is a managed file system which uses the FSx product designed for high performance computing

It delivers extreme performance for scenarios such as Big Data, Machine Learning and Financial Modeling

[Aggregate file system performance](https://docs.aws.amazon.com/fsx/latest/LustreGuide/performance.html#fsx-aggregate-perf)

[Persistent storage for high-performance workloads using Amazon FSx for Lustre](https://aws.amazon.com/blogs/storage/persistent-storage-for-high-performance-workloads-using-amazon-fsx-for-lustre/)

- Managed Lustre File System - Designed for HPC - Linux Clients (POSIX)
- Machine Learning, Financial Modelling, Big Data
- 100's GB/s throughput and sub millisecond latency
- Deployment types - Persistent and Scratch
- Scratch - Highly optimised for Short term no replication and fast
- Persistent - longer term, HA (in one AZ), self-healing, backups
- Accessible over VPN or Direct Connect

### FSx for Lustre - Information

- Metadata stored on Metadata Targets (MST)
- Objects are stored on called object storage targets (OSTs) (1.13TIB)
- Baseline performance based on size
- Size - min 1.2TiB then increments of 2.4TiB
- For Scratch - Base 200MB/s per TiB of storage
- Persistents offers 50MB/s per TiB, 100MB/s per TiB, 200MB/s per TiB
- Burst up to 1,300 MB/s per TiB (Credit System)

### FSx for Lustre - Scratch

- Scratch - Highly optimised for Short term no replication and fast
- Short term or temp workloads
- No HA .. No replication
- Larger file systems means more servers, more disks and more chance of failure
- Persistent has replication, backups, self-healing within ONE AZ only
- Auto-heals when hardware failure occurs
- You can backup to S3 with both!! (Manual or Automatic 0-35 day retention)

## CloudFront

Amazon CloudFront is a fast content delivery network (CDN) service that securely delivers data, videos, applications, and APIs to customers globally with low latency, high transfer speeds, all within a developer-friendly environment.

- Origin - The source location of your content
- S3 Origin or Custom Origin
- Distribution - The `configuration` unit of CloudFront
- Edge Location - Local cache of your data
- Regional Edge Cache - Larger version of an edge location. Provides another layer of caching.

### CloudFront - Behaviours

CloudFront Behaviours control much of the TTL, protocol and privacy settings within CloudFront

[Supported protocols and ciphers between viewers and CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/secure-connections-supported-viewer-protocols-ciphers.html)

### CloudFront - TTL

- More frequent cache HITS = lower origin load
- Deault TTL (behaviour) 24 hours (validity period)
- You can set Minimum and Maximum TTLs
- Origin Headers can be used to set TTLs
- Origin Headers: Cache-Control max-age (seconds)
- Origin Headers: Cache-Control s-maxage (seconds)
- Origin Headers: Expires (Date and Time)
- Custom Origin or S3 (via object metadata)

### CloudFront - Invalidations

- Cahce Invalidation .. performed on a distribution
- ... applies to all edge locations ... takes time
- /images/whiskers1.jpg
- /images/whiskers\*
- /images/\*
- /\*
- Versioned file names ... whiskers1_v1.jpg

## AWS Certificate Manager (ACM)

AWS Certificate Manager is a service that lets you easily provision, manage, and deploy public and private Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificates for use with AWS services and your internal connected resources.

- HTTP - Simple and Insecure
- HTTPS - SSL/TLS Layer of Encryption added to HTTP
- Data is encrypted in transit
- Certificates prove identity of the server
- Chain of trust - Signed by a trusted authority
- ACM lets you run a public or private Certificate Authority (CA)
- Private CA - Applications need to trust your private CA
- Public CA - Browsers trust a list of providers, which can trust other providers
- ACM can generate or import Certificates
- If generated ... it can automatically renew
- If imported .. you are responsible for renewal
- Certificates can be deployed out to supported services
- Supported AWS Services ONLY (e.g. CloudFront and ALBs... NOT EC2)
- ACM is a regional service
- Certs cannot leave the region they are generated or imported in
- To use a cert with an ALB in ap-southeast-2 you need a cert in ACM in ap-southeast-2
- Global Services such as CloudFront operate as though within `us-east-1`

## CloudFront and SSL

AWS Certificate Manager is a service that lets you easily provision, manage, and deploy public and private Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificates for use with AWS services and your internal connected resources.

- CloudFront Default Domain Name (CNAME) - https://d1234.cloudfront.net
- SSL Supported by default ... \*.cloudfront.net certificate
- Alternate Domain Name (CNAMES) - e.g. cdn.mydomain.com
- Verify Ownership (optionally HTTPS) using a matching certificate
- Generate or import in ACM .. in us-east-1
- HTTP or HTTPS, HTTP => HTTPS, HTTPS Only
- Two SSL Connections: Viewer => CloudFront and CloudFront => Origin
- Both Need valid public certificates (and intermediate certs)

- Historically every SSL enabled site needed its own IP
- Encryption starts at the TCP connection
- Host headers happens after that - Layer 7 // Application Layer
- SNI - Server Name Indication - allows multiple SSL sites on one IP
- SNI is a TLS extension, allowing a host to be included
- Resulting in many SSL Certs/Hosts using a shared IP
- Old browsers don't support SNI ... CF charges extra for dedicated IP

## CloudFront - Origin Types and Origin Architecture

CloudFront origins store content distributed via edge locations.

The features available differ based on using S3 origins vs Custom origins

[Supported protocols and ciphers between viewers and CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/secure-connections-supported-viewer-protocols-ciphers.html#secure-connections-supported-ciphers)

## CloudFront - Security

### CloudFront - Origin Access Identity (OAI) - S3 Origins

- An OAI is a type of identity
- It can be associated with CloudFront Distributions
- CloudFront becomes that OAI
- That OAI can be used in S3 Bucket Policies
- Deny all but one or more OAI's

### CloudFront - Origin Access Identity (OAI) - Custom Origins

- OAI can be used to restrict access to Custom Origins
- OAI can be used in the Origin Policy
- Requires custom headers to be set on the Origin
- Custom Origins can use either approch or a combination of both

### CloudFront - Private Distributions

- Public - Open Access to objects
- Private - requests require Signed Cookie or URL
- 1 Behaviour - Whole Distribution PUBLIC or PRIVATE
- Multiple Behaviours - each is PUBLIC or PRIVATE
- OLD - A CloudFront Key is created by an Account Root User
- OLD - The account is added as a TRUSTED SIGNER
- NEW - TRUSTED KEY GROUPS

### CloudFront - Signed URLs and Signed Cookies

- SignedURLs provides access to one object
- Historically RTMP distributions couldn't use cookies
- Use URL's if your client doesn't support cookies
- Cookies provides access to groups of objects
- Use for groups of files / all files of a type - e.g. all cat gifs
- Or if maintaining application URL's is important

## CloudFront - Geo Restriction

There are two common architectures for restricting access to content via CloudFront.

The built in feature set - CloudFront Geo Restriction allows for White or Black list restrictions based on ONLY Country Code

3rd Party Geolocation requires a compute instance, a private distribution and the generation of signed URLs or Cookies - but can restrict based on almost anything (licensing, user login status, user profile fields and much more)

### CloudFront - Geo Restriction - White List / Black List

- White List - Allow only these countries
- Black List - Deny only these countries
- Countries only - No IP ranges
- GeoIP Database 99.8%+ Accurate
- Applies to the entire distribution

### CloudFront - 3rd Party Geolocation

- Completely customisable
- Requires a compute instance
- Requires a private distribution
- Requires signed URLs or Cookies

## CloudFront - Lambda@Edge

Lambda@Edge allows CloudFront to run lambda function at CloudFront edge locations to modify traffic between the viewer and edge location and edge locations and origins.

[Example: Redirecting viewer requests to a country-specific URL](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/lambda-examples.html#lambda-examples-redirecting-examples)

- You can run lightweight Lambda at edge locations
- Adjust data between the Viewer and Origin
- Currently support Node.js and Python
- Run in the AWS Public Space (Not VPC)
- Layers are not supported
- Different Limits vs Normal Lambda Functions

### CloudFront - Lambda@Edge - Use Cases

- A/B Testing - Viewer Request
- Migration Between S3 Origins - Origin Request
- Different Objects Based on Device - Origin Request
- Content By Country - Origin Request
- Security Headers - Viewer Response
- Custom Headers - Viewer Request
- Custom Error Pages - Viewer Response

## Amazon DynamoDB

DynamoDB is a NoSQL fully managed Database-as-a-Service (DBaaS) product available within AWS.

- NoSQL Public Database-as-a-Service (DBaaS) - Key/Value and Document
- No self-managed server or infrastructure
- Manual / Automatic provisioned performance IN/OUT or On-Demand
- Highly Resilient ... across AZs and optionally global
- Really fast .. single-digit millisecond latency (SSD based)
- Backups, point-in-time recovery, encryption at rest
- Event-Driven integration ... do things when data changes

### DynamoDB - Tables

- A Table is a grouping of ITEMS with the same PRIMARY KEY
- Simple (Partition Key) or Composite (Partition Key and Sort Key)
- Each item must have a unique value for PK and SK
- No rigid attribute schema - each item can have different attributes
- No fixed schema - each item can have different attributes
- Item size limit 400KB
- Capacity Modes - On-Demand or Provisioned
- Capacity Units - Read Capacity Units (RCU) and Write Capacity Units (WCU)
- 1 RCU = 4KB/s Read
- 1 WCU = 1KB/s Write

### DynamoDB - On-Demand Backups

- On-Demand Backups - Full copy of the table
- Restore - Same or Cross Region, with or without indexes, adjust encryption settings
- Point-in-Time Recovery - Restore to any point in time
- Retention Period - 35 days
- Backups are stored in S3
- 1 second granularity for PITR - need to enable

### DynamoDB - Reading and Writing

[Capacity unit consumption for writes](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/ProvisionedThroughput.html#ItemSizeCalculations.Writes)

- On-Demand - Pay per request, best for unpredictable workloads, low admin overhead
- On-Demand - price per million RCU/WCU
- Provisioned - Pay for capacity, best for predictable workloads
- Provisioned - price per RCU/WCU per hour set on a per table basis
- Every operation consumes at least 1 RCU or WCU
- 1 RCU is 1 x 4KB read operation per second
- 1 WCU is 1 x 1KB write operation per second
- Every table has a RCU and WCU burst pool (300 seconds)

### DynamoDB - Query

- Query accepts a single PK value and optionally a SK value or range
- Capacity consumed is the size of all returned items
- Further filtering discards data - capacity is still consumed
- Can ONLY query on PK or PK and SK

### DynamoDB - Scan

- Scan reads every item in the table
- Scan moves through a table consuming the capacity of every item.
- You have complete control on what data is selected, any attributes can be used and any filters.
- Scans can be expensive in terms of capacity and time
- Scan is not efficient for large tables

### DynamoDB - Consistency Model

- Storage Nodes - 3 copies of data in 3 AZs
- One Leader Node - Writes to all 3 copies
- Writes are always directed at the leader node
- The Leader node replicates data to the storage nodes
- Eventually Consistent Reads - Read from any of the 3 nodes
- Potential for stale data
- Strongly Consistent Reads - Read from the leader node
- Not every application or access type tolerates eventual consistency

### DynamoDB - Indexes (LSI and GSI)

Local Secondary Indexes (LSI) and Global Secondary Indexes (GSI) allow for an alternative presentation of data stored in a base table.

LSI allow for alternative SK's whereas with GSIs you can use alternative PK and SK.

- Query is the most efficient operation in DDB
- Query can only work on 1 PK value at a time
- and optionally 1 SK value or range
- Indexes are alternative views on the table data
- Different SK (LSI) or Different PK and SK (GSI)
- Some or all attributes can be projected into the index

#### DynamoDB - LSI

- LSI is an alternative view for a table
- MUST be created with a table
- 5 LSI's per base table
- Alternative SK on the table
- Shares the RCU and WCU with the table
- Attributes - All, KEYS_ONLY, INCLUDE
- LSI's are an alternative view on the base table data using the same PK and a different SK
- Indexes are sparse, only items which have a value in the index alternative sort key are added to the index

#### DynamoDB - GSI

- Can be created at any time
- Default limit of 20 per base table
- Alternative PK and SK
- GSI's have their own RCU and WCU allocations
- Attributes - ALL, KEYS_ONLY, INCLUDE
- GSI's are an alternative view on the base table with alternative PK and SK they have their own RCU and WRU and can be created at any time
- GSI's are sparse, only items which have values in the new PK and optional SK are added
- GSI's are always eventually consistent, replication between base and GSI is Asynchronous

#### DynamoDB - Considertions

- Careful with projection (ALL, KEYS_ONLY, INCLUDE)
- Queries on attributes NOT projected are expensive
- Use GSIs as default, LSI only when strong consistency is required
- Use indexes for alternative access patterns

## DynamoDB - Streams and Triggers

- Time ordered list of ITEM CHANGES in a table
- 24-hour rolling window
- Enabled on a per table basis
- Records INSERTS, UPDATES, DELETES
- Different view types influence what is in the stream
- View types - KEYS_ONLY, NEW_IMAGE, OLD_IMAGE, NEW_AND_OLD_IMAGES

### DynamoDB - Trigger Concepts

- ITEM changes generate an event
- That event contains the data which changed
- An action is taken using that data
- AWS = Streams + Lambda
- Reporting and Analytics
- Aggregation, Messaging, Notifications
- 1. ITEM change occurs in a table with streams enabled
- 2. Stream Record is added onto stream
- 3. Lambda function is invoked when stream event occurs. Function is passed the VIEW data as an event

## DynamoDB - Accelerator (DAX)

DynamoDB Accelerator (DAX) is a fully managed, highly available, in-memory cache for DynamoDB that delivers up to a 10x performance improvement - from milliseconds to microseconds - even at millions of requests per second.

### Traditional Cache

- 1. Application checks the cache for data - a CACHE MISS occurs if data isn't cached
- 2. Data is loaded from the database with a separate operation and SDK
- 3. Cache is updated with retrieved data. Subsequent queries will load data from cache as a CACHE HIT

### DAX SDK

- 1. Application uses the DAX SDK and makes a single call for the data which is returned by DAX
- 2. DAX either returns the data from its cache or retrieves it from the database and then caches it
- Less complexity for the app developer - tighter integration with DynamoDB

### DAX Architecture

- DAX is a cluster of nodes
- Each node is an EC2 instance
- Each node has a copy of the data
- Item cache holds results of (Batch) GetItem and Query operations
- The query cache holds data based on query/scan parameters
- Read replicas in other AZs can be used to increase read capacity
- DAX is accessed via an endpoint in the VPC
- Cache HITS are returned in microseconds ... MISSES in milliseconds
- Write-Through is supported, data is written to DDB then DAX
- If a CACHE MISS occurs data is also written to the primary node of the cluster

#### DAX Considerations

- Primary NODE (Writes) and Replicas (Reads)
- Nodes are HA .. Primary failure = election
- In-Memory Cache - Scaling .. Much faster reads, reduced costs
- Scale UP and Scale OUT (Bigger or More)
- Supports write-through
- DAX Deployed WITHIN a VPC

## DynamoDB Global Tables

DynamoDB Global Tables provides multi-master global replication of DynamoDB tables which can be used for performance, HA or DR/BC reasons.

- Global tables provides multi-master cross-region replication
- Tables are created in multiple regions and added to the same global table (becoming replica tables)
- Last writer wins is used for conflict resolution
- Reads and Writes can occur to any region
- Generally sub-second replication between regions
- Strongly consistent reads ONLY in the same region as writes

## DynamoDB TTL

Amazon DynamoDB Time to Live (TTL) allows you to define a per-item timestamp to determine when an item is no longer needed. Shortly after the date and time of the specified timestamp, DynamoDB deletes the item from your table without consuming any write throughput. TTL is provided at no extra cost as a means to reduce stored data volumes by retaining only the items that remain current for your workload’s needs.

- Timestamp for automatic DELETE of ITEMS
- When TTL is enabled on a table a specific attribute is selected for TTL
- A Per-Partition process periodically runs, checking the current time (in seconds since epoch) to the value in the TTL attribute
- ITEMS where the TTL attribute is older than the current time are set to expired
- Another per-partition background process scans for expired items and removes them from tables and indexes and a delete is added to streams if enabled
- Any DELETE operations caused by TTL are background system processes and don't impact table performance and aren't chargeable
- A stream of TTL delections can be enabled (24 hour window)

## High Availability vs Fault Tolerance vs Disaster Recovery

### High Availability

- Aims to ensure an agreed level of operational performance, usually uptime, for a higher than normal period
- High-Availability - Minimise downtime

### Fault Tolerance

- The ability of a system to continue operating in the event of a failure of a component
- Fault tolerance is achieved by redundancy in hardware and software
- Fault tolerance enables a system to continue operating properly in the event of the failure of some of its components
- Fault tolerance is particularly important in high-availability systems
- Fault tolerance - Operate Through Faults

### Disaster Recovery

- Set of policies, tools and procedures to enable the recovery or continuation of vital technology infrastructure and systems following a natural or human-induced disaster
- Pre-planning and testing is essential
- DR Process - Risk Assessment, Business Impact Analysis, Strategy Development, Plan Development, Testing and Training, Maintenance
- Disaster Recover - Used when High-Availability and Fault Tolerance fail

## Disaster Recovery / Business Continuity

- Effective DR/BC costs money all the time
- You need some type of extra resource
- Executing a DR/BC process takes time
- How long .. depends on the type of DR/BC

### Disaster Recovery / Business Continuity - Types

#### Backup and Restore

- Backup - Copy of data
- Restore - Copy data back
- Data is constantly backed up at the primary site
- The only costs are backup media and management
- No ongoing spare infrastructure costs
- Restores require new hardware or a lenghty restore process

#### Pilot Light

- Pilot Light - A small version of the primary site
- A secondary environment is provisioned in advance
- Running the absolute minimum of infrastructure
- It can be powered on mucvh quicker than backup and restore
- Critical components such as Databases are always syncing ready to go

#### Warm Standby

- Warm Standby - A scaled down version of the primary site
- Smaller sized but fully functional version of your primary infrastructure is running 24/7/365
- Ready to be increased in size when failover is required
- Faster than pilot light but more expensive
- Cheaper than ful active-active

#### Multi-Site Active/Active

- Multi-Site Active/Active - Both sites are active all the time
- Data is constantly replicated from the primary site to backup.
- Costs are generally 200% of the primary site
- A full copy is running all the time
- You can load balance across environments improving HA and performance

### Disaster Recovery / Business Continuity - Considerations

- How important is it to your business?
- How quickly do you need to recovery?
- Backups - Cheap and Slow
- Pilot Light - Fairly Cheap and Faster
- Warm Standby - costly but quick to recover
- Multi-Site Active/Active - Most expensive but fastest but no recovery time

#### Disaster Recovery Storage

##### DR - Instance Store

- Instance store volumes are attached to the host that is running the instance
- This instance runs inside an AZ
- Failure of the host or AZ will result in the loss of the instance store volume

##### DR - EBS

- EBS volumes are network-attached storage
- EBS replicates whitin an AZ
- Failure of an AZ means failure of a volume
- Snapshots can be stored in S3 and copied to another AZ

##### DR - S3

- S3 is a regional service
- Data is replicated across multiple AZs
- S3 can provide regional resilience

##### DR - EFS

- EFS is a regional service
- EFS file systmes are replicated across multiple AZs
- They are by default regionally resillient
- Failure of the region means failure of the file system

##### DR - S3 Snapshot Copy

- Snapshots are stored in S3
- They can be copied between regions
- This provide global resilience

#### Disaster Recovery - Compute

##### DR - EC2

- EC2 runs within an one AZ
- EC2 can be moved to another host
- An ASG can be used to move instances to another AZ
- ASG can use launch templates/AMIs to launch in another AZ

##### DR - ECS

- ECS clusters can be in EC2 Mode or Fargate Mode
- In EC2 Mode the DR characteristics are the same as EC2
- AZ failure will result in ECS container failure
- In fargate mode containers use ENI's in a VPC
- Services can be used to achieve a similar architecture to auto scaling groups

##### DR - Lambda

- Lambda can run in public or private mode
- VPC Lambda functions are allocated an ENI in each subnet
- Failure of an AZ will result in other subnets being used
- Public Lambda functions operate from all AZs in a region
- A region failure would be required to impact service

#### Disaster Recovery - Databases

##### DR - RDS

- Databases on EC2 dependant on EC2 Host and AZ
- No resillence beyond snapshots
- RDS runs in a Subnet Group
- RDS can be Multi-AZ
- Primary or Standby in another AZ
- Syncronous replication between both
- Failover is automatic
- Failure of both primary and standby AZs would impact service
- Cross Region Read Replica Asynchronous Replication can be used for DR

##### DR - Aurora

- Aurora isn't limited to Primary and Standby
- Aurora can have up to 15 read replicas
- Aurora can have replicas in different AZs
- Aurora Cluster Storage is replicated 6+ times across 3 AZs at the storage level
- Only region failure would significantly impact service
- Aurora can have replicas in all AZs in a region storage is handled by the shared cluster storage
- Aurora Global Databases storage level replication across regions (1s or less lag)

##### DR - DynamoDB

- DynamoDB is a regional service
- Regional failure would need to occur to impact service
- DynamoDB Global Tables can be used to replicate data to other regions

#### Disaster Recovery - Networking

##### DR - VPC

- VPC are regionally resillient
- Region failure means VPC failure
- VPC Router and IGW also are region resilient
- Subnets are in '1' AZ - AZ Failure means subnet failure
- Load balancers have LB nodes in 2+ AZs - as long as one node is functional the LB is functional
- Accessing through a load balancer means from a customer perspective only a region failure would cause application failure
- Public services run from all AZs in a region, only region failure would cause service failure
- Interface Endpoints reside in one AZ. AZ failure means VPCE failure
- Multiple VPCE can be added for regional HA

## EC2 - Launch Configurations and Launch Templates

Launch Configurations and Launch Templates provide the WHAT to Auto scaling groups.

They define WHAT gets provisioned

The AMI, the Instance Type, the networking & security, the key pair to use, the userdata to inject and IAM Role to attach.

- Allow you to define the configuration of an EC2 instance in advance
- AMI, Instance Type, Storage and Key pair
- Networking and Security Groups
- Userdata and IAM Role
- Both are NOT editable - defined once. LT has versions
- LT provide newer features - including T2/T3 Unlimited, Placement Groups, Capacity Reservations, Elastic Graphics

## EC2 - Auto Scaling Groups

An Auto Scaling group contains a collection of Amazon EC2 instances that are treated as a logical grouping for the purposes of automatic scaling and management. An Auto Scaling group also enables you to use Amazon EC2 Auto Scaling features such as health check replacements and scaling policies. Both maintaining the number of instances in an Auto Scaling group and automatic scaling are the core functionality of the Amazon EC2 Auto Scaling service.

- Automatic Scaling and Self-Healing for EC2
- Uses Launch Templates or Configurations
- Has a Minimum, Desired and Maximum number of instances (e.g 1:2:4)
- Keep running instances at the Desired capacity by provisioning or terminating instances
- Scaling Policies automate based on metrics

### Auto Scaling - Scaling Policies

- Manual Scaling - Manually adjust the desired capacity
- Scheduled Scaling - Time based adjustment - e.g. Black Friday
- Dynamic Scaling
  - Simple Scaling - "CPU above 50% +1", "CPU below 20% -1"
  - Stepped Scaling - Bigger +/- based on difference
  - Target Tracking - Desired Aggregate CPU = 40% ..ASG handle it
- Cooldown Period - Time between scaling actions

### ASG + Load Balancer

- ASG instances are automatically added to or removed from the target group
- ASG can use the Load Balancer Health Checks rather than EC2 status checks Application Awareness

### Scaling Processes

- Launch and Terminate - SUSPEND and RESUME
- AddToLoadBalancer - add to LB on launch
- AlarmNotification - accept notifications from CloudWatch
- AZRebalance - balance instances across AZs
- HealthCheck - check instances are healthy
- ReplaceUnhealthy - replace unhealthy instances
- ScheduledActions - accept scheduled actions
- Standby - remove from service but keep in ASG

- Autoscaling Groups are free
- Only the resources created are billed
- Use cool downs to avoid rapid scaling
- Think about more, smaller instances - granularity
- Use with ALB's for elasticity - abstraction
- ASG defines WHEN and WHERE, LT defines WHAT

### ASG - Scaling Policies

With step scaling and simple scaling, you choose scaling metrics and threshold values for the CloudWatch alarms that trigger the scaling process. You also define how your Auto Scaling group should be scaled when a threshold is in breach for a specified number of evaluation periods.

Step scaling policies and simple scaling policies are two of the dynamic scaling options available for you to use. Both require you to create CloudWatch alarms for the scaling policies. Both require you to specify the high and low thresholds for the alarms. Both require you to define whether to add or remove instances, and how many, or set the group to an exact size.

The main difference between the policy types is the step adjustments that you get with step scaling policies. When step adjustments are applied, and they increase or decrease the current capacity of your Auto Scaling group, the adjustments vary based on the size of the alarm breach.

- ASGs don't NEED scaling policies - they can have none
- Manual - Min, Max and Desired - Testing and Urgent
- Simple Scaling - single metric, single threshold
- Step Scaling - More granular than simple scaling
- Target Tracking - CPU, Network, Memory, Custom Metrics
- Scaling Based on SQS - ApproximateNumberOfMessagesVisible

### ASG - Lifecycle Hooks

Lifecycle hooks enable you to perform custom actions by pausing instances as an Auto Scaling group launches or terminates them. When an instance is paused, it remains in a wait state either until you complete the lifecycle action using the complete-lifecycle-action command or the `CompleteLifecycleAction` operation, or until the timeout period ends (one hour by default).

- Custom Actions on instances during ASG actions
- Instance launch or Instance terminate transitions
- Instances are paused within the flow .. they wait
- Until a timeout (then either CONTINUE or ABANDON)
- or you resume the ASG process `CompleteLifecycleAction`
- EventBridge or SNS Notifications

### ASG - Health Checks

Amazon EC2 Auto Scaling can determine the health status of an instance using one or more of the following:

- Status checks provided by Amazon EC2 to identify hardware and software issues that may impair an instance. The default health checks for an Auto Scaling group are EC2 status checks only.
- Health checks provided by Elastic Load Balancing (ELB). These health checks are disabled by default but can be enabled.
- Your custom health checks.
- EC2 (Default), ELB (Can be enabled) and Custom
- EC2 - Stopping, Stopped, Terminatied, Shutting Down or Impaired (not 2/2 status) = UNHEALTHY
- ELB - HEALTHY = Running and passing ELB health check
- Can be more application aware (Layer 7)
- Custom - Instances marked healthy and unhealthy by an external system
- Health check grace period (Default 300s) - Delay before starting checks
- Allows system launch, bootstrapping and application startup

## Elastic Load Balancer (ELB)

The Elastic Load Balancer (ELB) was introduced in 2009 with the 'now called' Classic Load Balancer

Two new versions the v2 Application and v2 Network load balancers are now the recommended solutions.

- 3 Types of load balancers (ELB) available within AWS
- Split between v1 (avoid / migrate) and v2 (preferred)
- Classic Load Balancer (CLB) - v1 - Introduced in 2009
- Not really layer 7, lacking features, 1 SSL per CLB
- Application Load Balancer (ALB) - v2 - HTTP/S/WebSocket
- Network Load Balancer (NLB) - v2 - TCP/UDP/SSL/TLS
- V2 = faster, cheaper, support target groups and rules

### Elastic Load Balancer Architecture (ELB)

Elastic Load Balancers are a core part of any scaling architecture within AWS.

- Configured to run in 2+ AZ's
- 1 + Nodes are placed into a subnet in each AZ and scale with load
- Each ELB is configured with an (A) record DNS name. This resolves to the ELB Nodes
- Internet-facing Nodes have public IPs
- Internal Only have private IPs
- Load Balancers (Nodes) are configured with listeners which accept traffic on a port and protocol and communicate with targets on a port and protocol
- Internet-facing LB nodes can access public and private EC2 instances
- 8+ free IPs per subnet and a /27 or larger subnet to allow for scale

#### IMPORTANT

- ELB is a DNS A Record pointing at 1+ Nodes per AZ
- Nodes (in one subnet per AZ) can scale
- Internet-facing means nodes have public IPv2 IPs
- Internal is private only IPs
- EC2 doesn't need to be public to work with a LB
- Listener Configuration controls WHAT the LB does
- 8+ free IPs per subnet and a /27 or larger subnet to allow for scale

### Elastic Load Balancer Architecture - Three Tier Architecture (Web, Worker, Database)

- Web Tier - ALB - HTTP/S - Public
- Worker Tier - NLB - TCP/UDP - Private
- Database Tier - RDS - MySQL, Aurora, DynamoDB
- LB's allow each tier to scale independently

### Elastic Load Balancer - Cross Zone Load Balancing

- Cross Zone Load Balancing - Distribute traffic evenly across all instances in all AZs
- LB nodes in all AZs can accept traffic for all instances
- Enabled by default on ALB and NLB

### Application and Network Load Balancer (ALB vs NLB)

#### Load Balancer Consolidation

- CLBs don't scale well
- Every unique HTTPS name requires an individual CLB because SNI isn't supported
- v2 load balancers support rules and target groups
- Host based rules using SNI and a ALB allows consolidation

#### Application Load Balancer (ALB)

- Layer 7 Load balancer - HTTP/S, WebSockets
- No other Layer 7 protocols (SMTP, SSH, Gaming)
- No TCP/UDP/TLS Listeners
- L7 content type, cookies, custom headers, user location and app behaviour
- HTTP HTTPS (SSL/TLS) always terminated on the ALB - no unbroken SSL
- A new connection is made to the application
- ALBs MUST have SSL certs if HTTPS is used
- ALBs are slower than NLB .. more levels of the network stack to process
- Health checks evaluate application health ... Layer 7

#### Application Load Balancer - Rules

- Rules direct connections which arrive at a listener
- Processed in priority order
- Default rule = catchall
- Rule Conditions: host-header, http-header, http-request-method, path-pattern, query-string and source-ip
- Actions: forward, redirect, fixed-response, authenticate-oidc, authenticate-cognito

#### Network Load Balancer (NLB)

- Layer 4 Load Balancer - TCP, UDP, TLS, TCP_UDP
- No visibility or understanding of HTTP or HTTPS
- No headers, no cookies, no session stickiness
- Really fast millions of rps, 25% of ALB latency
- SMTP, SSH, Game Servers, financial services
- Health checks JUST check ICMP / TCP Handshake Not app aware
- NLB's can have static IP's - useful for whitelisting
- Forward TCP to instances .. unbroken encryption
- Used with private link to provide services to other VPCs

#### ALB vs NLB

- Unbroken encryption ... NLB
- Static IP for whitelisting ... NLB
- The fastest performance ... NLB (millions rps)
- Protocols not HTTP or HTTPS ... NLB
- Privatelink ... NLB
- Otherwise ... ALB

## User Sessoin State

Session State is a data representation of the interaction between a user and an application.

- Server-side piece of information
- Persists while you interact with that application
- Shopping Cart, Workflow Position or Login State
- Session State loss = User Experience (UX) Issues
- Session state stored on a server or externally

### User Session State - Session Stickiness

Session stickiness is a feature of AWS ELB's which allows applications which store session state internally on EC2 instances to function with load balancers

- With no Stickiness, connections are distributed across al in-service backend instances
- Unless an application correctly handles user-state this could cause user logoffs or shopping cart losses
- Stickiness is a feature of the ELB which allows connections from a user to be directed to the same backend instance
- AWSALB cookie or custom cookie, 1s to 7 days
- Stickiness generates a cookie which locks the device to a single backend instance for a duration

#### Stickiness Key Points

- Stickiness locks a session to 1 backend instance
- Creates AWSALB .. which is held by the client
- Sessions move on expiry or instance failure
- Enable if an application doesn't use external sessions
- Key words for exam - logout, lost carts, lost progress.. this suggests lost session state

## Gateway Load Balancer (GWLB)

Gateway Load Balancers enable you to deploy, scale, and manage virtual appliances, such as firewalls, intrusion detection and prevention systems, and deep packet inspection systems. It combines a transparent network gateway (that is, a single entry and exit point for all traffic) and distributes traffic while scaling your virtual appliances with the demand.

### Why do we need a GWLB?

- Transparent security appliance scans data after it leaves and before it enters the application instance
- This type of solution is tightly coupled and doesn't scale, even in a single app environment
- What about multi-tenent where a fleet of security appliances needs to protect many apps?

### Gateway Load Balancer - what is it?

- Help you run and scale 3rd party appliances
- things like firewalls, intrusion detection and prevention systems
- Inbound and Outbound traffic (transparent inspection and protection)
- GWLB endpoints ... traffic enters/leaves via these endpoints
- The GWLB balances across multiple backend appliances
- Traffic and metadata is tunnelled using GENEVE protocol

### Gateway Load Balancer - how it works

- GENEVE Encapsulation - Encapsulates traffic and metadata
- Original packets remain unaltered encapsulated through to appliances and back
- Ingress (gateway) route table directs any traffic destined for the ALB subnets at the Gateway Endpoint in the same AZ
- Original SRC and DST are maintained
- Packets are encapsulated and sent to the appliance
- Any outbound return traffic from the ALB is sent via default route to the Gateway LB endpoint

## Devops Security

### Web Application Firewall (WAF)

AWS WAF is a web application firewall that helps protect your web applications or APIs against common web exploits and bots that may affect availability, compromise security, or consume excessive resources.

- WAF is a Layer 7 Firewall
- WEB ACL - Web Access Control List
- Rules within Rule Groups
- Rule Groups within WEBACL
- Lambda Event Driven Processing of logs or event subscriptions
- Architecture is based on creating a feedback loop between logs generated by WAF
- Applications or ecosystems data to update WEBACL
- Logs can be stored in S3, CloudWatch logs or sent to Kinesis

### Web Access Control Lists (WEBACL)

- WEBACL Default Action (Allow or Block) - Non matching
- Resource Type - CloudFront or Regional Service
- ALB, API GW, AppSync pick region
- Add Rule Groups or Rules .. processed in order
- Web ACL Capacity Units (WCU) - Default 1500
- Can be increased via support ticket
- WEBACL's are associated with resources (this can take time)
- Adjusting a WEBACL takes less time than associating one

### Rule groups

- Rule Groups contain rules
- They don't have default actions ... that's defined when groups or rules are added to WEBACLs
- Managed (AWS or Marketplace) Yours, Service Owned (i.e. Shield and Firewall Manager)
- Rule groups can be referenced by multiple WEBACL
- Have a WCU capacity (defined upfront, max 1500)

### WAF Rules

- Type, Statement, Action
- Type: Regular or Rate-based
- Statement: (WHAT to match) or (COUNT ALL) or (WHAT and COUNT)
- Match against .. origin country, IP, label, header, cookies, query parameter, URI path, query string, body (first 8192 bytes ONLY), HTTP method
- Single, AND, OR, NOT
- Action: Allow, Block, Count, Captcha ... Custom Response (x-amzn-waf-), Label
- Labels can be referenced later in the same WEBACL .. multi-stage flows
- ALLOW and BLOCK stop processing, Count/Captcha actions continue

### WAF Pricing

- WEBACL - Monthly (per ACL) - $5 - these can be reused
- RULE on WEBACL - Monthly (per rule) - $1
- REQUESTS per WEBACL - $0.60 per million requests
- Intelligent Threat Mitigation
- Bot Control - $10 / month and $1 / 1million requests
- Captcha - ($0.40/1,00 challenge attempts)
- Fraud Control/Account Takeover ($10 / month and $1 / 1,000 login attempts)
- Marketplace Rule Groups - Extra costs

## AWS Network Firewall

AWS Network Firewall is a managed service that makes it easy to deploy essential network protections for all of your Amazon Virtual Private Clouds (VPCs)

- Requires a Firewall Subnet
- Traffic flows through Firewall Subnet into the Network Firewall
- Network Firewall sends the data back to the Firewall subnet
- Firewall Subnet sends the traffic into the Public Subnet

### AWS Network Firewall - Components

- Firewall - VPC, Subnets and Firewall Policy
- Firewall Policy - 1:M - defines filtering behaviour
- Rule Group - Collection of rules
- Either stateless or stateful
- Processing order and default action
- Rules - Traffic is evaluated against rules, pass, drop, forward

### AWS Network Firewall - Rule Groups

- Rule groups contain rules
- Customer created or AWS managed
- Defined upfront as stateful or stateless (type)
- Capacity .. limit on the processing requirements for the group (all the rules in the group)
- This cannot be changed afterwards

#### AWS Network Firewall - Stateless

- Inspects each packet in isolation - isn't state aware
- Request and Response are different
- INBOUND Request and OUTBOUND Request are different
- 5 Tuple - Protocol, SRC/DST CIDR, SRC/DST PORT
- Actions: Pass, Drop, Forward or Custom
- Processes in order .. then stops
- Default = lowest number = high priority

#### AWS Network Firewall - Stateful

- Uses suricata rules engine (open standard)
- Default = Pass, order = pass, drop, alert
- Rules = suricata format or built in standard for simple/domain list
- Simple = 5-Tuple w/ state (~SG)
- Domain list = domain names and protocol types
- Wildcards, headers(http), SNI (https)
- IPS Rules - Suricata compatible

## Connection Draining

- What happens when instances are unhealthy or deregistered
- Normally all connections are closed and no new connections
- Connection draining allows in-flight requests to complete
- CLASSIC LOAD BALANCER ONLY -defined on the CLB
- Timeout: Between 1 and 3,600 Seconds (default 300)
- InService: Instance deregistration currently in progress
- Auto Scaling waits for all connections to complete or Timeout

## Deregistration Delay

- Supported on ALB, NLB and GWLBs
- Defined on the Target group - NOT the LB
- Stops sending requests to deregistering targets
- Existing connections can continue
- Until they complete naturally
- Or the deregistration delay is reached
- Default 300 seconds (0-3600 seconds)

## X-Forwarded-For and PROXY Protocol

[X-Forwarded-For](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Forwarded-For)

[Proxy Protocol](https://www.haproxy.com/blog/use-the-proxy-protocol-to-preserve-a-clients-ip-address)

### X-Forwarded-For

- A set of HTTP headers (only works for HTTP/S) (Layer 7)
- X-Forwarded-For: client
- The header is added or appended by proxies/LBs
- The client is left most in the list
- X-Forwarded-For: 1.3.3.7, proxy1, proxy2
- LB adds header, containing IP
- Backend web server needs to be aware of this header
- Connections from LB, but X-Forwarded-For contains original client
- Supported ... CLB and ALB, NOT SUPPORTED NLB (not layer 4)

### PROXY Protocol

- Proxy Protocol works at Layer 4
- Additional layer 4 (tcp) header .. works with a range of protocols (including HTTP/s)
- Works with CLB (v1) and NLB (v2 - binary encoded)
- End to end encryption - e.g. unbroken HTTPS (tcp listener)
- Use PROXY Protocol, you can't add a HTTP header, it isn't decrypted

## Question Technique

### Keyword Identification

#### Question 1

A catagram.io Lambda function creates a _connection to a Database_ and _downloads some assets_ when executed.
You notice your costs for the lambda function are excessive because _every invocation_ is using _1 second_ to perform this _connection_ and _download_.
What options do you have to reduce costs and improve execution time? (Choose two)

#### Answers 1

- Change the runtime of the existing function ❌
- Use lambda savings plans ❌
- Store the assets in the /tmp folder ✅
- Store the assets in the /folder ❌
- Connect to the database within the function handler ❌
- Connect to the database outside of the function handler ✅
- Enable lambda execution environment persistence ❌

#### Question 2

A _Serverless_ application uses API Gateway to perform searches. API Gateway is configured with a _non proxy integration_ to a backing _lambda function_
which queries _DynamoDB_. You need to ensure that a _searchString parameter_ is _included_ in the _request_. What should you confirm to ensure this parameter is
required? (Choose one)

#### Answers 2

- Configure the integration response
- Configure the integration request
- Configure the API Gateway stage
- Configure the method request
- Configure the method response
