# AWS S3 and CloudFront Static Website Hosting

## Overview
This project demonstrates how to host a static website using AWS S3 and distribute it globally using CloudFront.

### AWS Services Used:
- **S3**: Stores static website files (HTML, CSS, JS).
- **CloudFront**: CDN to deliver content globally with low latency.

### Steps:
1. **Create an S3 bucket** to store the static website files.
2. **Upload HTML, CSS, and JS files** to the S3 bucket.
3. **Configure S3 for static website hosting**.
4. **Set up CloudFront** to distribute the content globally.
5. (Optional) **Configure a custom domain** with Route 53 and **SSL certificates** from ACM.

### To Deploy:
1. Log into AWS Console.
2. Create an S3 bucket and configure it for static website hosting.
3. Upload your static files (HTML, CSS, JS) to the S3 bucket.
4. Set up a CloudFront distribution pointing to your S3 bucket.

### Challenges:
- Managing DNS with Route 53 for custom domains.
- Using CloudFront to serve content globally.

### Code (Terraform Example):
```terraform
resource "aws_s3_bucket" "static_website" {
  bucket = "my-website-bucket-<your-name>"
  website {
    index_document = "index.html"
    error_document = "error.html"
  }
}
