# Amazon Web Services

[Amazon Web Services](https://aws.amazon.com/) is the preferred Public Cloud platform for The National Archives and SHOULD be used. Providers such as Azure and Google GCP SHOULD NOT be used.

In line with the [Government Cloud First policy](https://www.gov.uk/guidance/government-cloud-first-policy), serverless and/or managed service solutions are preferred and SHOULD be used. Server based services MAY be used but are NOT RECOMMENDED. Examples of serverless/managed services are API Gateway, DynamoDB, Lambda, S3, SNS, SQS, RDS, etc.

Infrastructure within AWS MUST be managed via an IaC solution; [Terraform](terraform.md) is preferred. Where possible, modules SHOULD be shared and reused. Examples of existing Terraform module repositories include:

- [da-terraform-modules](https://github.com/nationalarchives/da-terraform-modules)

When developing services in the Public Cloud, best practices from the supplier MUST be followed.

## Logging in to AWS

Access to AWS SHOULD be via [IAM Identity Center](https://nationalarchivesuk.awsapps.com/start#/) for all staff members. To manage who can access accounts through IAM Identity Center, see [these guides](https://national-archives.atlassian.net/l/cp/1cCe2cVy) on Confluence.

IAM Users SHOULD NOT be used to access the AWS Console or AWS API/SDK.
