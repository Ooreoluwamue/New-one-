# ELLA 2026 Registration App

A responsive registration web app for the NAAS Aba North Zone ELLA 2026 Ladies Summit.

## What it does

- Collects full name, gender, phone number and T-shirt size.
- Shows the UBA payment instructions for the N13,000 registration fee.
- Requires payment-receipt upload before a registration is confirmed.
- Blocks a second registration using the same phone number.
- Generates an ELLA26 registration code.
- Provides a private PRO dashboard with attendee list, shirt-size totals, receipt viewing and check-in.

## Supabase setup

1. In Supabase, open **SQL Editor** > **New query**.
2. Copy all contents of `supabase/schema.sql`, paste, then click **Run**.
3. Go to **Authentication** > **Users** > **Add user** > **Create new user**.
4. Create the sole admin user with `Ooreoluwaadedeji904@gmail.com` and set a strong password.
5. In **Authentication** > **URL Configuration**, add your future Vercel URL under **Site URL** and **Redirect URLs** after deployment.

## Run locally

1. Install Node.js 20 or later.
2. Copy `.env.example` to `.env`.
3. Replace `sb_publishable_REPLACE_WITH_YOUR_KEY` with the Publishable key from Supabase Settings > API Keys.
4. In a terminal in this folder, run:

```bash
npm install
npm run dev
```

Open the shown local address. The app routes are `/`, `/register`, and `/admin`.

## Deploy to Vercel

1. Create a GitHub account/repository, upload this project, and sign in to Vercel.
2. Choose **Add New > Project**, import the GitHub repository, then choose **Deploy**.
3. Before deploying, add these Vercel environment variables:

```text
VITE_SUPABASE_URL=https://ohxdxrqykdeezviupppo.supabase.co
VITE_SUPABASE_PUBLISHABLE_KEY=your Supabase Publishable key
```

4. Redeploy after saving variables.
5. In Supabase > Authentication > URL Configuration, add the Vercel deployment URL.
6. Open `https://your-vercel-domain.vercel.app/admin` and sign in with the PRO email and password you created.

## Important security notes

- Do not put the `sb_secret_` key or any service-role key into Vercel or this project.
- Keep the `payment-receipts` bucket private.
- The supplied policies allow the public to submit registrations and receipts, while only the specified PRO email can read registrations and receipts.
- The unique `phone` column is the server-side duplicate prevention rule.

## Flyer

Place your official summit flyer at `public/ella-flyer.jpg` if you want it visible as the home-page hero background. The app works without it.
