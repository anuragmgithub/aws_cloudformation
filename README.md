# AWS CloudFormation Templates for Infrastructure as Code (IaC) Overview
This repository contains multiple CloudFormation templates designed for managing Infrastructure as Code (IaC). CloudFormation is a service provided by Amazon Web Services (AWS) that allows you to define and provision AWS infrastructure in a declarative manner.

## Usage of Fn::Base64
One common usage in the provided templates involves the intrinsic function Fn::Base64. This function returns the Base64 representation of the input string. It is often employed to encode data passed to Amazon EC2 instances through the UserData property...

# Usage of parameters
Parameters enable you to input custom values to your template each time you create or update a stack.
General requirements for parameters:
1. You can have a maximum of 200 parameters in an AWS CloudFormation template.
2. Each parameter must be assigned a parameter type that is supported by AWS CloudFormation. For more information
SSM Parameter Types:
SSM parameter types correspond to existing parameters in Systems Manager Parameter Store. You specify a Systems Manager parameter key as the value of the SSM parameter, and AWS CloudFormation fetches the latest value from Parameter Store to use for the stack. 
Supported AWS-specific parameter types:
AWS::EC2::AvailabilityZone::Name
AWS::EC2::Image::Id
AWS::EC2::Instance::Id
AWS::EC2::KeyPair::KeyName
AWS::EC2::SecurityGroup::GroupName
An EC2-Classic or default VPC security group name, such as my-sg-abc.

AWS::EC2::SecurityGroup::Id
A security group ID, such as sg-a123fd85.

AWS::EC2::Subnet::Id
A subnet ID, such as subnet-123a351e.

AWS::EC2::Volume::Id
An Amazon EBS volume ID, such as vol-3cdd3f56.

AWS::EC2::VPC::Id
A VPC ID, such as vpc-a123baa3.

#### SSM - AWS Systems Manager Parameter Store

Parameter Store, a capability of AWS Systems Manager, provides secure, hierarchical storage for configuration data management and secrets management. You can store data such as passwords, database strings, Amazon Machine Image (AMI) IDs, and license codes as parameter values. You can store values as plain text or encrypted data. 
Note: To implement password rotation lifecycles, use AWS Secrets Manager. You can rotate, manage, and retrieve database credentials, API keys, and other secrets throughout their lifecycle using Secrets Manager. Parameter Store is also integrated with Secrets Manager. You can retrieve Secrets Manager secrets when using other AWS services that already support references to Parameter Store parameters. 
Accessible from other AWS services:

Amazon Elastic Compute Cloud (Amazon EC2)

Amazon Elastic Container Service (Amazon ECS)

AWS Secrets Manager

AWS Lambda

AWS CloudFormation

AWS CodeBuild

AWS CodePipeline

AWS CodeDeploy

Integrate with other AWS services

Configure integration with the following AWS services for encryption, notification, monitoring, and auditing:

AWS Key Management Service (AWS KMS)

Amazon Simple Notification Service (Amazon SNS)

Assigning parameter policies:
Parameter policies help you manage a growing set of parameters by allowing you to assign specific criteria to a parameter such as an expiration date or time to live. Parameter policies are especially helpful in forcing you to update or delete passwords and configuration data stored in Parameter Store, a capability of AWS Systems Manager. Parameter Store offers the following types of policies: Expiration, ExpirationNotification, and NoChangeNotification.
Add policies to an existing parameter (AWS CLI)
aws ssm put-parameter   
    --name "parameter name" \
    --value 'parameter value' \
    --type parameter type \
    --overwrite \
    --policies "[{policies-enclosed-in-brackets-and-curly-braces}]"

### Does the order of resource definitions matter? ?
The order of resource declaration within a CloudFormation template doesn't usually matter, but defining dependencies correctly is crucial for successful stack creation.