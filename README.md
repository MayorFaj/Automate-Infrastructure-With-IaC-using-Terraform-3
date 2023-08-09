# Automate-Infrastructure-With-IaC-using-Terraform-Part-3
Project 18

This project is a continuatioin of project 16 and 17. In this project i refactored the codes using modules to produce reusable and comprehensive IaC code structure and intoduced backend on S3.

- Modules serve as containers that allows for logical grouping of Terraform codes for similar resources in the same domain (e.g., Compute, Networking, AMI, etc.). One root module can call other child modules and insert their configurations when applying Terraform config. This concept makes  code structure neater, and it allows different team members to work on different parts of configuration at the same time.

- In previous projects, i have been using the default backend (i.e the local backend), where the state files are stored locally. Storing files locally has its limitations, one of the limitations is that it doesn't allow for collaboration within a team of multiple DevOps engineers, as others can't have access to a state file stored locally.To solve this, i configured a backend where the state file can be accessed remotely by other DevOps team members. There are plenty of different standard backends supported by Terraform that you can choose from. Since i am using AWS, i choosed an S3 bucket as a backend.

- Another useful option that is supported by S3 backend is `State Locking` – it is used to lock your state for all operations that could write state. This prevents others from acquiring the lock and potentially corrupting your state. State Locking feature for S3 backend is optional and requires another AWS service – **DynamoDB**.

