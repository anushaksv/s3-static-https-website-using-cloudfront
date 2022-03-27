# s3-static-https-website-using-cloudfront

## Description:-

Here we host a static website with S3 & CloudFront and set-up an SSL certificate from ACM.


## Architecture:-

![cloud-s3-block](https://user-images.githubusercontent.com/97517424/160056933-a4c25204-4f04-4681-8ef3-aa73fc9f8486.png)


## Setup:-

* Create an S3 bucket and set it up for static website hosting 

* Set up a CloudFront distribution and link it with a custom domain  

* Secure the connection via SSL and AWS Certificate Manager 

* Create a record in Route 53 as alias to CloudFront distribution.


### S3 Bucket

1. Create an s3 bucket by blocking all public access to it.
2. Upload website contents

![s3-1](https://user-images.githubusercontent.com/97517424/160268798-3cd44d7a-5720-458d-8660-165a3b4edb77.png)

3. Click Properties, and enable Static website hosting.

![s3-2](https://user-images.githubusercontent.com/97517424/160268800-7d33a494-b964-4558-a4f5-a005cf6ceaf5.png)


### CloudFront Distribution

Here we create a distribution for the website and point it at the S3 bucket, so that it gets the same contents as the S3 bucket.

1. Origin domain

   The Origin Domain Name should be the endpoint of the S3 bucket as shown below.

2. S3 bucket access 

   - Select "Yes use OAI (bucket can restrict access to only CloudFront)".

   - Create a new OAI and select "Yes, update the bucket policy" in bucket policy. This will automatically update bucket policy.

![cf-2](https://user-images.githubusercontent.com/97517424/160269057-3370cb09-2ca6-4bd5-9dc5-8b0fa044dd3c.png)

3. Viewer Protocol Policy

   Choose Redirect HTTP to HTTPS

![cf-3](https://user-images.githubusercontent.com/97517424/160269062-9371cee7-4415-48c3-bb50-34a822716615.png)

4. Alternate domain name (CNAME)

Put the domain of your website into the CNAMEs field.

5. SSL Certificate

Under settings, You can add a custom SSL certificate. Here I have added a ACM certificate.

![acm](https://user-images.githubusercontent.com/97517424/160270410-497b17ce-17df-453f-bf15-70509110ad6f.png)

6. Default root object

   Here I have added "index.html"

###### *This is the created distribution*

![cf-1](https://user-images.githubusercontent.com/97517424/160270536-d5611098-67ba-48a7-a3a4-7a7104fe0edc.png)


### Route 53

1. Select your domain and then add an A record
2. Choose Simple routing
3. Click the dropdown menu at Value/Route traffic to and choose Alias to CloudFront distribution.

![route-1](https://user-images.githubusercontent.com/97517424/160270622-26eb456e-3bfc-4e60-9d7d-0aba92ff0f97.png)


## Conclusion:-

When someone load the website for the firt time , the Cloudfront will cache the website in its edge locations so that the next time the site will load faster.

![site](https://user-images.githubusercontent.com/97517424/160270862-09542044-8b57-4165-9b3e-16235de80a02.png)
