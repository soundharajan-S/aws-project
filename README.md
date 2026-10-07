@"
# AWS Project - awsproject.in

🌐 Live: https://awsproject.in
🔒 HTTPS Enabled with Let's Encrypt

## Services Used (No DevOps Tools)
- **EC2** - Hosting (Amazon Linux + Apache)
- **IAM Role** - EC2 to S3 access (Secure, no keys)
- **S3** - Storage for backups/assets
- **RDS** - Database (MySQL)
- **ACM / Certbot** - SSL Certificate for HTTPS
- **Route53 / GoDaddy** - Domain

## Architecture
User -> Domain (awsproject.in) -> EC2 -> S3 + RDS
EC2 has IAM Role to access S3
Certbot gives HTTPS

## How I Deployed
1. Launched EC2
2. Created IAM Role for S3 access and attached to EC2
3. Created S3 bucket
4. Created RDS MySQL
5. Hosted website on EC2 Apache
6. Configured domain awsproject.in to EC2 IP
7. Installed Certbot and enabled HTTPS

```bash
sudo yum install httpd -y
sudo systemctl start httpd
sudo yum install certbot python3-certbot-apache -y
sudo certbot --apache -d awsproject.in
