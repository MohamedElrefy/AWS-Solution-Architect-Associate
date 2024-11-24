# AWS Architecture for Scalable Infrastructure

## Overview
This project demonstrates the design of a scalable, secure, and highly available infrastructure using AWS services. The setup is managed through the AWS Management Console.

## Architecture Diagram
![AWS Architecture Diagram]('/home/mohamed/Desktop/AWS/Project Structure.jpeg' )

## Components
- **VPC**: CIDR 10.0.0.0/16 with multiple subnets across two Availability Zones.
- **Subnets**:
  - Public: 10.0.10.0/24, 10.0.20.0/24
  - Private: 10.0.100.0/24, 10.0.200.0/24
- **NAT Gateway**: For outbound internet access from private subnets.
- **Route 53**: For DNS management.
- **SQS Queue**: Decoupled messaging between services.
- **Amazon RDS**: Relational database in private subnets.
- **EBS Volumes**: Persistent storage for EC2 instances.
- **IAM**: Access control with roles and policies.

## Steps to Recreate
To set up this architecture manually:
1. **VPC and Subnets**:
   - Create a VPC with CIDR `10.0.0.0/16`.
   - Add subnets as shown in the diagram.
2. **Internet Gateway and Route Tables**:
   - Attach an Internet Gateway to the VPC if not the default.
   - Configure route tables for public and private subnets.
3. **NAT Gateway**:
   - Set up a NAT Gateway in a public subnet.
   - Update private subnets' route tables for outbound internet access.
4. **EC2 Instances**:
   - Launch instances in private and public subnets as needed.
   - Attach EBS volumes.
5. **Amazon RDS**:
   - Create an RDS instance in private subnets.
6. **SQS Queue**:
   - Create an SQS queue for inter-service communication.
7. **Route 53**:
   - Configure DNS for custom domains.
8. **IAM Roles**:
   - Set up roles for EC2 and RDS with necessary policies.

## Security Considerations
- Ensure that Security Groups and Network NACLs are properly configured.
- Use IAM roles instead of embedding credentials in applications.

## Future Enhancements
- Automate the setup using Terraform or CloudFormation.
- Add monitoring and logging using CloudWatch.

