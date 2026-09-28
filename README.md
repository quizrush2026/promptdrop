# PromptDrop — Complete Netlify Version

This is the single-site version: frontend + Netlify Functions + persistent Netlify Blobs storage.

## What is included
- Automatic image feed from a licensed image API (Unsplash API)
- Automatic prompt creation from image metadata, with optional AI prompt generation
- Search and categories
- Locked prompts
- ₹2 payment link creation through Razorpay
- Server-side payment webhook verification
- Automatic unlock after payment confirmation
- Persistent purchase records using Netlify Blobs
- Admin endpoint for adding your own licensed photos/prompts
- No Instagram scraping

## REQUIRED before accepting real payments
Set these Netlify environment variables:
- RAZORPAY_KEY_ID
- RAZORPAY_KEY_SECRET
- RAZORPAY_WEBHOOK_SECRET

The Razorpay merchant account must be your authorized account. Your UPI ID is not a replacement for a payment-gateway merchant account; the gateway account is what processes and verifies payments.

## Automatic photos
Set:
- UNSPLASH_ACCESS_KEY

The site uses the Unsplash API. Use only images permitted by that provider's terms. The website does not scrape Instagram.

## Optional automatic AI prompts
Set:
- AI_API_URL
- AI_API_KEY
- AI_MODEL

If those are absent, the site generates a deterministic prompt from the image title/description instead, so the site still works.

## Deploy
Upload the contents of this project to your Netlify site. Because this project includes Netlify Functions, the recommended route is a Git-connected deploy or Netlify CLI/API deploy rather than uploading only `public`.

Then set environment variables in:
Project configuration → Environment variables.

For Razorpay, configure a webhook URL:
https://YOUR-SITE.netlify.app/api/payment-webhook

Subscribe to the Payment Link paid event and use the same webhook secret as RAZORPAY_WEBHOOK_SECRET.

## Important
Never put RAZORPAY_KEY_SECRET, webhook secrets, or AI secrets into browser JavaScript.
