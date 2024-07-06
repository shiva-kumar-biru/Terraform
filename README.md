# Setting up on Infrastructure on AWS using Terraform.





## Architecture

1. **VPC**: A Virtual Private Cloud with a custom CIDR block.
2. **Subnets**: Two public subnets in different availability zones.
3. **Internet Gateway**: For internet access.
4. **Route Table**: Routes for internet access.
5. **Security Group**: Allow HTTP and SSH access.
6. **EC2 Instances**: Two web servers in different subnets.
7. **Application Load Balancer (ALB)**: Distributes traffic across the web servers.
8. **S3 Bucket**: A simple S3 bucket.

![Architecture](/Users/shivakumarbiru/Desktop/Github/Terraform/terraformscripts/architecture.png)



## Prerequisites

- [Terraform](https://www.terraform.io/downloads.html) installed on your local machine.
- AWS credentials configured. You can use the [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) to configure them.


## Resources

The following AWS resources are created:

- **VPC**:
  - `aws_vpc.myvpc`
  
  ![vpc](https://github.com/shiva-kumar-biru/Terraform/blob/main/terraformscripts/docs/vpc.png)

- **Subnets**:
  - `aws_subnet.sub1`
  - `aws_subnet.sub2`

![subnet](https://github.com/shiva-kumar-biru/Terraform/blob/main/terraformscripts/docs/subnet.png)

- **Internet Gateway**:
  - `aws_internet_gateway.igw`

![IG](https://github.com/shiva-kumar-biru/Terraform/blob/main/terraformscripts/docs/IG.png)


- **Route Table**:
  - `aws_route_table.RT`
  - `aws_route_table_association.rta1`
  - `aws_route_table_association.rta2`
 
![routetable](https://github.com/shiva-kumar-biru/Terraform/blob/main/terraformscripts/docs/routetable.png)


- **Security Group**:
  - `aws_security_group.webSg`

- **S3 Bucket**:
  - `aws_s3_bucket.example`

![bucket](https://github.com/shiva-kumar-biru/Terraform/blob/main/terraformscripts/docs/bucket.png)

- **EC2 Instances**:
  - `aws_instance.webserver1`
  - `aws_instance.webserver2`

![instance](https://github.com/shiva-kumar-biru/Terraform/blob/main/terraformscripts/docs/instance.png)
![ec1](https://github.com/shiva-kumar-biru/Terraform/blob/main/terraformscripts/docs/ec1.png)
![ec2](https://github.com/shiva-kumar-biru/Terraform/blob/main/terraformscripts/docs/ec2.png)


- **Application Load Balancer**:
  - `aws_lb.myalb`
  - `aws_lb_target_group.tg`
  - `aws_lb_target_group_attachment.attach1`
  - `aws_lb_target_group_attachment.attach2`
  - `aws_lb_listener.listener`

![lb](https://github.com/shiva-kumar-biru/Terraform/blob/main/terraformscripts/docs/lb.png)
![tg](https://github.com/shiva-kumar-biru/Terraform/blob/main/terraformscripts/docs/TG.png)
![listener](https://github.com/shiva-kumar-biru/Terraform/blob/main/terraformscripts/docs/listener.png)




## Load Balancer Traffic Distribution

The Application Load Balancer (ALB) is set up to distribute incoming HTTP traffic across two EC2 instances (`webserver1` and `webserver2`). The ALB ensures high availability and reliability by spreading the traffic, which helps in managing the load efficiently and providing a seamless user experience.


!(dns1)[https://github.com/shiva-kumar-biru/Terraform/blob/main/terraformscripts/docs/dns1.png]

!(dns2)[https://github.com/shiva-kumar-biru/Terraform/blob/main/terraformscripts/docs/dns2.png]

## Conclusion

This Terraform configuration provides a robust and scalable infrastructure on AWS, featuring a VPC with public subnets, an internet gateway, security groups, and two EC2 instances behind an Application Load Balancer. It serves as a foundational setup for hosting web applications or other services requiring high availability and internet access. By using this configuration, you can quickly deploy a reliable environment, ensuring your web servers are securely accessible through the load balancer. Additionally, the configuration is easy to extend and customize according to your project's specific needs.
