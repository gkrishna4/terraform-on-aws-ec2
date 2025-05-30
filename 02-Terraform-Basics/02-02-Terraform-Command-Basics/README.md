# Terraform Command Basics
  -  terraform init
  -  terraform validate
  -  terraform plan
  -  terraform apply
  -  terraform destroy
    

## Step-01: Introduction
- Understand basic Terraform Commands
  - terraform init :- Used to Initialize a working directory containing terraform config files,This is the first command that should be run
                      after writing a new Terraform configuration. And Downloads Providers.

  - terraform validate :- Validates the terraform configurations files in that respective directory to ensure they are syntactically valid and internally consistent.
    
  - terraform plan :-  Creates an execution plan, Terraform performs a refresh and determines what actions are necessary to achieve the desired state
                       specified in configuration files
    
  - terraform apply :- Used to apply the changes required to reach the desired state of the configuration. By default, apply scans the current directory
                       for the configuration and applies the changes appropriately.

  - terraform destroy :- Used to destroy the Terraform-managed infrastructure, This will ask for confirmation before destroying
    

## Step-02: Review terraform manifest for EC2 Instance
- **Pre-Conditions-1:** Ensure you have **default-vpc** in that respective region
- **Pre-Conditions-2:** Ensure AMI you are provisioning exists in that region if not update AMI ID 
- **Pre-Conditions-3:** Verify your AWS Credentials in **$HOME/.aws/credentials**
```t
# Terraform Settings Block
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      #version = "~> 3.21" # Optional but recommended in production
    }
  }
}

# Provider Block
provider "aws" {
  profile = "default" # AWS Credentials Profile configured on your local desktop terminal  $HOME/.aws/credentials
  region  = "us-east-1"
}

# Resource Block
resource "aws_instance" "ec2demo" {
  ami           = "ami-04d29b6f966df1537" # Amazon Linux in us-east-1, update as per your region
  instance_type = "t2.micro"
}
```

## Step-03: Terraform Core Commands
```t
# Initialize Terraform
terraform init

# Terraform Validate
terraform validate

# Terraform Plan to Verify what it is going to create / update / destroy
terraform plan

# Terraform Apply to Create EC2 Instance
terraform apply 
```

## Step-04: Verify the EC2 Instance in AWS Management Console
- Go to AWS Management Console -> Services -> EC2
- Verify newly created EC2 instance



## Step-05: Destroy Infrastructure
```t
# Destroy EC2 Instance
terraform destroy

# Delete Terraform files 
rm -rf .terraform*
rm -rf terraform.tfstate*
```

## Step-08: Conclusion
- Re-iterate what we have learned in this section
- Learned about Important Terraform Commands
  - terraform init
  - terraform validate
  - terraform plan
  - terraform apply
  - terraform destroy     



