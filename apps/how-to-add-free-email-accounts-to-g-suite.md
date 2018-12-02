# How to add free email accounts to G Suite

The tutorial below explains how to mix paid G Suite accounts with free Gmail accounts using a custom domain.

You'll need at least one paid G Suite account - Basic, Business or Enterprise. You won't be able to use any G Suite functionality (such as shared team drives on Google Drive) on your additional free Gmail inboxes.

To add free additional inboxes to G Suite, you'll use the G Suite email forwarding option (to forward emails from your custom domain to free Gmail inbox) and "Send email us" option from free Gmail (to send emails using your custom domain).

1. Set up SMTP server in G Suite (custom domain)
    - Open Google Admin console
    - Go to Apps, click the G Suite tile, then Gmail row, then Advanced settings (at the very bottom)
    - Turn on SMTP relay service
        - Name it something like "Non-G Suite email accounts"
        - Allowed senders - only addresses in my domain
        - Tick "Require SMTP Authentication"
        - Tick "Require TLS encryption"
2. Configure email forwarding in G Suite
    - Remain in Advanced Settings
    - Open the Default routing tab
    - Add setting
        - Single recipient - the email address in your domain, from which emails will be forwarded
        - Tick "Add X-Gm-Original-To header" in "Headers" section (this will allow Gmail to display the actual recipient address)
        - Tick "Add more recipients" in "Also deliver to" section
        - Press Add
        - Select Advanced mode from the dropdown
        - Provide email address you want to forward emails to
        - Uncheck "Do not deliver spam to this recipient" (you'll use your Gmail spam filter; otherwise mails classified as spam will not be forwarded and you won't be able to review them in the Spam folder)
3. Generate an App password to allow Gmail to sign in the SMTP server
    - If you haven't already, enable 2-step verification in G Suite
    - Go to [https://security.google.com/settings/security/apppasswords](https://security.google.com/settings/security/apppasswords)
    - Re-authenticate using G Suite credentials
    - Generate a new password
        - Select Gmail from the application dropdown
        - Select Other device from the device dropdown
    - Copy your password to clipboard
4. Configure sending emails through your custom domain from a free Gmail account
    - Create a new free Gmail account or log into existing one
    - Go to Settings > Accounts and Import
    - Click "Add another email address" in "Send email as" section
    - Type:
        - Name - your display name for all emails you'll send through your custom domain
        - Email address - your custom domain email address
    - Press next
    - Type:
        - SMTP Server - smtp-relay.gmail.com
        - Username - your G Suite login
        - Password - App password you generated previously
    - The popup should close
    - You can click "Make default" next to your newly added address if you want to send emails with this address by default
