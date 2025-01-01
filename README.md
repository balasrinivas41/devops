# Create S3 bucket
Full Workflow Example:
Create a bucket in Mumbai (ap-south-1):

bash
Copy code
aws s3api create-bucket --bucket my-unique-bucket-name --region ap-south-1 \
  --create-bucket-configuration LocationConstraint=ap-south-1
Verify the bucket:

bash
Copy code
aws s3api list-buckets
Upload a file to the bucket:

bash
Copy code
aws s3 cp myfile.txt s3://my-unique-bucket-name/
