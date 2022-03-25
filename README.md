# s3-static-https-website-using-cloudfront

## Description:-

Here we host a static website with S3 & CloudFront and set-up an SSL certificate from ACM.


## Architecture

![cloud-s3-block](https://user-images.githubusercontent.com/97517424/160056933-a4c25204-4f04-4681-8ef3-aa73fc9f8486.png)


## Setup:-

1. Create an S3 bucket and set it up for static website hosting 

2. Set up a CloudFront distribution and link it with a custom domain  

3. Secure the connection via SSL and AWS Certificate Manager 

4. Create a record in Route 53 as alias to CloudFront distribution.


### S3 Bucket


