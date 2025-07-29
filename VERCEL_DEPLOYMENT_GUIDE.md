# 🚀 Deploy Your Portfolio to Vercel

## Overview
Your portfolio is built with React and Tailwind CSS, making it perfect for Vercel deployment. Vercel offers excellent performance, automatic HTTPS, and seamless CI/CD integration.

## Prerequisites
- GitHub account (recommended method)
- Vercel account (free tier available)
- Your portfolio code ready

## Step 1: Prepare Your Project

### Create package.json
First, you'll need to create a `package.json` file in your project root:

```json
{
  "name": "divy-patel-portfolio",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview",
    "lint": "eslint . --ext ts,tsx --report-unused-disable-directives --max-warnings 0"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "lucide-react": "^0.263.1",
    "sonner": "^1.4.41",
    "class-variance-authority": "^0.7.0",
    "clsx": "^2.0.0",
    "tailwind-merge": "^1.14.0"
  },
  "devDependencies": {
    "@types/react": "^18.2.15",
    "@types/react-dom": "^18.2.7",
    "@typescript-eslint/eslint-plugin": "^6.0.0",
    "@typescript-eslint/parser": "^6.0.0",
    "@vitejs/plugin-react": "^4.0.3",
    "autoprefixer": "^10.4.14",
    "eslint": "^8.45.0",
    "eslint-plugin-react-hooks": "^4.6.0",
    "eslint-plugin-react-refresh": "^0.4.3",
    "postcss": "^8.4.27",
    "tailwindcss": "^3.3.0",
    "typescript": "^5.0.2",
    "vite": "^4.4.5"
  }
}
```

### Create vite.config.ts
```typescript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
  build: {
    outDir: 'dist',
  }
})
```

### Create index.html
```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta name="description" content="Divy Patel - UI/UX Designer & Figma Expert Portfolio" />
    <meta name="keywords" content="UI/UX Designer, Figma Expert, Portfolio, Web Design" />
    <meta name="author" content="Divy Patel" />
    <title>Divy Patel - UI/UX Designer & Figma Expert</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.tsx"></script>
  </body>
</html>
```

### Create src/main.tsx
```typescript
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from '../App.tsx'
import '../styles/globals.css'

ReactDOM.createRoot(document.getElementById('root')!).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
)
```

## Step 2: Push to GitHub

1. **Initialize Git Repository**
   ```bash
   git init
   git add .
   git commit -m "Initial commit: Portfolio website"
   ```

2. **Create GitHub Repository**
   - Go to [GitHub.com](https://github.com)
   - Click "New repository"
   - Name it "divy-patel-portfolio" (or your preferred name)
   - Make it public
   - Don't initialize with README (since you already have files)

3. **Push to GitHub**
   ```bash
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/divy-patel-portfolio.git
   git push -u origin main
   ```

## Step 3: Deploy to Vercel

### Method 1: GitHub Integration (Recommended)

1. **Sign up for Vercel**
   - Go to [vercel.com](https://vercel.com)
   - Sign up with GitHub account

2. **Import Project**
   - Click "New Project"
   - Select "Import Git Repository"
   - Choose your portfolio repository
   - Click "Import"

3. **Configure Project**
   - **Project Name**: `divy-patel-portfolio`
   - **Framework Preset**: Vite
   - **Root Directory**: `./` (leave as default)
   - **Build Command**: `npm run build`
   - **Output Directory**: `dist`
   - **Install Command**: `npm install`

4. **Deploy**
   - Click "Deploy"
   - Wait for deployment to complete (usually 1-2 minutes)

### Method 2: Vercel CLI (Alternative)

1. **Install Vercel CLI**
   ```bash
   npm i -g vercel
   ```

2. **Deploy**
   ```bash
   vercel
   ```
   - Follow the prompts
   - Choose your settings when asked

## Step 4: Configure Custom Domain (Optional)

1. **Buy a Domain** (if you don't have one)
   - Namecheap, GoDaddy, or any domain registrar
   - Suggestions: `divypatel.dev`, `divypatel.design`, `divyux.com`

2. **Add Domain in Vercel**
   - Go to your project dashboard
   - Click "Domains"
   - Add your custom domain
   - Follow DNS configuration instructions

3. **Update DNS Records**
   - Add CNAME record pointing to Vercel
   - Wait for propagation (up to 24 hours)

## Step 5: Environment Variables (If Needed)

If you add email functionality later:
1. Go to project settings in Vercel
2. Click "Environment Variables"
3. Add your email service keys

## Step 6: Automatic Deployments

Once connected to GitHub:
- Every push to `main` branch automatically deploys
- Preview deployments for pull requests
- Rollback capability

## Performance Optimizations

### Add these to your project:

1. **Create vercel.json** (optional)
```json
{
  "buildCommand": "npm run build",
  "outputDirectory": "dist",
  "framework": "vite",
  "rewrites": [
    {
      "source": "/(.*)",
      "destination": "/index.html"
    }
  ]
}
```

2. **Optimize Images**
   - Use WebP format when possible
   - Add lazy loading
   - Compress images

## Monitoring & Analytics

1. **Vercel Analytics** (Free)
   - Automatically enabled
   - View in project dashboard

2. **Google Analytics** (Optional)
   - Add tracking code to index.html
   - Monitor visitor data

## Security Headers

Add to `vercel.json`:
```json
{
  "headers": [
    {
      "source": "/(.*)",
      "headers": [
        {
          "key": "X-Frame-Options",
          "value": "DENY"
        },
        {
          "key": "X-Content-Type-Options",
          "value": "nosniff"
        }
      ]
    }
  ]
}
```

## Troubleshooting

### Common Issues:
1. **Build Fails**: Check package.json dependencies
2. **404 Errors**: Ensure routing is configured correctly
3. **CSS Not Loading**: Check import paths
4. **Images Not Showing**: Verify image paths and formats

### Build Commands:
- **Development**: `npm run dev`
- **Build**: `npm run build`
- **Preview**: `npm run preview`

## Cost

- **Free Tier**: 100GB bandwidth, unlimited personal projects
- **Pro Tier**: $20/month for more features
- **Custom domains**: Free with any plan

## Final Steps

1. Test your live site thoroughly
2. Update social media links with your new URL
3. Share your portfolio!

## Your Live URLs

Once deployed, you'll get:
- **Vercel URL**: `https://divy-patel-portfolio.vercel.app`
- **Custom Domain**: `https://yourdomain.com` (if configured)

---

🎉 **Congratulations!** Your portfolio is now live and accessible worldwide!

## Next Steps After Deployment

- Set up Google Analytics
- Add contact form functionality
- Optimize for SEO
- Add more projects
- Consider adding a blog section

---

*Need help? The Vercel community and documentation are excellent resources.*