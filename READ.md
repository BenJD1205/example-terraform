Terraform basics, explained
Terraform is an infrastructure as code (IaC) tool. Instead of clicking through a cloud console, you describe the infrastructure you want in configuration files, and Terraform figures out how to create, change, or destroy it to match. This lab teaches that loop hands-on. Below is the background to go with it.

The building blocks (HCL)
provider: the plugin Terraform uses to talk to a platform, such as AWS, Azure, or GCP.
resource: a single piece of infrastructure, like an EC2 instance or an S3 bucket.
variable: an input you can change without editing the main config, such as region or instance size.
output: a value Terraform exposes after apply, like an instance IP, for you or other tools to read.
state: Terraform's record of what it created, so it knows what to change next time.
The core workflow
terraform init: download providers and prepare the directory. Run it first.
terraform validate: check the config is syntactically valid.
terraform plan: preview the changes. + create, ~ change, - destroy.
terraform apply: make the changes and write them to state.
terraform destroy: tear everything down so it stops costing money.
