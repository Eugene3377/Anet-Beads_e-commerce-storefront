# 🛍️ Anet Beads E-commerce Storefront

A modern, fully-featured e-commerce platform built with **Next.js**, **TypeScript**, and **Tailwind CSS**. Featuring product browsing, real-time search, secure checkout with **Paystack**, order history tracking, authentication via **Firebase**, and error monitoring with **Sentry**.

🔗 **Live Demo:** [nadiabeads.netlify.app](https://nadiabeads.netlify.app/)

---

## Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Environment Variables](#environment-variables)
- [Sanity Studio](#sanity-studio)
- [API Routes](#api-routes)
- [Useful Scripts](#useful-scripts)
- [Deployment](#deployment)
- [Troubleshooting](#troubleshooting)
- [Resources](#resources)

---

## Features

✨ **Core Functionality**
- 📱 Responsive design for all devices
- 👕 Product browsing by category (Women, Men, Accessories)
- 🔍 Real-time search with debounced navigation
- 🛒 Shopping cart management with `use-shopping-cart`
- 💳 Secure checkout with **Paystack** payment integration
- 📦 Order history and order tracking
- 🌓 Dark and light theme support

🔐 **Authentication & Security**
- Firebase authentication with Google Sign-In
- Secure user sessions
- Protected routes and checkout flow

💼 **Content Management**
- **Sanity CMS** for dynamic product content
- Hero image management
- Category configuration
- Product details and pricing

📊 **Monitoring & Analytics**
- **Sentry** error tracking and monitoring
- Real-time issue alerts
- Performance tracking

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| **Framework** | Next.js 14, React 18 |
| **Language** | TypeScript |
| **Styling** | Tailwind CSS, shadcn/ui, Radix UI |
| **Database** | MongoDB with Mongoose, Sanity CMS |
| **Authentication** | Firebase Auth |
| **Payments** | Paystack, Stripe (optional) |
| **Monitoring** | Sentry |
| **Cart Management** | use-shopping-cart |

---

## Project Structure

```
e-commerce-main/
├── src/
│   ├── app/                  # Next.js 14 App Router
│   │   ├── api/              # API routes (orders, auth, webhooks)
│   │   ├── (routes)/         # Route groups for organization
│   │   ├── layout.tsx        # Root layout with theme
│   │   └── page.tsx          # Home page
│   │
│   ├── components/           # Reusable UI components
│   │   ├── ProductCard.tsx   # Product display component
│   │   ├── Cart/             # Shopping cart components
│   │   ├── Navbar.tsx        # Navigation bar
│   │   ├── Footer.tsx        # Footer section
│   │   └── ...
│   │
│   ├── lib/                  # Utilities and configurations
│   │   ├── firebase.ts       # Firebase initialization
│   │   ├── mongodb.ts        # MongoDB connection
│   │   ├── sanity.ts         # Sanity client & queries
│   │   ├── stripe.ts         # Stripe configuration
│   │   └── utils/            # Helper functions
│   │
│   ├── hooks/                # Custom React hooks
│   │   ├── useCart.ts        # Cart management
│   │   ├── useAuth.ts        # Authentication context
│   │   └── ...
│   │
│   └── styles/               # Global styles
│
├── public/                   # Static assets (images, icons)
│
├── sanity/                   # Separate Sanity Studio project
│   ├── schemaTypes/          # Product, category, hero schemas
│   └── package.json
│
├── .env.example              # Environment variables template
├── .env.local                # Local environment (not committed)
├── tailwind.config.ts        # Tailwind CSS configuration
├── tsconfig.json             # TypeScript configuration
└── package.json              # Dependencies
```

---

## Getting Started

### Prerequisites

- **Node.js** 18+ (check with `node --version`)
- **npm** 9+ or **yarn** 3.6+
- Accounts for:
  - Firebase (Google Cloud)
  - MongoDB Atlas
  - Paystack
  - Sanity
  - (Optional) Stripe

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Eugene3377/Anet-Beads_e-commerce-storefront.git
   cd Anet-Beads_e-commerce-storefront
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Create environment file:**
   ```bash
   cp .env.example .env.local
   ```

4. **Fill in your credentials** (see [Environment Variables](#environment-variables))

5. **Start the development server:**
   ```bash
   npm run dev
   ```

6. Open [http://localhost:3000](http://localhost:3000) in your browser

---

## Environment Variables

Create a `.env.local` file in the project root. Here's where to get each value:

### Firebase Configuration
| Variable | Source | Required |
|----------|--------|----------|
| `NEXT_PUBLIC_FIREBASE_API_KEY` | Firebase Console → Project Settings → Web API Key | ✅ |
| `NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN` | Firebase Console → Project Settings | ✅ |
| `NEXT_PUBLIC_FIREBASE_PROJECT_ID` | Firebase Console → Project Settings | ✅ |
| `NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET` | Firebase Console → Storage | ✅ |
| `NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID` | Firebase Console → Project Settings | ✅ |
| `NEXT_PUBLIC_FIREBASE_APP_ID` | Firebase Console → Project Settings | ✅ |

### Database & Payments
| Variable | Source | Required |
|----------|--------|----------|
| `MONGODB_URI` | MongoDB Atlas → Connect → Connection String | ✅ |
| `NEXT_PUBLIC_PAYSTACK_KEY` | Paystack Dashboard → Settings → API Keys (Public Key) | ✅ |
| `NEXT_PUBLIC_STRIPE_KEY` | Stripe Dashboard → API Keys (Publishable Key) | ❌ |

### Example `.env.local`:
```env
# Firebase
NEXT_PUBLIC_FIREBASE_API_KEY=AIzaSyD...
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=anetbeads.firebaseapp.com
NEXT_PUBLIC_FIREBASE_PROJECT_ID=anetbeads
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=anetbeads.appspot.com
NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=123456789
NEXT_PUBLIC_FIREBASE_APP_ID=1:123456789:web:abc123def456

# Database
MONGODB_URI=mongodb+srv://user:password@cluster.mongodb.net/anetbeads

# Payments
NEXT_PUBLIC_PAYSTACK_KEY=pk_live_abc123...
NEXT_PUBLIC_STRIPE_KEY=pk_live_xyz789...
```

⚠️ **Security Note:** Never commit `.env.local` to Git. The `.gitignore` file should already exclude it.

---

## Sanity Studio

The content management system (CMS) is in the `sanity/` folder and is deployed separately.

### Local Development

```bash
cd sanity
npm install
npm run dev
```

Then open the URL shown in the terminal (usually `http://localhost:3333`) to manage:
- 📦 Products (name, price, images, description)
- 🏷️ Categories (women, men, accessories)
- 🖼️ Hero images (homepage banners)

### Deployment

```bash
cd sanity
npm run deploy
```

Follow the prompts to deploy to Sanity's hosted studios.

---

## API Routes

The Next.js app includes API routes for backend logic:

| Endpoint | Method | Purpose |
|----------|--------|---------|
| `/api/orders` | `POST` | Create a new order |
| `/api/orders` | `GET` | Fetch user's order history |
| `/api/orders/:id` | `GET` | Get order details |
| `/api/checkout` | `POST` | Initialize Paystack checkout session |
| `/api/auth/user` | `GET` | Get current user info |
| `/api/webhook/paystack` | `POST` | Handle Paystack payment webhook |

---

## Useful Scripts

```bash
# Development
npm run dev              # Start development server (http://localhost:3000)
npm run build            # Build for production
npm run start            # Run production build locally

# Linting & Quality
npm run lint             # Run Next.js linting
npm run type-check       # Run TypeScript type checking (if configured)
```

---

## Deployment

This project is optimized for **Vercel** (the creators of Next.js), but works on any Node.js host.

### Deploy to Vercel (Recommended)

1. Push your code to GitHub
2. Import the repository in [Vercel Dashboard](https://vercel.com)
3. Add environment variables in Vercel Project Settings
4. Click "Deploy"

### Deploy Sanity Studio Separately

```bash
cd sanity
npm run deploy
```

### Deploy to Other Platforms

For platforms like Netlify, AWS Amplify, or self-hosted:

1. Ensure `npm run build` succeeds locally
2. Set all environment variables in your hosting dashboard
3. Run `npm run start` to start the production server

---

## Troubleshooting

### Port 3000 Already in Use
```bash
# Find and kill the process
lsof -ti:3000 | xargs kill -9

# Or use a different port
npm run dev -- -p 3001
```

### Firebase Connection Error
- Verify all `NEXT_PUBLIC_FIREBASE_*` variables are correctly set
- Ensure Firebase project exists and is active
- Check firestore/realtime database rules allow read/write

### MongoDB Connection Failed
- Verify `MONGODB_URI` connection string is correct
- Check MongoDB Atlas cluster is running and IP whitelist includes your IP
- Ensure database user has correct permissions

### Paystack Payment Issues
- Verify `NEXT_PUBLIC_PAYSTACK_KEY` is the **public key**, not secret
- Check Paystack account is activated (not in test mode)
- Review Paystack webhook configuration in dashboard

### Build Fails with TypeScript Errors
```bash
npm run type-check  # Check for TS errors
npm run lint        # Check for linting issues
```

### Sentry Not Capturing Errors
- Verify Sentry DSN is set in your project
- Check Sentry project is active and organization settings are correct
- Review Sentry integration setup in `src/lib/sentry.ts`

---

## Resources

### Documentation
- [Next.js 14 Docs](https://nextjs.org/docs)
- [Firebase Authentication](https://firebase.google.com/docs/auth)
- [MongoDB Atlas](https://docs.atlas.mongodb.com/)
- [Sanity CMS Documentation](https://www.sanity.io/docs)
- [Paystack Integration Guide](https://paystack.com/docs/payments/accept-payments)
- [Sentry Error Tracking](https://docs.sentry.io/)

### UI Components
- [shadcn/ui Components](https://ui.shadcn.com/)
- [Radix UI Primitives](https://www.radix-ui.com/docs/primitives/overview/introduction)
- [Tailwind CSS Docs](https://tailwindcss.com/docs)

### Community & Support
- [GitHub Issues](https://github.com/Eugene3377/Anet-Beads_e-commerce-storefront/issues)
- [Discussions](https://github.com/Eugene3377/Anet-Beads_e-commerce-storefront/discussions)

---

## License

This project is open source. Refer to the LICENSE file for details.

---

**Made with ❤️ by Eugene3377**
