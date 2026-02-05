# ☁️ AWS Certified Cloud Practitioner (CLF-C02) Study Notes

This repository contains my personal study notes, cheatsheets, and resources for the AWS Cloud Practitioner exam.

## 📌 Progress Tracker
- [x] Domain 1: Cloud concepts (24% of the scored content)
- [ ] Domain 2: Security and compliance (30% of the scored content)
- [ ] Domain 3: Cloud technology and services (34% of the scored content)
- [ ] Domain 4: Billing, pricing, and support (12% of the scored content)

---

## 📖 Exam Domains

### 1. Cloud Concepts
The Shared Responsibility Model is key here.
> **Tip:** Remember that AWS is responsible for security **OF** the cloud, and the customer is responsible for security **IN** the cloud.

### 2. Security and Compliance
| Service | Purpose | Use Case |
| :--- | :--- | :--- |
| **AWS IAM** | Identity Management | Managing users and permissions. |
| **AWS Shield** | DDoS Protection | Protecting applications from attacks. |
| **AWS WAF** | Web Firewall | Filtering malicious web traffic. |
| **AWS Secrets Manager** | Secret Rotation | Managing RDS passwords securely. |

---

## 🛠️ Hands-on: Terraform Examples
Since I am presenting at **HashiTalks 2026**, I am documenting how to deploy these services securely.

### Secure S3 Bucket
```hcl
resource "aws_s3_bucket" "secure_bucket" {
  bucket = "my-secure-data-2026"
}

resource "aws_s3_bucket_public_access_block" "block_public" {
  bucket = aws_s3_bucket.secure_bucket.id

  block_public_acls       = true
  block_public_policy     = true
  ignore_public_acls      = true
  restrict_public_buckets = true
}