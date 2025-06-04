# Static Website Deployment with AWS S3 & CloudFront

This repository hosts the source files for a static website and includes automation for deploying to Amazon S3 and distributing via CloudFront using GitHub Actions.

## 🧾 Project Overview

This project helps you:
- Host a static website (HTML, CSS, JS) on **Amazon S3**
- Serve it globally with low latency using **CloudFront**
- Automate deployments using **GitHub Actions CI/CD**

## 📁 Repository Structure
Static_hosting/
├── index.html
├── style.css
├── script.js
├── Assets/
│ └── images, fonts, etc.
└── .github/workflows/
└── deploy.yml

## 🛠 Prerequisites

Before you begin, ensure you have:

1. An **AWS Account**
2. An **S3 Bucket** configured for static website hosting (`apple-website-976`)
3. A **CloudFront Distribution** pointing to your S3 bucket
4. Your website files in this repo (HTML, CSS, JS, assets)

## 🔐 Configure GitHub Secrets

To enable automated deployment, you need to store your AWS credentials securely in GitHub:

Go to:  
**Settings > Secrets and variables > Actions** in your GitHub repo, and add:

| Secret Name | Description |
|-------------|-------------|
| `AWS_ACCESS_KEY_ID` | Your AWS access key ID |
| `AWS_SECRET_ACCESS_KEY` | Your AWS secret access key |
| `CLOUDFRONT_DISTRIBUTION_ID` | The ID of your CloudFront distribution (e.g., `E2XXXXXXXXXXXX`) |

## 🚀 Deploy Automatically

The site is automatically deployed when you push changes to the `main` branch.

The [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml) workflow does the following:

- Syncs local files with your S3 bucket
- Makes uploaded files publicly readable
- Invalidates CloudFront cache to reflect updates instantly

## 📦 Manual Upload (Optional)

If you prefer manual upload:

```bash
aws s3 sync . s3://apple-website-976 --acl public-read
🌐 Access Your Site
Once deployed, visit your hosted static website , which looks like:
https://apple-website-976.s3.us-east-1.amazonaws.com/index.html
