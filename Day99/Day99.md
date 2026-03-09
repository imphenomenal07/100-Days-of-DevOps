# Day 99: Attach IAM Policy for DynamoDB Access Using Terraform

# 1. First check the file 'provider.tf', if everything is fine

# 2. Create a 'main.tf' file under terraform directory

#File Content:

#DynamoDB Table
resource "aws_dynamodb_table" "nautilus_table" {
  name         = var.KKE_TABLE_NAME
  billing_mode = "PAY_PER_REQUEST"
  hash_key     = "id"

  attribute {
    name = "id"
    type = "S"
  }
}

#IAM Role
resource "aws_iam_role" "nautilus_role" {
  name = var.KKE_ROLE_NAME

  assume_role_policy = jsonencode({
    Version = "2012-10-17"
    Statement = [
      {
        Effect = "Allow"
        Principal = {
          Service = "ec2.amazonaws.com"
        }
        Action = "sts:AssumeRole"
      }
    ]
  })
}

#IAM Policy (Read Only for DynamoDB Table)
resource "aws_iam_policy" "nautilus_readonly_policy" {
  name = var.KKE_POLICY_NAME

  policy = jsonencode({
    Version = "2012-10-17"
    Statement = [
      {
        Effect = "Allow"
        Action = [
          "dynamodb:GetItem",
          "dynamodb:Scan",
          "dynamodb:Query"
        ]
        Resource = aws_dynamodb_table.nautilus_table.arn
      }
    ]
  })
}

#Attach Policy to Role
resource "aws_iam_role_policy_attachment" "attach_policy" {
  role       = aws_iam_role.nautilus_role.name
  policy_arn = aws_iam_policy.nautilus_readonly_policy.arn
}

# 3: Create 'variables.tf' file

#File Content:

variable "KKE_TABLE_NAME" {
  description = "Name of the DynamoDB table"
  type        = string
}

variable "KKE_ROLE_NAME" {
  description = "Name of the IAM role"
  type        = string
}

variable "KKE_POLICY_NAME" {
  description = "Name of the IAM policy"
  type        = string
}

# 4: Create 'outputs.tf' file

#File Content:

output "kke_dynamodb_table" {
  value = aws_dynamodb_table.nautilus_table.name
}

output "kke_iam_role_name" {
  value = aws_iam_role.nautilus_role.name
}

output "kke_iam_policy_name" {
  value = aws_iam_policy.nautilus_readonly_policy.name
}

# 5. Create 'terraform.tfvars' file

#File Content:

KKE_TABLE_NAME  = "nautilus-table"
KKE_ROLE_NAME   = "nautilus-role"
KKE_POLICY_NAME = "nautilus-readonly-policy"KKE_TABLE_NAME  = "nautilus-table"
KKE_ROLE_NAME   = "nautilus-role"
KKE_POLICY_NAME = "nautilus-readonly-policy"

# 6. Open bash terminal and run the below commands to create infra

$ terraform init
$ terraform plan
$ terraform validate
$ terraform apply

#There is any error, find it and fix it !!
