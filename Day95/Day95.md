# Day 95: Create Security Group Using Terraform

# 1. First check the file 'provider.tf', if everything is fine

# 2. Create a 'main.tf' file under terraform directory

#File Content:

resource "aws_security_group" "xfusion_sg" {
  name        = "xfusion-sg"
  description = "Security group for Nautilus App Servers"
  #vpc_id      = data.aws_vpc.default.id

  tags = {
    Name = "xfusion-sg"
  }
}

resource "aws_vpc_security_group_ingress_rule" "http_rule" {
  security_group_id = aws_security_group.xfusion_sg.id

  cidr_ipv4   = "0.0.0.0/0"
  from_port   = 80
  ip_protocol = "tcp"
  to_port     = 80
}

resource "aws_vpc_security_group_ingress_rule" "ssh_rule" {
  security_group_id = aws_security_group.xfusion_sg.id

  cidr_ipv4   = "0.0.0.0/0"
  from_port   = 22
  ip_protocol = "tcp"
  to_port     = 22
}

#There is any VPC/VPC-ID mentioned, update that accordingly

# 3. Open terminal and create infra

$ terraform init
$ terraform plan
$ terraform validate
$ terraform apply

#Troubleshoot and fix the errors, if any!!
