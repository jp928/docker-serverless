Docker AWS Serverless
======================

Docker image containing AWS CLI, NodeJS, and Serverless Framework to ease deployment to AWS.

Usage
------

### Build Locally

If you want to build and use your own local image

```bash
$ make docker-build
$ make docker-shell
```

### Environment Variables

```
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_DEFAULT_REGION=
AWS_ACCOUNT_ID=

# Cloudformation stack name to be created/updated/deleted
STACK_NAME=
# the cloudformation file path
CFN_FILE=
# the cloudformation params file
CFN_PARAMS_FILE=
```

Those environment variables must all be set

- using a file and passing it to `docker run --env-file path/to/file` (see example)
- passing them to `docker run -e NAME1=value1 -e NAME2=value2`
- a mix of both

### Ways of using the image

Here are some ways of using the image

- running one container per command (see example)
- running a container and stay inside it to execute the commands

Docker image
------------

The Docker image has the following:

- Node 4.7 (Alpine)

  > AWS Lambda only supports Node 4.3.2 but there was no official Docker image with this version.

- [aws-cli](https://github.com/aws/aws-cli)
- [aws-shell](https://github.com/awslabs/aws-shell)
- [Serverless Framework v1.4](https://serverless.com)
- envsubst which is quite useful to create file based on a template using env vars

### Scripts

Some scripts has been written to help deploying to AWS (see example)

Name | Description
---|---
cfn-create-or-update.sh | Create or update a cloudformation
cfn-delete.sh | Delete a cloudformation
cfn-validate-template.sh | Validate a cloudformation template