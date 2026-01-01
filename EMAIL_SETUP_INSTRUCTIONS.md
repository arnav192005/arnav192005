# Email Notification Setup Guide

Your login page is now configured to send you email notifications when users log in! Follow these steps to complete the setup:

## Step 1: Create EmailJS Account

1. Go to [https://www.emailjs.com/](https://www.emailjs.com/)
2. Click "Sign Up" and create a free account
3. Verify your email address

## Step 2: Set Up Email Service

1. After logging in, go to **Email Services**
2. Click **Add New Service**
3. Choose your email provider (Gmail recommended)
4. Follow the instructions to connect your email
5. Copy the **Service ID** (you'll need this later)

## Step 3: Create Email Template

1. Go to **Email Templates**
2. Click **Create New Template**
3. **IMPORTANT:** Set the "To Email" field to: **arnavpanwala@gmail.com**
4. Use this template content:

**Template Name:** Login Notification

**To Email:** arnavpanwala@gmail.com

**Subject:** New Login Alert - CODEX

**Content:**
```
Hello Arnav,

A new user has logged into CODEX:

User Email: {{user_email}}
Login Type: {{login_type}}
Login Time: {{login_time}}
Browser Info: {{user_ip}}

---
CODEX - College Study Material Hub
```

5. Save the template and copy the **Template ID**

## Step 4: Get Your Public Key

1. Go to **Account** → **General**
2. Find your **Public Key**
3. Copy it

## Step 5: Update login.html

Open `login.html` and replace these placeholders:

**Line ~393:** Replace `YOUR_PUBLIC_KEY` with your actual public key:
```javascript
emailjs.init('YOUR_ACTUAL_PUBLIC_KEY_HERE');
```

**Line ~536:** Replace `YOUR_SERVICE_ID` and `YOUR_TEMPLATE_ID`:
```javascript
emailjs.send('YOUR_SERVICE_ID', 'YOUR_TEMPLATE_ID', templateParams)
```

## Example Configuration

```javascript
// Replace this:
emailjs.init('YOUR_PUBLIC_KEY');

// With something like:
emailjs.init('abcd1234XYZ5678');

// And replace this:
emailjs.send('YOUR_SERVICE_ID', 'YOUR_TEMPLATE_ID', templateParams)

// With something like:
emailjs.send('service_abc123', 'template_xyz789', templateParams)
```

## Step 6: Test It!

1. Open your login page
2. Enter any email and password
3. Click "Sign In"
4. Check your email inbox - you should receive a notification!

## What Gets Sent

When a user logs in, you'll receive an email with:
- ✉️ User's email address
- 🔐 Login type (Email Login, Google Login, or Guest Login)
- 🕐 Login timestamp
- 💻 Browser information

## Troubleshooting

**Not receiving emails?**
- Check your spam folder
- Verify all IDs are correct in login.html
- Check browser console for errors (F12 → Console tab)
- Make sure you verified your EmailJS email

**EmailJS Free Tier Limits:**
- 200 emails per month
- Upgrade for more if needed

## Security Note

The current setup is for demonstration. For production:
- Move email logic to a backend server
- Never expose API keys in client-side code
- Implement proper authentication
- Add rate limiting to prevent spam

---

Need help? Check [EmailJS Documentation](https://www.emailjs.com/docs/)
