# Day 97: Create IAM Policy Using Terraform

# 1. First check the file 'provider.tf', if everything is fine

# 2. Create a 'main.tf' file under terraform directory

#File Content:

resource "aws_iam_policy" "iampolicy_kirsty" {
  name        = "iampolicy_kirsty"
  description = "Read-only access to EC2 instances, AMIs, and snapshots"

  policy = jsonencode({
    Version = "2012-10-17"
    Statement = [
      {
        Effect = "Allow"
        Action = [
          "ec2:DescribeInstances",
          "ec2:DescribeImages",
          "ec2:DescribeSnapshots",
          "ec2:DescribeTags",
          "ec2:DescribeVolumes",
          "ec2:DescribeInstanceStatus"
        ]
        Resource = "*"
      }
    ]
  })
}

# 3. Open bash terminal of code editor and create infra

$ terraform init
$ terraform plan
$ terraform validate
$ terraform apply

#Troubleshoot and fix the errors, if any!!
