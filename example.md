terraform init
Initializing the backend...
Initializing provider plugins...
- Finding hashicorp/aws versions matching "~> 5.0"...
- Installing hashicorp/aws v5.62.0...
Terraform has been successfully initialized!
terraform validate
Success! The configuration is valid.
terraform plan
Terraform will perform the following actions:
 
  # aws_security_group.web will be created
  + resource "aws_security_group" "web" {
      + id = (known after apply)
      + name = "web-sg"
      + description = "Allow HTTP and SSH"
      + vpc_id = (known after apply)
    }
  # aws_instance.web will be created
  + resource "aws_instance" "web" {
      + id = (known after apply)
      + instance_type = "t3.micro"
      + ami = "ami-0c55b159cbfafe1f0"
      + public_ip = (known after apply)
    }
  # aws_s3_bucket.assets will be created
  + resource "aws_s3_bucket" "assets" {
      + id = (known after apply)
      + bucket = "devops-daily-assets"
      + region = "us-east-1"
    }
 
Plan: 3 to add, 0 to change, 0 to destroy.
terraform apply -auto-approve
Terraform will perform the following actions:
 
  # aws_security_group.web will be created
  + resource "aws_security_group" "web" {
      + id = (known after apply)
      + name = "web-sg"
      + description = "Allow HTTP and SSH"
      + vpc_id = (known after apply)
    }
  # aws_instance.web will be created
  + resource "aws_instance" "web" {
      + id = (known after apply)
      + instance_type = "t3.micro"
      + ami = "ami-0c55b159cbfafe1f0"
      + public_ip = (known after apply)
    }
  # aws_s3_bucket.assets will be created
  + resource "aws_s3_bucket" "assets" {
      + id = (known after apply)
      + bucket = "devops-daily-assets"
      + region = "us-east-1"
    }
 
Plan: 3 to add, 0 to change, 0 to destroy.
 
aws_security_group.web: Creating...
aws_security_group.web: Creation complete [id=sg-07da7af1bd21de402]
aws_instance.web: Creating...
aws_instance.web: Creation complete [id=i-0dd2e99ada3c97b29]
aws_s3_bucket.assets: Creating...
aws_s3_bucket.assets: Creation complete [id=devops-daily-assets]
 
Apply complete! Resources: 3 added, 0 changed, 0 destroyed.
 
Outputs:
instance_id = "i-0dd2e99ada3c97b29"
instance_public_ip = "54.227.178.181"
bucket_name = "devops-daily-assets"
terraform plan
No changes. Your infrastructure matches the configuration.
terraform plan
Terraform will perform the following actions:
 
  # aws_instance.web will be updated in-place
  ~ resource "aws_instance" "web" {
      ~ instance_type = "t3.micro" -> "t3.small"
    }
 
Plan: 0 to add, 1 to change, 0 to destroy.
terraform apply -auto-approve
Terraform will perform the following actions:
 
  # aws_instance.web will be updated in-place
  ~ resource "aws_instance" "web" {
      ~ instance_type = "t3.micro" -> "t3.small"
    }
 
Plan: 0 to add, 1 to change, 0 to destroy.
 
aws_instance.web: Modifying... [id=i-0dd2e99ada3c97b29]
aws_instance.web: Modifications complete
 
Apply complete! Resources: 0 added, 1 changed, 0 destroyed.
 
Outputs:
instance_id = "i-0dd2e99ada3c97b29"
instance_public_ip = "54.227.178.181"
bucket_name = "devops-daily-assets"
terraform state list
aws_security_group.web
aws_instance.web
aws_s3_bucket.assets
terraform output
instance_id = "i-0dd2e99ada3c97b29"
instance_public_ip = "54.227.178.181"
bucket_name = "devops-daily-assets"
terraform destroy -auto-approve
Terraform will perform the following actions:
 
  # aws_security_group.web will be destroyed
  - resource "aws_security_group" "web"
  # aws_instance.web will be destroyed
  - resource "aws_instance" "web"
  # aws_s3_bucket.assets will be destroyed
  - resource "aws_s3_bucket" "assets"
 
Plan: 0 to add, 0 to change, 3 to destroy.
 
aws_s3_bucket.assets: Destroying... [id=devops-daily-assets]
aws_instance.web: Destroying... [id=i-0dd2e99ada3c97b29]
aws_security_group.web: Destroying... [id=sg-07da7af1bd21de402]
 
Destroy complete! Resources: 3 destroyed.
