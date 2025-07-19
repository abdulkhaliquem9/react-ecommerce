## Setup - React + Git Actions + AWS S3 Bucket

### Create S3 bucket and assign the below policy under Bucket policy

```
s3-bucket-policy
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicRead",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject",
                "s3:GetObjectVersion"
            ],
            "Resource": "arn:aws:s3:::test-react-ecommerce/*"
        }
    ]
}
```
### Create an IAM user, and add the below custom policy to the user. generate AWS_ACCESS_KEY_ID & AWS_SECRET_ACCESS_KEY
### and use it in main.yml. store these keys in project environment

#### Custom Policy: GitHubListBucketAndGetPutObject
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "s3:PutObject",
                "s3:GetObject",
                "s3:ListBucket",
                "s3:ListAllMyBuckets",
                "s3:DeleteObject"
            ],
            "Resource": [
                "arn:aws:s3:::test-react-ecommerce",
                "arn:aws:s3:::test-react-ecommerce/*"
            ]
        }
    ]
}
```
Issues: 
1. (AccessDenied) when calling the DeleteObject operation: User: arn:aws:iam::***:user/git-web-app-deployer is not authorized to perform: s3:DeleteObject on resource: "arn:aws:s3:::test-react-ecommerce/assets/index-DZzBzpaP.js" because no identity-based policy allows the s3:DeleteObject action
Solution: Add the `"s3:DeleteObject"`action to the IAM user to delete the s3 bucket objects.

2. An error occurred (AccessDenied) when calling the ListBuckets operation: Access Denied.
This issue will be solved by adding `"s3:ListAllMyBuckets"` Action.