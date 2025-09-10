# Static Website Deployment with GitHub Actions (Dev & Prod)

This repository contains a simple static website that is automatically deployed to AWS S3 using GitHub Actions. The workflow supports **separate Development and Production deployments** based on the branch.

---

## Project Files

- `index.html` – Main webpage  
- `style.css` – Styling for the webpage  
- `app.js` (optional) – JavaScript interactivity  

---

## How the Deployment Works

### GitHub Actions Workflow
- **Branch triggers:**
  - `dev` → deploys to **Development S3 bucket**
  - `main` → deploys to **Production S3 bucket**
- **S3 Sync options:**
  - `--delete` → removes files from S3 that are no longer in the repo  
  - `--exact-timestamps` → ensures only changed files are uploaded

### Dev Deployment
- Triggered automatically when pushing to the `dev` branch  
- Deploys to your **Development bucket** for testing

### Prod Deployment
- Triggered automatically when pushing to the `main` branch  
- Deploys to your **Production bucket** for live use

---

## Setup Instructions

1. **Create S3 Buckets**
   - One for Development (`dev-bucket`)  
   - One for Production (`prod-bucket`)  
   - Enable **Static Website Hosting**  
   - Add **public read permissions** if needed (or manage via workflow secrets)

2. **Add Repository Secrets**
   - `AWS_ACCESS_KEY_ID`  
   - `AWS_SECRET_ACCESS_KEY`  
   - `S3_BUCKET_DEV`  
   - `S3_BUCKET_PROD`  
   - `S3_BUCKET_REGION`

3. **Push Code**
   - Push changes to `dev` for testing  
   - Merge to `main` for production deployment  

---

## Notes

- The workflow **ensures dev code never goes directly to production**.  
- All deployments are **branch-based** and fully automated.  

---

## Author

Kartik Bhandari  
