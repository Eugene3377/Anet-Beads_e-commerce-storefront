# Anet Beads Sanity Studio

This folder contains the Sanity Studio used to manage storefront content for the Anet Beads e-commerce app.

## Content Types

- Products
- Categories
- Hero images

## Getting Started

Install dependencies:

```bash
npm install
```

Start the studio:

```bash
npm run dev
```

Sanity will print the local studio URL in the terminal.

## Scripts

```bash
npm run dev              # Start the local Studio
npm run build            # Build the Studio
npm run deploy           # Deploy the Studio
npm run deploy-graphql   # Deploy the GraphQL API
```

## Configuration

The Studio is configured in `sanity.config.ts` and currently uses:

- Project ID: `jbtkn2lg`
- Dataset: `production`
