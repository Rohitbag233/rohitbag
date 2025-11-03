# Vercel Deployment Checklist

Use this checklist to ensure a smooth deployment to Vercel.

## Pre-Deployment Checklist

### 1. Code Preparation
- [x] Base path changed from `/rohit-site/` to `/`
- [x] Router basename removed from App.jsx
- [x] Build optimization configured (code splitting, minification)
- [x] Console statements removal configured
- [x] CSS errors fixed (invalid Tailwind classes removed)
- [x] vercel.json created for SPA routing and headers

### 2. Environment Variables Ready
- [ ] `VITE_SUPABASE_URL` - Your Supabase project URL
- [ ] `VITE_SUPABASE_ANON_KEY` - Your Supabase anonymous key

**Get these from**: Supabase Dashboard → Settings → API

### 3. Git Repository
- [ ] Code committed to a Git repository (GitHub, GitLab, or Bitbucket)
- [ ] Branch pushed to remote

### 4. Supabase Database
- [ ] Database created on Supabase
- [ ] Schema applied (`supabase-schema.sql`)
- [ ] RLS policies enabled
- [ ] Tables verified in Table Editor

## Deployment Steps

### Quick Deploy (5 minutes)

1. **Push to Git** (if not already done)
   ```bash
   git add .
   git commit -m "Optimize for Vercel deployment"
   git push origin main
   ```

2. **Sign in to Vercel**
   - Visit [vercel.com](https://vercel.com)
   - Sign up/login with GitHub (recommended)

3. **Import Project**
   - Click "Add New Project"
   - Select your repository
   - Click "Import"

4. **Configure Build**
   - Framework Preset: **Vite** (auto-detected)
   - Build Command: `npm run build` (auto-detected)
   - Output Directory: `dist` (auto-detected)
   - Install Command: `npm install` (auto-detected)

5. **Add Environment Variables**
   ```
   VITE_SUPABASE_URL = your_url_here
   VITE_SUPABASE_ANON_KEY = your_key_here
   ```

6. **Deploy**
   - Click "Deploy"
   - Wait 60-90 seconds
   - Done! 🎉

## Post-Deployment Verification

### 1. Basic Functionality
- [ ] Homepage loads correctly
- [ ] All navigation links work
- [ ] Story page displays
- [ ] Projects page displays
- [ ] Advice Museum page displays and form works
- [ ] Contact page displays and form works

### 2. Admin Panel
- [ ] Admin login page accessible (`/admin/login`)
- [ ] Can login with credentials
- [ ] Dashboard loads
- [ ] Can manage content

### 3. Features
- [ ] Dark/light theme toggle works
- [ ] Accessibility mode works
- [ ] Mobile responsive design
- [ ] Animations work smoothly
- [ ] Forms submit to Supabase

### 4. Performance
- [ ] Page loads in <3 seconds
- [ ] No console errors in browser
- [ ] Assets load from CDN
- [ ] Images display correctly

### 5. SEO & Metadata
- [ ] Page title shows correctly
- [ ] Meta descriptions present
- [ ] Social media cards work (test with Twitter/Facebook)

## Troubleshooting Quick Fixes

### Problem: Blank Page
**Check:**
1. Browser console for errors
2. Environment variables are set in Vercel
3. Build logs in Vercel dashboard

**Fix:** Redeploy after verifying env vars

### Problem: 404 on Page Refresh
**Check:**
1. `vercel.json` exists in root
2. Rewrite rules are correct

**Fix:** Should be automatic with the provided `vercel.json`

### Problem: Supabase Connection Error
**Check:**
1. Environment variables are correct
2. Supabase project is active
3. RLS policies allow access

**Fix:** Verify credentials and RLS settings

### Problem: Forms Not Working
**Check:**
1. Supabase RLS policies
2. Network tab for failed requests
3. Console for error messages

**Fix:** Adjust RLS policies in Supabase

## Optional: Custom Domain

### If Using Custom Domain
1. **Add Domain in Vercel**
   - Project → Settings → Domains
   - Add your domain

2. **Configure DNS**
   - Add records shown by Vercel
   - Wait for DNS propagation (5-30 min)

3. **HTTPS**
   - Automatic (provisioned by Vercel)
   - Check the certificate status

## Performance Monitoring

### After 24 Hours
- [ ] Check Vercel Analytics (if enabled)
- [ ] Run Lighthouse audit
- [ ] Test on multiple devices
- [ ] Monitor error logs

### Optimization Opportunities
- [ ] Enable Vercel Analytics
- [ ] Add service worker for offline support
- [ ] Optimize images with Vercel Image Optimization
- [ ] Add prefetching for better navigation

## Continuous Deployment

Your site is now set up for **automatic deployments**:

- ✅ Every push to `main` → Production deployment
- ✅ Every pull request → Preview deployment
- ✅ Instant rollbacks available
- ✅ Build logs for debugging

## Support & Resources

- 📖 [VERCEL_DEPLOYMENT.md](VERCEL_DEPLOYMENT.md) - Full deployment guide
- 🚀 [QUICKSTART_VERCEL.md](QUICKSTART_VERCEL.md) - 5-minute quick start
- 📊 [OPTIMIZATION_SUMMARY.md](OPTIMIZATION_SUMMARY.md) - Performance details
- 🔧 [Vercel Documentation](https://vercel.com/docs)
- 💾 [Supabase Documentation](https://supabase.com/docs)

## Success Criteria

Your deployment is successful when:

✅ Site is live at your Vercel URL  
✅ All pages load without errors  
✅ Forms submit successfully  
✅ Admin panel is accessible  
✅ Responsive on mobile devices  
✅ No console errors  
✅ Build completes in <90 seconds  
✅ Page loads in <3 seconds  

---

## Final Notes

- Your bundle size is optimized (~167 KB gzipped)
- Code splitting is enabled for optimal caching
- Security headers are configured
- SPA routing is handled automatically
- HTTPS is automatic

**You're ready to deploy!** 🚀

For questions or issues, refer to the detailed guides or Vercel support.
