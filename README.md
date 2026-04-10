# 🌐 Highly Available Static Website on AWS

## 📌 Project Overview
This project demonstrates how to build a **Highly Available Static Website** using AWS services.  

The website is hosted on an EC2 instance with an attached EBS volume, and backups are maintained using **EBS Snapshots, AMI, and S3**. In case of failure, the application can be restored in another Availability Zone to ensure high availability.

---

## 🎯 Objective
- Deploy static website on EC2
- Attach and configure EBS volume
- Store backups using Snapshot and AMI
- Store additional backup in S3
- Restore website in another Availability Zone

---

## 🛠️ Technologies & Services Used
- AWS EC2 (Elastic Compute Cloud)
- Amazon EBS (Elastic Block Store)
- EBS Snapshot
- Amazon AMI
- Amazon S3 (Private Bucket)
- IAM Role
- Apache Web Server (httpd)
- Linux

---

## 🏗️ Architecture Diagram
EC2 (AZ-1) → EBS → Snapshot + AMI → S3 Backup → EC2 (AZ-2) → Same Website


---

## 🔄 Workflow

1. Launch EC2 instance in Availability Zone 1
2. Configure security groups (HTTP, SSH)
3. Attach EBS volume to EC2
4. Install Apache and host static website
5. Create EBS snapshot (backup)
6. Store backup in S3 (private bucket)
7. Create AMI from EC2 instance
8. Launch new EC2 instance in another AZ using AMI
9. Start web server and verify output

---

## ⚙️ Setup Steps

### 🔹 Step 1: Launch EC2 Instance
- Create EC2 instance in AZ-1
- Configure security group (HTTP & SSH)
- Connect using SSH

---

### 🔹 Step 2: Attach and Configure EBS Volume
bash
lsblk
sudo mkfs -t ext4 /dev/xvdb
sudo mount /dev/xvdb /mnt

🔹 Step 3: Install Apache
sudo yum install httpd -y
sudo systemctl start httpd

🔹 Step 4: Deploy Static Website
cd /mnt
echo "My Static Website" > index.html
sudo cp index.html /var/www/html/

🔹 Step 5: Verify Website
Open browser:
http://<EC2-Public-IP>

🔹 Step 6: Create EBS Snapshot
Go to EC2 → Volumes
Select volume → Create Snapshot

🔹 Step 7: Store Backup in S3
Create private S3 bucket
Upload backup files

🔹 Step 8: Create IAM Role
Create role with S3 access
Attach role to EC2 instance

🔹 Step 9: Create AMI
Select EC2 → Actions → Create Image

🔹 Step 10: Launch EC2 in Another AZ
Use AMI to launch new EC2 instance in AZ-2

🔹 Step 11: Start Web Server
sudo systemctl start httpd

🔹 Step 12: Verify High Availability
Access new EC2 public IP

Confirm same website is displayed
📸 Screenshots

(main page.pdf)

EC2 Instance Setup
EBS Volume Attachment
Apache Installation
Website Output
Snapshot Creation
S3 Backup
AMI Creation
Second EC2 Instance Output
✅ Key Features
High availability across Availability Zones
Backup using Snapshot and AMI
Secure storage in S3
Easy recovery and replication
📈 Benefits
Fault tolerance
Data protection
Business continuity
Scalable architecture
🚀 Future Enhancements
Add Load Balancer (ALB)
Use Auto Scaling Group
Implement CloudFront CDN
Enable HTTPS with SSL


👨‍💻 Author

Harshavardhan
BCA Student | Aspiring Cloud & DevOps Engineer
