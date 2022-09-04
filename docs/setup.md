# Setup

### **Create AWS RDS database**

- Create a New database ( Postgres ) using the AWS console
- Allow connections to your database
- Check database connectivity using software like ( Postbird )

---

### **ElasticBeanstalk Cli**

- Install the EB using the following [Link](https://github.com/aws/aws-elastic-beanstalk-cli-setup)
- Start initializing the EB application using

```sh
    cd udagram-api
```

```sh
    eb init <APP_NAME> --platform Node.js --region <REGOIN>
```

- A directory called _.elasticbeanstalk_ will be created inside the udagram-api
- You need to create the Elastic environment using the following command

```sh
    eb create --sample <ENVIRONMENT_NAME>
```

- Check the EB using the command `eb open`, After creation process finish
- Add environments variables to the EB using
  AWS CONSOLE -> Elastic Beanstalk -> APP_NAME -> Configuration -> Software -> Add Environtment variables

| Environment Variable | Usage               |
| :------------------: | ------------------- |
|         PORT         | <server_port>       |
|    POSTGRES_HOST     | <database_host>     |
|     POSTGRES_DB      | <database_name>     |
|  POSTGRES_USERNAME   | <database_username> |
|  POSTGRES_PASSWORD   | <database_password> |
|    POSTGRES_PORT     | <database_port>     |
|      JWT_SECRET      | <jwt_secret>        |
|      AWS_BUCKET      | <s3_bucket_ARN>     |
|      AWS_REGION      | <s3_region>         |
|     AWS_PROFILE      | <s3_profile>        |
|         URL          | <APP_URL>           |

- Build API using the following command inside the udagram-api directory

```sh
  npm run build
```

- Deploy your API to the EB by using the following commands

```sh
  eb use ENVIRONMENT_NAME
  eb deploy ENVIRONMENT_NAME
```

- Now you are able to access the AWS S3 and it's Connected to the AWS EB api.

---

### **AWS Cli**

- Setup the AWS CLI from [Here](https://awscli.amazonaws.com/AWSCLIV2.msi)
- start the AWS configuration by running this command:

```sh
    aws configure
```

|       Requirements        | Defination                                   |
| :-----------------------: | :------------------------------------------- |
|  **AWS_DEFAULT_REGION**   | Region to use with AWS services              |
|   **AWS_ACCESS_KEY_ID**   | The AWS Access key id                        |
| **AWS_SECRET_ACCESS_KEY** | The AWS Secret key for the used AWS id       |
|        **Output**         | The data output type preferred to use _json_ |

- Create your S3 Bucket

```sh
    aws s3api create-bucket --bucket <YOUR-BUCKET-NAME> --region <CHOOSE-REGION>
```

- Enable AWS S3 Bucket **Static Website**

```sh
    aws s3 website s3://<BUCKET_NAME>/ --index-document index.html
```

- Check AWS website is running using AWS s3 Link

  **http://`BUCKET_NAME`.s3-website-`REGION`.amazonaws.com**

- Modify the link to your API in `udagram-frontend/src/environments/` in both files to

```js
apiHost: "Http://<YOUR_EB_DIRECT_LINK>/api/v0";
```

- Build frontend and upload the files to the **AWS S3 Bucket**

```sh
    cd udagram-frontend
    npm run build
    aws s3 cp --recursive ./www s3://<BUCKET-NAME> --acl public-read
```

---
