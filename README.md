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
                "s3:ListAllMyBuckets"
            ],
            "Resource": [
                "arn:aws:s3:::test-react-ecommerce",
                "arn:aws:s3:::test-react-ecommerce/*"
            ]
        }
    ]
}