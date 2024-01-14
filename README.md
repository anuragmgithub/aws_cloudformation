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

### Does the order of resource definitions matter? ?
The order of resource declaration within a CloudFormation template doesn't usually matter, but defining dependencies correctly is crucial for successful stack creation.