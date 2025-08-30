# AWS S3 Static Website Deployment with Terraform and GitHub Actions

This project demonstrates how to deploy a **static website** to **AWS S3** using **Terraform** for infrastructure provisioning and **GitHub Actions** for CI/CD automation.

---

## Features

- **Infrastructure as Code:** Provision an S3 bucket, bucket policy, and enable static website hosting using Terraform.
- **CI/CD Pipeline:** Automatically deploy website updates from GitHub to S3 using GitHub Actions.
- **Automatic Updates:** Any push to the `main` branch triggers the workflow to sync the latest website files to the S3 bucket.
- **Public Access:** Bucket policy allows public read access to the static website.

---

## Tech Stack

- **AWS S3** – Hosting static content  
- **Terraform** – Infrastructure provisioning  
- **GitHub Actions** – Continuous Deployment  
- **Git** – Version control  
- **HTML** – Website content  

## How It Works

1. Terraform creates the S3 bucket, bucket policy, and uploads initial website files.  
2. Any changes to the `website/` folder trigger GitHub Actions, syncing files to the bucket.  
3. The website is automatically updated and accessible at:  
http://<bucket-name>.s3-website-<region>.amazonaws.com


---

## Quick Start

1. Clone the repo:  
```bash
git clone https://github.com/orimoladeben/aws-s3-static-website.git
cd s3-website
```
2. Configure AWS credentials (You can store them GitHub Secrets for CI/CD as shown below):
```
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
AWS_REGION
S3_BUCKET (bucket name for deployment)
```

3. Deploy with Terraform:
```
terraform init
terraform apply -auto-approve
```
4. Update the website
```
git add website/
git commit -m "Update website"
git push origin main
```
GitHub Actions will automatically deploy the changes

5. Access the static website URL:
```
http://<your-bucket-name>.s3-website-<region>.amazonaws.com
```

6. Clean up resources
```
terraform destroy -auto-approve
```

Notes

Ensure force_destroy = true is set in the Terraform S3 bucket resource to allow deletion of non-empty buckets (If not, you will have to delete the S3 bucket first using AWS CLI).

Make sure your GitHub Secrets are correctly set for the workflow to deploy successfully.

Author

Ben Orimolade 
GitHub: @orimoladeben

