# Deploying to Vercel

This project is optimized for deployment on Vercel. Follow these steps to deploy:

## 1. Prerequisites
- A GitHub/GitLab/Bitbucket account
- A Vercel account (https://vercel.com)

## 2. Environment Variables
You MUST set the following Environment Variables in your Vercel Project Settings (Settings -> Environment Variables):

### Payment Gateway (PhonePe)
- `PHONEPE_MERCHANT_ID`: Your Merchant ID (or `MOCK_MERCHANT_ID` for testing)
- `PHONEPE_SALT_KEY`: Your Salt Key (or `MOCK_SALT_KEY` for testing)
- `PHONEPE_SALT_INDEX`: Your Salt Index (usually `1`)
- `PHONEPE_HOST_URL`: `https://api.phonepe.com/apis/hermes` (Production) or `https://api-preprod.phonepe.com/apis/pg-sandbox` (Testing)

### Google Sheets Integration
- `GOOGLE_CLIENT_EMAIL`: The email from your Google Service Account JSON
- `GOOGLE_PRIVATE_KEY`: The private key from your Google Service Account JSON (copy the entire string including `-----BEGIN PRIVATE KEY...`)
- `GOOGLE_SHEET_ID`: The ID of your Google Sheet (found in the URL)

### UPI Details
- `NEXT_PUBLIC_UPI_PA`: Your UPI ID (e.g., `business@bank`)
- `NEXT_PUBLIC_UPI_PN`: Payee Name (e.g., `CUCupid`)

### App URL (Optional but Recommended)
- `NEXT_PUBLIC_BASE_URL`: Your full domain (e.g., `https://your-store.vercel.app`). 
  - *Note: The code will automatically try to use Vercel's generated URL if this is not set, but setting it explicitly is safer.*

## 3. Deployment Steps
1. Push your code to a git repository (GitHub/GitLab/Bitbucket).
2. Log in to Vercel and click **"Add New..."** -> **"Project"**.
3. Import your repository.
4. In the **"Configure Project"** screen:
   - **Framework Preset**: Next.js (should be auto-detected)
   - **Root Directory**: `./` (default)
   - **Environment Variables**: Add all the variables listed above.
5. Click **"Deploy"**.

## 4. Troubleshooting
- **Google Sheets Error**: Ensure the Service Account email (`GOOGLE_CLIENT_EMAIL`) has "Editor" access to your Google Sheet (Share the sheet with that email).
- **Payment Callback 404**: Ensure `NEXT_PUBLIC_BASE_URL` is set correctly or that the Vercel URL is accessible.
