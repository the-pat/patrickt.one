---
layout: post
title: "Custom Domains and Gmail"
date: 2020-01-02 14:12 -0600
---

This post walks through the process of using Gmail with a custom domain name _for free_.

## 1. Create a Gmail Account

You can use a personal Gmail account or [create a new one](https://accounts.google.com/SignUp). Either way you will need an account. Personally, I like to keep my professional and personal accounts separate.

![Create a Gmail Account](/assets/images/custom-domains-and-gmail/00-create-gmail-account.jpg)

## 2. Purchase a domain

Next, you will need a domain. If you have one, feel free to skip this section.

I purchased this domain from [Namecheap](https://www.namecheap.com/), but I hear good things about [Google Domains](https://domains.google/). Students can get a free/discounted domain with the [GitHub Student Developer Pack](https://education.github.com/pack).

![Google Domains](/assets/images/custom-domains-and-gmail/01-purchase-domain.jpg)

## 3. Create a Mailgun account

After this step the real fun begins. I use [Mailgun](https://www.mailgun.com/) as my domain's email service. Some DNS providers have an email forwarding service, but this tutorial does not explore that route.

Mailgun does require a Credit Card on file to send emails. After you create your account, don't forget to confirm your email address.

![Mailgun Home Page](/assets/images/custom-domains-and-gmail/02-create-mailgun-account.jpg)

## 4. Add and verify your domain

Find the **Getting Started** section on the right-side of the Mailgun dashboard. Follow the link to _Add a custom domain_.

Create your subdomain (`patrickt.one`). Keep the **Create DKIM Authority** checked and select **2048** for extra security.

Mailgun provides step-by-step directions for adding the DNS records for your DNS provider. I recommend you add all the records to your DNS records (2 TXT, 2 MX, and 1 CNAME). Now we wait for the DNS records to update (may take up to 48 hours...).

![Set up Mailgun](/assets/images/custom-domains-and-gmail/03-set-up-mailgun.jpg)

## 5. Set up routing

With Mailgun you have the ability to set up **routes** (Receiving > Create Route). This allows you to forward mail to different email addresses. With a personal domain, I find having one _catch all_ route sufficient.

- **Expression Type:** Catch All
- **Forward:** Selected + your gmail address
- **Priority:** 10

![Set up routes](/assets/images/custom-domains-and-gmail/04-set-up-routes.jpg)

## 6. Set up SMTP credentials

Now you need to create STMP credentials for the account you want to send emails as. Note: the catch all route allows you to receive all the emails, but you'll need STMP credentials to send emails from Gmail.

To add an STMP credential, navigate to your domain settings (Sending > Domain settings > SMTP credentials > New STMP User). Choose the email address you'd like to send emails as (`hello@patrickt.one`). Take note of the password.

![Set up STMP credentials](/assets/images/custom-domains-and-gmail/05-stmp-creds.jpg)

### (Optional) Set up _Open_ tracking

Go to the Domain settings > Open tracking and set tracking to **On**.

## 7. Send from Gmail

Finally to Gmail. On the right side of the page, click the gear icon > Settings > Accounts and Import > Send mail as > Add another email address.

1. **Name:** `your name (or whatever you'd like to show up)`

   **Email address:** `<the SMTP email address you created (hello@patrickt.one)>`

   **Treat as an alias:** `checked`

2. **SMTP Server:** `smtp.mailgun.org`

   **Port:** 587

   **Username:** `hello@patrickt.one`

   **Password:** `<password from earlier>`

   **Secured connection using TLS:** `selected`

If everything goes as expected, you will receive an email from Google with a verification code (or link).

![Send email as](/assets/images/custom-domains-and-gmail/06-send-email-as.jpg)

_**Voilà!**_ You can now send emails with your custom domain with Gmail.
