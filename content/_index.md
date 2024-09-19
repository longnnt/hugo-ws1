+++
title = "Home"
date = 2024-09-07T19:01:00+07:00
weight = 1
url = '/hugo-ws1'
chapter = true
pre = "<b>X. </b>"
+++

### Chapter X

# CI/CD using codepipeline AWS deploy react app to EC2

![alt text](ci_cd-aws.drawio.png)

### Information about this workshop

#### 1. What is CI/CD ?
- **Continuous integration (CI)** refers to the practice of automatically and frequently integrating code changes into a shared source code repository
- **Continuous delivery and/or deployment (CD)** is a 2 part process that refers to the integration, testing, and delivery of code changes
#### 2. This workshop used to 6 main services
- **VPC**: A VPC is a virtual network that closely resembles a traditional network that you'd operate in your own data center.
- **EC2**: Using for run reactjs app.
- **S3 Bucket**: Using for store source code, buildspec config, build folder result after phase Build.
- **AWS CodeBuild**: Using for phase Build in CodePipeline
- **AWS CodeDeploy**: Using for phase Deploy in CodePipeline
- **AWS CodePipeline**: Combination CodeBuild and CodeDeploy.