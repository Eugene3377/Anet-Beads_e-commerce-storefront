# Anet Beads E-commerce Store

A responsive fashion and accessories storefront built with Next.js, TypeScript, Tailwind CSS, Sanity, Firebase, MongoDB, Stripe, Paystack, and Sentry.

The app includes product browsing, category pages, search, cart handling, authentication, checkout integrations, and a separate Sanity Studio for managing product content.

## Features

- Next.js app router with TypeScript
- Fashion categories for women, men, and accessories
- Product details, newest products, and category listing pages
- Search flow with debounced navigation
- Shopping cart powered by `use-shopping-cart`
- Firebase authentication with Google support
- MongoDB order storage through API routes
- Sanity CMS product and hero-image content
- Stripe and Paystack checkout hooks
- Dark and light theme support
- Sentry monitoring configuration

## Tech Stack

- Next.js 14
- React 18
- TypeScript
- Tailwind CSS
- shadcn/ui and Radix UI components
- Firebase
- MongoDB and Mongoose
- Sanity
- Stripe
- Paystack
- Sentry

## Project Structure

```text
e-commerce-main/
  src/app/              Next.js pages, layouts, API routes, and route groups
  src/components/       Storefront UI components
  src/lib/              Firebase, MongoDB, Sanity, and utility helpers
  src/hooks/            Reusable React hooks
  public/               Static images and icons
  sanity/               Sanity Studio project
```

## Getting Started

Install dependencies:

```bash
npm install
```

Create a local environment file:

```bash
cp .env.example .env.local
```

Fill in the Firebase, MongoDB, Stripe, and Paystack values in `.env.local`.

Run the storefront:

```bash
npm run dev
```

Open `http://localhost:3000`.

## Environment Variables

The app reads these values:

```env
NEXT_PUBLIC_FIREBASE_API_KEY=
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=
NEXT_PUBLIC_FIREBASE_PROJECT_ID=
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=
NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=
NEXT_PUBLIC_FIREBASE_APP_ID=
MONGODB_URI=
NEXT_PUBLIC_STRIPE_KEY=
NEXT_PUBLIC_PAYSTACK_KEY=
```

## Sanity Studio

The Sanity Studio lives in `sanity/`.

```bash
cd sanity
npm install
npm run dev
```

Open the studio URL shown in the terminal and manage products, categories, and hero images there.

## Useful Scripts

```bash
npm run dev      # Start the development server
npm run build    # Build for production
npm run start    # Start the production build
npm run lint     # Run the configured Next.js lint command
```

## Deployment

This project is suitable for Vercel or any host that supports Next.js. Add the environment variables in the hosting dashboard before deploying.

If using Sanity Studio, deploy it separately from the `sanity/` folder:

```bash
cd sanity
npm run deploy
```

## Notes

- Keep `.env.local` out of Git.
- Review checkout keys before production deployment.
- Update the Sentry DSN and organization settings for the production account before going live.
