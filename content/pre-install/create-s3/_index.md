+++
title = 'Create S3 bucket'
date = 2024-09-07T19:02:03+07:00
weight = 2
url = '/pre-install/create-s3'

+++

#### Create s3 bucket using cli:

```bash
aws s3api create-bucket --bucket codepipeline-ap-southeast-1-nntl-example --create-bucket-configuration LocationConstraint=ap-southeast-1
```

Specifying:

-   --bucket: Name of bucket (ex: ```codepipeline-ap-southeast-1-nntl-example```)
-   --create-bucket-configuration: Location-create-bucket

**Result**
![alt text](image-14.png)

Check bucket exist using `aws s3api list-buckets`
![alt text](image-15.png)