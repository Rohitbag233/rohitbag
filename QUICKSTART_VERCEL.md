# Quick Start: Deploy to Vercel in 5 Minutes

## Prerequisites
- GitHub account with your code pushed
- Supabase account with database set up
- Vercel account (free - sign up at [vercel.com](https://vercel.com))

## Step 1: Push to GitHub (1 minute)

```bash
git add .
git commit -m "Ready for Vercel deployment"
git push origin main
```

## Step 2: Deploy on Vercel (2 minutes)

1. Visit [vercel.com](https://vercel.com)
2. Click **"New Project"**
3. Import your GitHub repository
4. Click **"Import"**

## Step 3: Add Environment Variables (1 minute)

In the project configuration screen, add these two variables:

```
VITE_SUPABASE_URL = your_supabase_url_here
VITE_SUPABASE_ANON_KEY = your_supabase_anon_key_here
```

Get these from: Supabase Dashboard → Settings → API

## Step 4: Deploy (1 minute)

1. Click **"Deploy"**
2. Wait 60-90 seconds
3. ✅ **Your site is live!**

Visit your URL: `https://your-project.vercel.app`

---

## What's Been Optimized?

✅ **Code splitting** - Faster initial load  
✅ **Minification** - Smaller bundle size  
✅ **Tree shaking** - Removed unused code  
✅ **Asset caching** - CDN with 1-year cache  
✅ **Compression** - Automatic gzip/brotli  
✅ **SPA routing** - No 404 errors on refresh  
✅ **Security headers** - XSS protection, CSP  

## Next Steps

- Test all pages and features
- Add custom domain (optional)
- Enable Vercel Analytics
- Set up continuous deployment (already done!)

## Need Help?

See [VERCEL_DEPLOYMENT.md](VERCEL_DEPLOYMENT.md) for the full deployment guide.

---

That's it! Your optimized site is now live on Vercel. 🚀
