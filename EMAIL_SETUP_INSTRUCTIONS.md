# Email Setup Instructions for Portfolio Contact Form

Your contact form is now ready to send emails directly to your email address (pateldivy9808@gmail.com) using EmailJS. Follow these steps to complete the setup:

## Step 1: Create EmailJS Account
1. Go to [https://www.emailjs.com/](https://www.emailjs.com/)
2. Click "Sign Up" and create a free account
3. Verify your email address

## Step 2: Add Email Service
1. In your EmailJS dashboard, go to "Email Services"
2. Click "Add New Service"
3. Choose your email provider (Gmail, Outlook, etc.)
4. For Gmail:
   - Enter your Gmail address: `pateldivy9808@gmail.com`
   - Follow the authentication process
5. Note down your **Service ID** (e.g., service_abc123)

## Step 3: Create Email Template
1. Go to "Email Templates" in your dashboard
2. Click "Create New Template"
3. Copy and paste this template content:

```
Subject: New Portfolio Contact - {{subject}}

Hello Divy,

You have received a new message from your portfolio website:

From: {{from_name}} ({{from_email}})
Subject: {{subject}}

Message:
{{message}}

---
This message was sent from your portfolio contact form.
Reply directly to this email to respond to {{from_name}}.
```

4. Save the template and note down your **Template ID** (e.g., template_xyz789)

## Step 4: Get Public Key
1. Go to "Account" → "General" in your dashboard
2. Copy your **Public Key** (e.g., user_abcdefghijk)

## Step 5: Update Configuration
1. Open `/components/email-config.ts` in your project
2. Replace the placeholder values with your actual credentials:

```typescript
export const emailConfig = {
  serviceId: 'service_abc123', // Your Service ID
  templateId: 'template_xyz789', // Your Template ID
  publicKey: 'user_abcdefghijk', // Your Public Key
  recipientEmail: 'pateldivy9808@gmail.com' // Your email (already set)
};
```

## Step 6: Test the Form
1. Save your changes
2. Test the contact form on your website
3. You should receive an email at pateldivy9808@gmail.com

## Features Included:
- ✅ Real-time email notifications
- ✅ Form validation
- ✅ Loading states and user feedback
- ✅ Automatic form reset after submission
- ✅ Professional email template
- ✅ Error handling and fallback messages

## Troubleshooting:
- **Error: "Email service not configured"**: Make sure you've updated the values in `email-config.ts`
- **Emails not received**: Check your spam folder and verify your EmailJS service is connected
- **Authentication issues**: Re-authenticate your email service in EmailJS dashboard

## EmailJS Free Tier:
- 200 emails per month
- Perfect for portfolio contact forms
- No credit card required

Your contact form will now send emails directly to your inbox whenever someone submits a message!