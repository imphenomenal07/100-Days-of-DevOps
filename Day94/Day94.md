# Day 94: Create VPC Using Terraform

# 1. First the file 'provider.tf', if everything is fine

# 2. Create a 'main.tf' file under terraform directory

#File Content:

resource "aws_vpc" "datacenter_vpc" {
  cidr_block           = "10.0.0.0/16"
  enable_dns_support   = true
  enable_dns_hostnames = true

  tags = {
    Name = "datacenter-vpc"
  }
}

# 3. Open terminal and create infra

$ terraform init
$ terraform plan
$ terraform validate
$ terraform apply
