Static Web App with AWS CloudFront and Custom Domain

Description
This project demonstrates how to deploy a static web application using AWS S3 and CloudFront. The static content (HTML, CSS, JavaScript) is hosted on an S3 bucket, and AWS CloudFront is used for content delivery. Additionally, a custom domain (`www.deekshitha.live`) is configured to point to the CloudFront distribution using Route 53.

## Table of Contents
1. [Installation](#installation)
2. [Setup Instructions](#setup-instructions)
   - [Creating the S3 Bucket](#creating-the-s3-bucket)
   - [Setting Up CloudFront Distribution](#setting-up-cloudfront-distribution)
   - [Configuring DNS](#configuring-dns)
3. [Usage](#usage)
4. [Screenshots](#screenshots)
5. [License](#license)

## Installation
Before you begin, ensure you have:
- An AWS account
- A custom domain registered
- Access to the AWS Management Console
- Static web app files (HTML, CSS, JavaScript) ready to be uploaded to the S3 bucket

## Setup Instructions

### Creating the S3 Bucket
1. **Create an S3 Bucket**:
   - Go to the **S3** service in the AWS Management Console.
   - Create a new bucket, naming it (e.g., `deekshitha-live-web`).
   - Upload your static web files (HTML, CSS, JS) to the bucket.
   
2. **Make the Bucket Public**:
   - Set the S3 bucket's permissions to allow public access to the files.
   - Configure the **Bucket Policy** to allow CloudFront to fetch content from the S3 bucket.

### Setting Up CloudFront Distribution
1. **Create a CloudFront Distribution**:
   - Go to **CloudFront** in the AWS Console and click on "Create Distribution."
   - Choose **Web** as the delivery method.
   - Select your S3 bucket as the origin.
   - Configure any additional settings like caching, HTTPS, and SSL as required.
   - Once the distribution is created, CloudFront will provide a domain name (e.g., `d1234567890abc.cloudfront.net`).

2. **Configure Cache Behavior** (Optional):
   - Set up cache behaviors to determine how CloudFront handles requests for different file types, like images or HTML.

### Configuring DNS
1. **Create a Hosted Zone in Route 53**:
   - Go to **Route 53** and create a public hosted zone with your domain name (`deekshitha.live`).
   
2. **Update DNS Records**:
   - Copy the CloudFront domain name (e.g., `d1234567890abc.cloudfront.net`).
   - Create a **CNAME** record in Route 53:
     - **Name**: `www` (for `www.deekshitha.live`)
     - **Value**: The CloudFront domain name.
   - If you're pointing the root domain (`deekshitha.live`), create an **A record** with an alias pointing to CloudFront.

3. **Update Domain Registrar**:
   - At your domain registrar (where you bought your domain), update the **name servers** with the values provided by Route 53.
   
4. **Wait for DNS Propagation**:
   - DNS changes might take up to 2 hours to propagate. After that, you can access your web app via the custom domain.

## Usage
Once the DNS changes have propagated, you can access your static web app via:
- `www.deekshitha.live`
- The CloudFront distribution URL (e.g., `d1234567890abc.cloudfront.net`)

## Screenshots
Here’s an example of the CloudFront distribution serving the static web app:

![Screenshot (167)](https://github.com/user-attachments/assets/72c684bb-a716-41f2-99aa-1f9263e6fa7c)
![Screenshot (168)](https://github.com/user-attachments/assets/376ea88f-5789-4116-aac8-49d95ea6c5b9)
![Screenshot (169)](https://github.com/user-attachments/assets/4defdb4b-97e2-4e6c-a118-6ba655b8cdcc)
![Screenshot (170)](https://github.com/user-attachments/assets/3bdb7d3a-1bec-47dd-963c-ba9797c015c1)
![Screenshot (171)](https://github.com/user-attachments/assets/4bf198c2-23b1-4a9e-874a-bdeb2184d3e5)



## License
This project is licensed under the MIT License. See the LICENSE file for more details.
