# AWS CloudFormation Templates for Infrastructure as Code (IaC) Overview
This repository contains multiple CloudFormation templates designed for managing Infrastructure as Code (IaC). CloudFormation is a service provided by Amazon Web Services (AWS) that allows you to define and provision AWS infrastructure in a declarative manner.

## Usage of Fn::Base64
One common usage in the provided templates involves the intrinsic function Fn::Base64. This function returns the Base64 representation of the input string. It is often employed to encode data passed to Amazon EC2 instances through the UserData property.