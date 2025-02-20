AWS EC2 and VPC Setup

## Overview
This project demonstrates  to create a Virtual Private Cloud (VPC) and launch an EC2 instance within it.

### AWS Services Used:
- **VPC**: Virtual network for isolated resources.
- **EC2**: Elastic Compute Cloud for running instances.
- **Security Groups**: Virtual firewalls for instances.

### Steps:
1. **Create a VPC** with public and private subnets.
2. **Launch an EC2 instance** inside the VPC.
3. **Configure Security Group** to allow SSH and HTTP access.

### Code (Terraform Example):
```terraform
resource "aws_vpc" "main" {
  cidr_block = "10.0.0.0/16"
}

resource "aws_security_group" "allow_http_ssh" {
  name = "allow_http_ssh"
  ingress {
    from_port   = 22
    to_port     = 22
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }
  ingress {
    from_port   = 80
    to_port     = 80
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }
}

