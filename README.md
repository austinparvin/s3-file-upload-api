# s3-file-upload-api

## AWS and Github Setup

In AWS create a new user with Programmatic access and the following policies:

1. IAMFullAccess
2. AmazonS3FullAccess
3. AmazonAPIGatewayAdministrator
4. AmazonAPIGatewayPushToCloudWatchLogs
5. AWSCloudFormationFullAccess
6. AWSLambda_FullAccess

Next grab the Access Key ID and Secret Access Key from AWS for the created user.

In you github repository, go to Settings > Secrets > New Repository Secret

```text
Name: AWS_ACCESS_KEY_ID
Value: copied_value_from_AWS
```

```text
Name: AWS_SECRET_ACCESS_KEY
Value: copied_value_from_AWS
```

## Github Actions Setup

In the root dir, create .github/workflows/main.yml |
*check file for format*

### Serverless Setup

In the root dir, create serverless.yml |
*check file for format*

## Troubleshooting

My stack would repeatedly fail because

```text
Error: s3-file-uploader-bucket-dev already exists
```

I fixed this by changing the custom bucket name by adding "test" into it

It seems that serverless creates a default bucket to store past stack data that ended up being essentially the same name.  I believe there is a way to configure this to not happen as my previous lambda/aws/serverless experience did not have this issue.

[More on the issue](https://stackoverflow.com/questions/70994280/two-s3-buckets-are-creating-when-deploying-using-serverless-framework)
