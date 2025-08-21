Description:
A reusable Terraform module to create and manage AWS Security Groups with customizable ingress and egress rules.

Key Features:

Create Security Groups inside a given VPC

Support for multiple ingress/egress rules

Allows CIDR blocks, SG IDs, and self-referencing rules

Fully supports tagging

Example Usage:
A developer using your module would write:

module "security_group" {
  source = "git::https://github.com/<your-username>/terraform-aws-securitygroup-module.git"

  vpc_id = "vpc-123456"

  ingress_rules = [
    {
      from_port   = 22
      to_port     = 22
      protocol    = "tcp"
      cidr_blocks = ["0.0.0.0/0"]
    }
  ]

  egress_rules = [
    {
      from_port   = 0
      to_port     = 0
      protocol    = "-1"
      cidr_blocks = ["0.0.0.0/0"]
    }
  ]
}


Inputs:

vpc_id → VPC ID where SG will be created

ingress_rules → List of ingress rules

egress_rules → List of egress rules

Outputs:

security_group_id → ID of the created Security Group
