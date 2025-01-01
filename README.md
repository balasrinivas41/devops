i# Create S3 bucket
Full Workflow Example:
Create a bucket in Mumbai (ap-south-1):

# AWS S3 CLI Operations

This document provides instructions for using the AWS CLI to interact with Amazon S3 buckets, including listing files, viewing their contents, and deleting objects.

## Prerequisites

- **AWS CLI** installed and configured with your AWS credentials. If you haven't configured the CLI, run the following command:
  
  ```bash
  aws configure

  ##create s3 bucket
  aws s3api create-bucket --bucket bala --region ap-south-1 --create-bucket-configuration LocationConstraint=ap-south-1

  ##list buckets  
  aws s3api list-buckets --region ap-south-1

  ##create file in bucket
  aws s3 cp bala.js s3://bala/
  
  ## remove files from s3 bucket  
  aws s3 rm s3://bala --recursive
  
  ##delete s3 bucket
  aws s3api delete-bucket --bucket bala --region ap-south-1


