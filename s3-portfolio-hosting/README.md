# Hosting a portfolio website on AWS S3

## 📌 Project Objective
Host a personal portfolio website using **AWS S3 Static Website Hosting** with public access, following best practices.

---

## 🛠️ AWS Services Used
- **Amazon S3**: For static website hosting (HTML/CSS files).
- **IAM**: Used for bucket policy to ensure secure public access.

---

## 🚀 Implementation Steps

### Step 1: Prepare Website Files

Create the following files for your portfolio:

- `index.html`: The main webpage.
- `style.css`: The stylesheet for the webpage.

### Step 2: Create an S3 Bucket

1. Go to the **AWS Management Console** → **S3**.
2. **Create a new bucket** with a unique name.
3. Select the **Region** closest to your audience.
4. **Disable ACLs** (use default settings).
5. **Uncheck** "Block all public access" (acknowledge warning).

### Step 3: Enable Static Website Hosting

1. Inside your S3 bucket, go to **Properties** → **Static Website Hosting**.
2. Enable static website hosting and set the **Index document** as `index.html`.
3. (Optional) Set an **Error document** (can use `index.html` or create a custom `error.html`).

### Step 4: Upload Files

1. Go to the **Objects** tab inside your S3 bucket.
2. **Upload the `index.html`** and **`style.css`** files.
3. Verify the correct content type is detected (HTML, CSS).

### Step 5: Set Bucket Policy

1. Go to **Permissions** → **Bucket Policy**.
2. Add the following policy to allow public read access to the files:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::YOUR_BUCKET_NAME/*"
    }
  ]
}```

---

🔒 Best Practices Followed
- Clean bucket setup
- Minimum permissions (only GetObject)
- Versioning enabled
- No unnecessary files
- Clean and responsive portfolio site

📄 License
This project is for educational and professional portfolio use.
