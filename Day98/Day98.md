# Day 98: Launch EC2 in Private VPC Subnet Using Terraform

# 1. First check the file 'provider.tf', if everything is fine

# 2. Create a 'main.tf' file under terraform directory

#File Content:

resource "aws_vpc" "devops_vpc" {
  cidr_block = var.KKE_VPC_CIDR

  tags = {
    Name = "devops-priv-vpc"
  }
}

resource "aws_subnet" "devops_subnet" {
  vpc_id                  = aws_vpc.devops_vpc.id
  cidr_block              = var.KKE_SUBNET_CIDR
  map_public_ip_on_launch = false

  tags = {
    Name = "devops-priv-subnet"
  }
}

resource "aws_security_group" "devops_sg" {
  name   = "devops-priv-sg"
  vpc_id = aws_vpc.devops_vpc.id

  ingress {
    from_port   = 0
    to_port     = 0
    protocol    = "-1"
    cidr_blocks = [var.KKE_VPC_CIDR]
  }

  egress {
    from_port   = 0
    to_port     = 0
    protocol    = "-1"
    cidr_blocks = ["0.0.0.0/0"]
  }

  tags = {
    Name = "devops-priv-sg"
  }
}

resource "aws_instance" "devops_ec2" {
  ami                    = "ami-0c02fb55956c7d316"
  instance_type          = "t2.micro"
  subnet_id              = aws_subnet.devops_subnet.id
  vpc_security_group_ids = [aws_security_group.devops_sg.id]

  tags = {
    Name = "devops-priv-ec2"
  }
}

# 3. Create 'variables.tf' file

#File Content:

variable "KKE_VPC_CIDR" {
  description = "CIDR block for VPC"
  type        = string
  default     = "10.0.0.0/16"
}

variable "KKE_SUBNET_CIDR" {
  description = "CIDR block for Subnet"
  type        = string
  default     = "10.0.1.0/24"
}

# 4. Create 'outputs.tf' file

#File Content:

output "KKE_vpc_name" {
  value = aws_vpc.devops_vpc.tags["Name"]
}

output "KKE_subnet_name" {
  value = aws_subnet.devops_subnet.tags["Name"]
}

output "KKE_ec2_private" {
  value = aws_instance.devops_ec2.tags["Name"]
}

# 5. Open bash terminal of code editor and create infra

$ terraform init
$ terraform plan
$ terraform validate
$ terraform apply

#Troubleshoot and fix the errors, if any!!
