# AWS IAM Least Privilege Lab

## 📌 Overview
This lab demonstrates the principle of **least privilege** using AWS Identity and Access Management (IAM).  
An administrator account is used to create a restricted analyst user who can view EC2 and S3 resources but is **explicitly denied IAM permissions**.

This project showcases:
- Secure IAM user and group management
- Custom IAM policies
- Multi-Factor Authentication (MFA)
- Access denial enforcement

---

## 🛠 Technologies Used
- AWS IAM
- AWS Management Console
- Virtual MFA (Authenticator App)
- Custom IAM Policies (JSON)
- GitHub Documentation

---

## 🧠 Lab Architecture
- **Admin User** (`alice-admin`)
  - Full administrative access
  - MFA enabled
- **Analyst User** (`bob-analyst`)
  - Member of `Analysts` group
  - Read-only access to EC2 and S3
  - No IAM permissions (least privilege enforced)

---

## 🔐 Step-by-Step Implementation

### Step 1: Create Admin User
Created an IAM administrator user with full access.
![Step 1]images/01-root-mfa-enabled.png

---

### Step 2: Attach Admin Group & Permissions
Attached `AdministratorAccess` policy via an admin group.
![Step 2](screenshots/02-admin-group-attached.png)

---

### Step 3: Enable MFA for Admin
Enabled virtual MFA to secure the admin account.
![Step 3](screenshots/03-mfa-enabled-admin.png)

---

### Step 4: Create Analyst User
Created a restricted IAM user named `bob-analyst`.
![Step 4](screenshots/04-analyst-user-created.png)

---

### Step 5: Create Analyst Group
Created an IAM group called `Analysts`.
![Step 5](screenshots/05-analyst-group-created.png)

---

### Step 6: Create Custom IAM Policy
Created a **custom policy** allowing:
- `ec2:Describe*`
- `s3:ListAllMyBuckets`
- `s3:GetObject`

![Step 6](screenshots/06-custom-policy-created.png)

---

### Step 7: Attach Policy to Analyst Group
Attached the custom read-only policy to the `Analysts` group.
![Step 7](screenshots/07-policy-attached-to-group.png)

---

### Step 8: Add Analyst User to Group
Added `bob-analyst` to the `Analysts` group.
![Step 8](screenshots/08-analyst-added-to-group.png)

---

### Step 9: Analyst Login Page
Verified IAM login using the account ID and IAM username.
![Step 9](screenshots/09-analyst-console-login-page.png)

---

### Step 10: Password Reset
Forced password reset on first login for security.
![Step 10](screenshots/10-password-reset-required.png)

---

### Step 11: Successful Analyst Login
Confirmed `bob-analyst` successfully logged in.
![Step 11](screenshots/11-bob-analyst-successful-login.png)

---

### Step 12: Access Denied (Least Privilege Enforced)
Attempted to list IAM users and received an access denied error.
This confirms **least privilege is correctly enforced**.
![Step 12](screenshots/12-access-denied-iam-listusers.png)

---

## ✅ Security Principles Demonstrated
- Least Privilege
- Role-Based Access Control (RBAC)
- MFA Enforcement
- Password Hygiene
- Separation of Duties

---

## 🎯 Why This Matters
This lab reflects real-world IAM practices used in:
- Cloud security engineering
- SOC operations
- Compliance-driven environments (CMMC, NIST, ISO 27001)

---

## 📌 Author
**Deon Ricks**  
Aspiring Cloud & Security Engineer  
