# Vercel Deployment Guide for Rohit's Personal Website

This guide will walk you through deploying your personal website to Vercel.

## Prerequisites

- A [Vercel](https://vercel.com) account (free tier works great!)
- A [Supabase](https://supabase.com) account with your database configured
- Your code pushed to a Git repository (GitHub, GitLab, or Bitbucket)

## Quick Deploy to Vercel

### Method 1: Deploy via Vercel Dashboard (Recommended)

1. **Push Your Code to GitHub**
   ```bash
   git add .
   git commit -m "Optimize for Vercel deployment"
   git push origin main
   ```

2. **Visit Vercel**
   - Go to [vercel.com](https://vercel.com)
   - Sign up or log in
   - Click **"Add New Project"**

3. **Import Your Repository**
   - Click **"Import Git Repository"**
   - Select your GitHub repository
   - Click **"Import"**

4. **Configure Your Project**
   - **Framework Preset**: Vite (auto-detected)
   - **Root Directory**: `./` (default)
   - **Build Command**: `npm run build` (auto-detected)
   - **Output Directory**: `dist` (auto-detected)
   - Leave other settings as default

5. **Add Environment Variables**
   Click on **"Environment Variables"** and add:
   
   ```
   VITE_SUPABASE_URL=your_supabase_project_url
   VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
   ```
   
   Get these from your Supabase project:
   - Go to Supabase Dashboard → **Settings** → **API**
   - Copy the **Project URL** and **anon public** key

6. **Deploy**
   - Click **"Deploy"**
   - Wait 1-2 minutes for the build to complete
   - Your site will be live at `https://your-project-name.vercel.app`

### Method 2: Deploy via Vercel CLI

1. **Install Vercel CLI**
   ```bash
   npm install -g vercel
   ```

2. **Login to Vercel**
   ```bash
   vercel login
   ```

3. **Deploy**
   ```bash
   vercel
   ```
   
   Follow the prompts:
   - Set up and deploy? **Y**
   - Which scope? Select your account
   - Link to existing project? **N**
   - What's your project's name? Enter a name
   - In which directory is your code located? **.**
   - Want to override the settings? **N**

4. **Add Environment Variables**
   ```bash
   vercel env add VITE_SUPABASE_URL
   vercel env add VITE_SUPABASE_ANON_KEY
   ```
   
   Paste your values when prompted.

5. **Deploy to Production**
   ```bash
   vercel --prod
   ```

## After Deployment

### 1. Verify Your Site

Visit your Vercel URL and test:
- ✅ Homepage loads correctly
- ✅ All pages are accessible (Story, Projects, Advice Museum, Contact)
- ✅ Forms submit correctly (Contact, Advice submissions)
- ✅ Admin panel is accessible at `/admin/login`
- ✅ Responsive design works on mobile
- ✅ Dark/light theme toggle works

### 2. Configure Custom Domain (Optional)

1. **In Vercel Dashboard**
   - Go to your project
   - Click **"Settings"** → **"Domains"**
   - Click **"Add Domain"**
   - Enter your domain name

2. **Configure DNS**
   - Add the DNS records shown by Vercel
   - For apex domain (`example.com`): Add A record
   - For subdomain (`www.example.com`): Add CNAME record
   - Wait for DNS propagation (5-30 minutes)

3. **Automatic HTTPS**
   - Vercel automatically provisions SSL certificates
   - Your site will be accessible via HTTPS

### 3. Set Up Continuous Deployment

Vercel automatically deploys:
- **Production**: Every push to `main` branch
- **Preview**: Every pull request gets a unique URL
- **Instant Rollbacks**: Revert to any previous deployment

## Environment Variables

Required environment variables:

| Variable | Description | Where to Find |
|----------|-------------|---------------|
| `VITE_SUPABASE_URL` | Your Supabase project URL | Supabase → Settings → API |
| `VITE_SUPABASE_ANON_KEY` | Supabase anonymous key | Supabase → Settings → API |

Optional (for advanced features):
| Variable | Description |
|----------|-------------|
| `VITE_SUPABASE_SERVICE_ROLE_KEY` | For admin operations (use with caution) |

### How to Update Environment Variables

1. **Via Dashboard**
   - Project → **Settings** → **Environment Variables**
   - Edit or add variables
   - Redeploy for changes to take effect

2. **Via CLI**
   ```bash
   vercel env add VARIABLE_NAME
   vercel env rm VARIABLE_NAME
   vercel env ls
   ```

## Performance Optimizations

Your site is already optimized with:

✅ **Code Splitting**: Separate chunks for vendor, supabase, animations, and icons  
✅ **Minification**: Production builds are minified with Terser  
✅ **Tree Shaking**: Unused code is automatically removed  
✅ **Asset Caching**: Static assets cached for 1 year  
✅ **Compression**: Vercel automatically serves brotli/gzip  
✅ **CDN**: Content served from edge locations worldwide  

### Vercel Analytics (Optional)

Enable Vercel Analytics for insights:

1. Go to your project dashboard
2. Click **"Analytics"**
3. Enable **Web Analytics**
4. View real-time visitor data, page views, and performance metrics

## Updating Your Site

### Option 1: Git Push (Automatic)
```bash
# Make your changes
git add .
git commit -m "Update content"
git push origin main

# Vercel automatically deploys!
```

### Option 2: Manual Deploy via CLI
```bash
vercel --prod
```

## Troubleshooting

### Issue: Blank Page After Deployment

**Solution**:
1. Check browser console for errors
2. Verify environment variables are set in Vercel
3. Check build logs in Vercel dashboard
4. Ensure `vercel.json` is properly configured

### Issue: 404 Errors on Direct Page Access

**Solution**: The `vercel.json` file handles SPA routing. If you see 404s:
1. Verify `vercel.json` exists in your root directory
2. Check that the rewrite rules are correct
3. Redeploy the project

### Issue: Environment Variables Not Working

**Solution**:
1. Variables must start with `VITE_` to be exposed to the client
2. After adding/updating variables, you must redeploy
3. Check that variables are added to the correct environment (Production/Preview)

### Issue: Supabase Connection Errors

**Solution**:
1. Verify Supabase URL and key are correct
2. Check Supabase project is active
3. Ensure RLS policies allow anonymous access for public operations
4. Check browser console for specific error messages

### Issue: Build Fails

**Solution**:
1. Check build logs in Vercel dashboard
2. Ensure all dependencies are in `package.json`
3. Test build locally: `npm run build`
4. Verify Node.js version compatibility

## Security Best Practices

✅ **Environment Variables**: Never commit `.env` files  
✅ **HTTPS**: Automatically enabled by Vercel  
✅ **Security Headers**: Configured in `vercel.json`  
✅ **RLS Policies**: Enabled in Supabase for data security  
✅ **Admin Auth**: Use Supabase Auth for production admin access  

## Vercel Features You Can Use

- **Edge Functions**: Add serverless API routes
- **Image Optimization**: Automatic image optimization
- **Web Analytics**: Privacy-friendly analytics
- **Preview Deployments**: Test changes before going live
- **Instant Rollbacks**: One-click rollback to previous versions
- **Custom Headers**: Already configured for security
- **Redirects & Rewrites**: Configured for SPA routing

## Monitoring & Maintenance

### Check Deployment Status
```bash
vercel ls
```

### View Logs
```bash
vercel logs [deployment-url]
```

### Inspect Latest Deployment
```bash
vercel inspect
```

## Cost

Vercel's **Hobby Plan** (Free) includes:
- Unlimited deployments
- Automatic HTTPS
- 100GB bandwidth/month
- Serverless function executions
- Preview deployments
- Built-in CI/CD

This is perfect for personal websites!

## Next Steps

1. ✅ Deploy your site
2. ✅ Test all functionality
3. ✅ Add custom domain (optional)
4. ✅ Enable Vercel Analytics
5. ✅ Set up Supabase Row Level Security
6. ✅ Replace demo admin credentials with Supabase Auth
7. ✅ Monitor your site's performance

## Support

- [Vercel Documentation](https://vercel.com/docs)
- [Vercel Community](https://github.com/vercel/vercel/discussions)
- [Supabase Documentation](https://supabase.com/docs)

---

🎉 **Your website is now optimized for Vercel deployment!**

Any questions? Check the Vercel docs or open an issue in your repository.
