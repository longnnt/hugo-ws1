+++
title = 'Create deployment'
date = 2024-09-07T19:01:58+07:00
draft = false
weight = 5
pre = "<b>5.4. </b>"
+++

1. Create code deployment config:
```bash
vi codedeployment.yaml
```
```yaml
applicationName: "codedeploy-application"
deploymentGroupName: "codedeploy-group-name"
revision:
    revisionType: "S3"
    s3Location:
        bucket: "codepipeline-ap-southeast-1-nntl-example"
        key: "my-build-artifact.zip"
        bundleType: "zip"
```
Specifying:
- **revision**: Define location using for deployment in s3 location and folder compressed zip exported in phase build
- **applicationName**: Name of application created
- **deploymentGroupName**: Name of deployment group created
```console
aws deploy create-deployment --cli-input-yaml file://codedeployment.yaml
```
**Result**
![alt text](image-33.png)




