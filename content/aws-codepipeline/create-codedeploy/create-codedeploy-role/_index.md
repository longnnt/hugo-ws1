+++
title = 'Create service role for codedeploy'
date = 2024-09-07T19:01:58+07:00
draft = false
weight = 2
pre = "<b>4.2.2. </b>"
+++

### Create role and policy for deployment group:

```bash 
codedeploy-policy.json
```

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:DescribeInstances",
                "ec2:DescribeInstanceStatus",
                "ec2:TerminateInstances"
            ],
            "Resource": "*"
        }
    ]
}
```

```bash
vi codedeploy-role-document.json
```

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "codedeploy.amazonaws.com"
            },
            "Action": "sts:AssumeRole"
        }
    ]
}
```

Create and attach role policy cli:

```console
aws iam create-policy --policy-name CodeDeployPolicy --policy-document file://codedeploy-policy.json
aws iam create-role --role-name CodeDeployRole --assume-role-policy-document file://codedeploy-role-document.json
aws iam attach-role-policy --role-name CodeDeployRole --policy-arn arn:aws:iam::xxxxxxxxxx:policy/CodeDeployPolicy
```