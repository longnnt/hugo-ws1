+++
title = 'Create role and policy for codepipeline'
date = 2024-09-07T19:01:58+07:00
draft = false
weight = 2
pre = "<b>6.1. </b>"
+++

1. Create role using for codepipeline:
   - Need to access role **EC2, codebuild, codedeploy, codestar connections**

```bash 
vi codepipeline-policy.json
```

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "codedeploy:CreateDeployment",
                "codedeploy:GetApplication",
                "codedeploy:GetApplicationRevision",
                "codedeploy:GetDeployment",
                "codedeploy:GetDeploymentConfig",
                "codedeploy:RegisterApplicationRevision"
            ],
            "Resource": "*",
            "Effect": "Allow"
        },
        {
            "Action": ["codestar-connections:UseConnection"],
            "Resource": "*",
            "Effect": "Allow"
        },
        {
            "Action": ["ec2:*", "s3:*"],
            "Resource": "*",
            "Effect": "Allow"
        },
        {
            "Action": [
                "codebuild:BatchGetBuilds",
                "codebuild:StartBuild",
                "codebuild:BatchGetBuildBatches",
                "codebuild:StartBuildBatch"
            ],
            "Resource": "*",
            "Effect": "Allow"
        }
    ]
}
```

```bash
codepipeline-role-document.json
```

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "codepipeline.amazonaws.com"
            },
            "Action": "sts:AssumeRole"
        }
    ]
}
```
---
2. Create and attach role policy cli:

```console
aws iam create-policy --policy-name CodepipelinePolicy --policy-document file://codepipeline-policy.json
aws iam create-role --role-name CodepipelineRole --assume-role-policy-document file://codepipeline-role-document.json
aws iam attach-role-policy --role-name CodepipelineRole --policy-arn arn:aws:iam::xxxxxxxxxx:policy/CodepipelinePolicy
```




