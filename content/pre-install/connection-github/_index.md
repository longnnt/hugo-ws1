+++
title = 'Create connection to github'
date = 2024-09-07T20:59:39+07:00
url = '/pre-install/connect-github'
pre = "<b>1.3. </b>"
+++
#### Create connection to github using console:
1. Go to Codepipeline service from homepage
    ![alt text](image.png)
2. Choose **Connections**
    ![alt text](image-1.png)
3. Choose **Create connections**
  ![alt text](image-2.png)
4. Choose Github in tab select a provider and create connection name (ex: ```github-conn```)
    ![alt text](image-4.png)
5. Choose **Install a new app**
  ![alt text](image-5.png)
6. Navigate to github config
     - Can choose between **All Or Only Select repositories** then press Install & Authorize
     ![alt text](image-6.png)
7. Choose **connect**
  ![alt text](image-7.png)
**Result**
![alt text](image-10.png)

{{% notice note %}}
Arn used to in code pipeline step
{{% /notice %}}