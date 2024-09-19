+++
title = 'Create service role for codebuild'
date = 2024-09-07T19:01:58+07:00
draft = false
weight = 2
pre = "<b>4.1. </b>"
+++
---
1. Create IAM Policy for codebuild:
   -   **Codebuild** is just needed to get data from the source saved in s3 and save build output artifacts to s3. I just configured two actions for read and write.
   -   **Resource**: ARN of s3 we created in previous ([section]([#1-codebuild](/pre-install/create-s3/#create-s3-bucket-using-cli)))
<!-- - Need to change this -->

```bash
vi codebuild-policy.json
```

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": ["s3:get*", "s3:putObject", "s3:ListBucket"],
            "Resource": "arn:aws:s3:::codepipeline-ap-southeast-1-*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "logs:CreateLogStream"
            ],
            "Resource": "*"
        }
    ]
}
```

```console
aws iam create-policy --policy-name CodeBuildPolicy --policy-document file://codebuild-policy.json
```
---
2. Create IAM Role for codebuild
```bash
vi codebuild-role-document.json
```

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "codebuild.amazonaws.com"
            },
            "Action": "sts:AssumeRole"
        }
    ]
}
```

```console
aws iam create-role --role-name CodeBuildRole --assume-role-policy-document file://codebuild-role-document.json
```

**Result**
```json
// Output after run cli
{
    "Role": {
        "Path": "/",
        "RoleName": "CodeBuildRole",
        "RoleId": "AROAQMEY6BIJ2TJMARGR4",
        "Arn": "arn:aws:iam::xxxxxxxxxx:role/CodeBuildRole",
        "CreateDate": "2024-09-07T03:31:11+00:00",
        "AssumeRolePolicyDocument": {
            "Version": "2012-10-17",
            "Statement": [
                {
                    "Effect": "Allow",
                    "Principal": {
                        "Service": "codebuild.amazonaws.com"
                    },
                    "Action": "sts:AssumeRole"
                }
            ]
        }
    }
}
```
---
3. Attach policy to role:

```console
aws iam attach-role-policy --role-name CodeBuildRole --policy-arn arn:aws:iam::xxxxxxxxxx:policy/CodeBuildPolicy
```


