test pipeline policy.

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

Custom Policy: GitHubListBucketAndGetPutObject

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
NOTE: (AccessDenied) when calling the DeleteObject operation: User: arn:aws:iam::***:user/git-web-app-deployer is not authorized to perform: s3:DeleteObject on resource: "arn:aws:s3:::test-react-ecommerce/assets/index-DZzBzpaP.js" because no identity-based policy allows the s3:DeleteObject action
Solution: Add the `"s3:DeleteObject"`action to the IAM user to delete the s3 bucket objects.