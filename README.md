This is a [Next.js](https://nextjs.org) project with Google Authentication using NextAuth.js.

## Features

- 🔐 Google OAuth Authentication
- 🎨 Modern UI with Tailwind CSS
- ⚡ Next.js 15 with App Router
- 🔄 Session Management

## Prerequisites

Before running this project, you need to set up Google OAuth credentials.

## Google Cloud Console Setup

### 1. Create a Google Cloud Project

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select an existing one
3. Enable the Google+ API

### 2. Create OAuth 2.0 Credentials

1. Navigate to **APIs & Services** > **Credentials**
2. Click **+ CREATE CREDENTIALS** > **OAuth client ID**
3. Choose **Web application** as the application type
4. Configure the OAuth consent screen if prompted

### 3. Configure OAuth Client

Fill in the following details:

**Name:** `Next.js Google Auth` (or any name you prefer)

**Authorized JavaScript origins:**

```
http://localhost:3000
```

**Authorized redirect URIs:**

```
http://localhost:3000/api/auth/callback/google
```

### 4. Get Your Credentials

After creating the OAuth client, you'll get:

- **Client ID** (looks like: `123456789-abcdefghijk.apps.googleusercontent.com`)
- **Client Secret** (looks like: `GOCSPX-abcdefghijklmnopqrstuvwx`)

## Environment Setup

### 1. Create Environment File

Create a `.env.local` file in the root directory:

```bash
cp .env.example .env.local
```

### 2. Add Your Credentials

Edit `.env.local` and replace the placeholder values:

```env
NEXTAUTH_URL=http://localhost:3000
NEXTAUTH_SECRET=your-secret-key-here
GOOGLE_CLIENT_ID=your-google-client-id-here
GOOGLE_CLIENT_SECRET=your-google-client-secret-here
```

**Important:**

- Replace `your-secret-key-here` with a random string (you can generate one using `openssl rand -base64 32`)
- Replace `your-google-client-id-here` with your actual Google Client ID
- Replace `your-google-client-secret-here` with your actual Google Client Secret

## Getting Started

First, install dependencies and run the development server:

```bash
# Install dependencies
npm install
# or
yarn install
# or
pnpm install

# Run the development server
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

## Usage

1. **Sign In:** Click the "Sign in with Google" button
2. **Authentication:** You'll be redirected to Google's OAuth page
3. **Authorization:** Grant permissions to your application
4. **Success:** You'll be redirected back with your Google account information

## Troubleshooting

### Common Issues

**Error 400: redirect_uri_mismatch**

- Make sure your redirect URI in Google Cloud Console is exactly: `http://localhost:3000/api/auth/callback/google`
- Check that there are no trailing slashes or typos

**Environment Variables Not Loading**

- Ensure your `.env.local` file is in the root directory
- Restart your development server after changing environment variables
- Check that all required variables are set

**Session Issues**

- Clear your browser cookies and try again
- Make sure `NEXTAUTH_SECRET` is set to a secure random string

### Development Tips

- Use browser developer tools to check for console errors
- Check the terminal for server-side error messages
- Verify your Google Cloud Console settings match the URLs in your environment variables

## Project Structure

```
├── app/
│   ├── api/auth/[...nextauth]/route.js  # NextAuth.js configuration
│   ├── lib/auth.js                      # Auth helper functions
│   ├── providers.tsx                    # Session provider wrapper
│   ├── layout.tsx                       # Root layout with providers
│   └── page.tsx                         # Main page with auth UI
├── .env.example                         # Environment variables template
└── .env.local                          # Your actual environment variables (not in git)
```

This project uses:

- [`next/font`](https://nextjs.org/docs/app/building-your-application/optimizing/fonts) for font optimization
- [NextAuth.js](https://next-auth.js.org/) for authentication
- [Tailwind CSS](https://tailwindcss.com/) for styling

## Deployment

### Environment Variables for Production

When deploying to production, make sure to update your environment variables:

```env
NEXTAUTH_URL=https://your-domain.com
NEXTAUTH_SECRET=your-production-secret-key
GOOGLE_CLIENT_ID=your-production-google-client-id
GOOGLE_CLIENT_SECRET=your-production-google-client-secret
```

### Google Cloud Console for Production

Update your Google OAuth client with production URLs:

**Authorized JavaScript origins:**

```
https://your-domain.com
```

**Authorized redirect URIs:**

```
https://your-domain.com/api/auth/callback/google
```

### Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme):

1. Push your code to GitHub
2. Connect your repository to Vercel
3. Add environment variables in Vercel dashboard
4. Deploy!

Check out our [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying) for more details.

## Learn More

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API
- [NextAuth.js Documentation](https://next-auth.js.org/) - learn about NextAuth.js
- [Google OAuth Documentation](https://developers.google.com/identity/protocols/oauth2) - learn about Google OAuth
- [Tailwind CSS Documentation](https://tailwindcss.com/docs) - learn about Tailwind CSS

## Contributing

Feel free to submit issues and enhancement requests!

## License

This project is open source and available under the [MIT License](LICENSE).
