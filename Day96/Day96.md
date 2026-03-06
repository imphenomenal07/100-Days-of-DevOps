# Day 96: Create EC2 Instance Using Terraform

# 1. First check the file 'provider.tf', if everything is fine

# 2. Create a 'main.tf' file under terraform directory

#File Content:

resource "tls_private_key" "nautilus_key" {
  algorithm = "RSA"
  rsa_bits  = 4096
}

resource "aws_key_pair" "nautilus_kp" {
  key_name   = "nautilus-kp"
  public_key = tls_private_key.nautilus_key.public_key_openssh
}

resource "aws_instance" "nautilus-ec2" {
  ami                    = "ami-0c101f26f147fa7fd"
  instance_type          = "t2.micro"
  key_name               = aws_key_pair.nautilus_kp.key_name
  #vpc_security_group_ids = ["sg-default"]

  tags = {
    Name = "nautilus-ec2"
  }
}

#There is any SG/SG-ID mentioned, update that accordingly

# 3. Open terminal and create infra

$ terraform init
$ terraform plan
$ terraform validate
$ terraform apply

#Troubleshoot and fix the errors, if any!!
