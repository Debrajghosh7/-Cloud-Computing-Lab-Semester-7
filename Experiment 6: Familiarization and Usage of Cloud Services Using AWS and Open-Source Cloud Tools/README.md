# Experiment 6: Familiarization and Usage of Cloud Services Using AWS and Open-Source Cloud Tools

## 📌 Aim
To become familiar with different cloud services and perform basic cloud operations using **Amazon Web Services (AWS), Ubuntu Linux, Oracle VirtualBox, and AWS Command Line Interface (CLI).**

## 🛠️ Technologies and Tools Used

- **Amazon Web Services (AWS):** Cloud computing platform.
- **Amazon S3:** Cloud object storage service.
- **AWS IAM:** Identity and Access Management.
- **Amazon EC2:** Cloud-based virtual machine service.
- **Amazon VPC:** Virtual Private Cloud for networking.
- **Amazon CloudWatch:** Cloud resource monitoring service.
- **AWS CLI:** Command-line tool for interacting with AWS services.
- **Ubuntu Linux:** Open-source operating system.
- **Oracle VirtualBox:** Virtualization software.

## 📚 Experiment Overview

This experiment is divided into four major practical tasks.

### Task 1: Virtual Machine Setup Using VirtualBox

**Objective:** Install Ubuntu Linux in Oracle VirtualBox and execute basic Linux commands.

**Steps Performed:**
1. Created a virtual machine using Oracle VirtualBox.
2. Installed Ubuntu Linux.
3. Updated the Ubuntu package repository.
4. Upgraded installed packages.
5. Installed basic Linux utilities.
6. Executed basic Linux terminal commands.

**Commands:**
```bash
sudo apt update
sudo apt upgrade -y
```

### Task 2: Cloud Storage Using Amazon S3

**Objective:** Create an Amazon S3 bucket and perform basic file operations.

**Steps Performed:**
1. Accessed the AWS Management Console.
2. Created an Amazon S3 bucket.
3. Kept Block Public Access enabled.
4. Enabled default encryption.
5. Created a sample text file in Ubuntu.
6. Uploaded the file to the S3 bucket.
7. Downloaded the uploaded file.
8. Verified the downloaded file.
9. Deleted the test object and bucket.

**Linux Commands:**
```bash
mkdir cloud-lab6
cd cloud-lab6

echo "Cloud Computing Lab Experiment 6" > lab-note.txt

cat lab-note.txt
```

### Task 3: Exploration of AWS Cloud Services

#### A. AWS Identity and Access Management (IAM)

**Objective:** Understand how AWS manages users, groups, roles, and permissions.

Topics explored:
- IAM Users
- IAM Groups
- IAM Roles
- IAM Policies
- Principle of Least Privilege

An example IAM policy was studied to understand how permissions are granted to AWS resources.

#### B. Amazon Elastic Compute Cloud (EC2)

**Objective:** Understand cloud-based virtual machine provisioning.

Topics explored:
- Amazon Machine Images (AMI)
- EC2 Instance Types
- Key Pair Configuration
- Network and Security Groups
- Storage Configuration
- Instance Launch and Termination Process

#### C. Amazon Virtual Private Cloud (VPC)

**Objective:** Understand virtual networking in AWS.

Components explored:
- Virtual Private Cloud (VPC)
- Public and Private Subnets
- Route Tables
- Internet Gateways
- Security Groups

### Task 4: Cloud Monitoring and AWS CLI

#### A. Monitoring Using Amazon CloudWatch

**Objective:** Explore AWS resource monitoring and performance metrics.

Topics explored:
- CloudWatch Dashboard
- CloudWatch Metrics
- EC2 CPU Utilization
- Metric Dimensions
- CloudWatch Alarms
- Performance Monitoring

#### B. Basic AWS Operations Using AWS CLI

**Objective:** Perform basic AWS operations through command-line instructions.

**Commands Executed:**

Check AWS CLI version:
```bash
aws --version
```

Verify AWS account identity:
```bash
aws sts get-caller-identity
```

List available S3 buckets:
```bash
aws s3 ls
```

Create a sample file:
```bash
mkdir cloud-lab6-cli
cd cloud-lab6-cli

echo "AWS CLI Cloud Storage Test" > sample.txt
```

Upload a file to S3:
```bash
aws s3 cp sample.txt s3://YOUR-BUCKET-NAME/sample.txt
```

List objects inside the bucket:
```bash
aws s3 ls s3://YOUR-BUCKET-NAME/
```

Download the file:
```bash
aws s3 cp s3://YOUR-BUCKET-NAME/sample.txt downloaded.txt
```

Verify downloaded content:
```bash
cat downloaded.txt
```

Delete the test object:
```bash
aws s3 rm s3://YOUR-BUCKET-NAME/sample.txt
```

**Note:** Replace `YOUR-BUCKET-NAME` with your actual S3 bucket name.

## 📸 Screenshots and Practical Demonstration

The following screenshots can be added to demonstrate the successful completion of the experiment:

1. Ubuntu Virtual Machine running in VirtualBox.
2. Ubuntu terminal showing update and Linux commands.
3. AWS Management Console home page.
4. Amazon S3 bucket creation.
5. Successful file upload to S3.
6. Successful file download and content verification.
7. AWS IAM dashboard and policy overview.
8. Amazon EC2 dashboard and instance configuration.
9. Amazon VPC dashboard and networking components.
10. CloudWatch metrics and monitoring dashboard.
11. AWS CLI version and identity verification.
12. Successful S3 upload and download using AWS CLI.

## 🎯 Learning Outcomes

After completing this experiment, the following concepts were understood:

- Basic virtualization using Oracle VirtualBox.
- Ubuntu Linux installation and command-line operations.
- Cloud object storage using Amazon S3.
- AWS identity and access management using IAM.
- Cloud virtual machine provisioning using EC2.
- Virtual networking using Amazon VPC.
- Cloud resource monitoring using Amazon CloudWatch.
- Basic cloud service operations using AWS CLI.
- Secure management of cloud resources and permissions.
- AWS resource cleanup and cost management.

## ⚠️ Precautions

1. Use only an authorized AWS account.
2. Never share AWS passwords or access keys.
3. Keep S3 buckets private.
4. Follow the principle of least privilege.
5. Check AWS pricing and account eligibility before launching resources.
6. Terminate unused EC2 instances.
7. Delete unnecessary test resources after completing the experiment.
8. Monitor AWS billing to avoid unexpected charges.

## 🏁 Conclusion

Successfully explored the fundamentals of cloud computing using AWS and open-source cloud tools. Practiced Ubuntu virtualization using VirtualBox, cloud storage operations using Amazon S3, and explored AWS IAM, EC2, VPC, and CloudWatch services. Also learned to interact with AWS resources using AWS CLI.

This experiment provided practical knowledge of cloud infrastructure, virtualization, storage, networking, security, and cloud monitoring.

---

**Course:** Cloud Computing Lab  
**Experiment:** 06  
**Tools:** AWS | Ubuntu Linux | Oracle VirtualBox | AWS CLI
