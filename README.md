# Rohit Bag - Personal Website

A modern, feature-rich personal website built with React, Vite, Tailwind CSS, and Supabase.

## Features

### Public Features
- ✅ **Responsive Design** - Mobile-first approach with beautiful UI
- ✅ **Dark/Light Theme** - Toggle with memory (localStorage)
- ✅ **Accessibility Mode** - Larger text, higher contrast, enhanced navigation
- ✅ **Life Story** - Complete journey from childhood to entrepreneurship
- ✅ **Projects Showcase** - Display of active and archived projects
- ✅ **Advice Museum** - Collective wall of wisdom from visitors
- ✅ **Contact Form** - With Supabase backend integration
- ✅ **Micro-animations** - Smooth reveal on scroll with Framer Motion
- ✅ **Mobile Shortcuts** - Quick actions bar for mobile users
- ✅ **SEO Optimized** - Meta tags, semantic HTML

### Admin Panel Features
- ✅ **Dashboard** - Overview of all content with statistics
- ✅ **Story Manager** - Add/edit/delete life story entries
- ✅ **Projects Manager** - Manage project portfolio
- ✅ **Advice Museum Manager** - Review and approve advice submissions
- ✅ **Contact Manager** - View and manage contact form submissions
- ✅ **Settings Manager** - Global site configuration
- ✅ **Secure Login** - Protected admin routes

## Tech Stack

- **Frontend**: React 18, Vite
- **Styling**: Tailwind CSS
- **Animations**: Framer Motion
- **Icons**: Lucide React
- **Routing**: React Router DOM
- **Backend**: Supabase (PostgreSQL)
- **Deployment**: Vercel (optimized), GitHub Pages compatible

## Setup Instructions

### 1. Clone and Install Dependencies

```bash
npm install
```

### 2. Set Up Supabase

1. Go to [Supabase](https://supabase.com) and create a new project
2. Copy the file `supabase-schema.sql` content
3. In your Supabase project, go to **SQL Editor**
4. Paste the entire SQL schema and click **Run**
5. This will create all necessary tables, indexes, and policies

### 3. Configure Environment Variables

The `.env` file is already configured with your Supabase credentials:

```env
VITE_SUPABASE_URL=https://icjahaocvwrvrsilpqwy.supabase.co
VITE_SUPABASE_ANON_KEY=your_anon_key
```

### 4. Development

Run the development server:

```bash
npm run dev
```

Open [http://localhost:5173](http://localhost:5173) in your browser.

### 5. Admin Panel Access

**Demo Credentials:**
- URL: `/admin/login`
- Email: `admin@rohit.dev`
- Password: `admin123`

For production, you should:
1. Implement proper Supabase Auth
2. Use Row Level Security policies
3. Store admin emails in the `admin_users` table

### 6. Deployment

#### Deploy to Vercel (Recommended)

This project is optimized for Vercel deployment:

```bash
# Install Vercel CLI
npm install -g vercel

# Deploy
vercel
```

Or use the Vercel Dashboard:
1. Push your code to GitHub
2. Import project on [vercel.com](https://vercel.com)
3. Add environment variables (`VITE_SUPABASE_URL`, `VITE_SUPABASE_ANON_KEY`)
4. Deploy!

**📖 See [VERCEL_DEPLOYMENT.md](VERCEL_DEPLOYMENT.md) for detailed instructions**

#### Alternative: GitHub Pages

If you prefer GitHub Pages, see [DEPLOYMENT_GUIDE.md](DEPLOYMENT_GUIDE.md)

## Project Structure

```
src/
├── components/
│   ├── admin/           # Admin panel components
│   ├── Footer.jsx
│   ├── Header.jsx
│   ├── Layout.jsx
│   ├── MobileShortcuts.jsx
│   └── ScrollToTop.jsx
├── contexts/
│   └── ThemeContext.jsx # Theme and accessibility state
├── hooks/
│   └── useScrollReveal.js # Scroll animation hook
├── lib/
│   └── supabase.js      # Supabase client
├── pages/
│   ├── Admin.jsx        # Admin panel layout
│   ├── AdminLogin.jsx   # Admin authentication
│   ├── AdviceMuseum.jsx
│   ├── Contact.jsx
│   ├── Home.jsx
│   ├── NotFound.jsx
│   ├── Projects.jsx
│   └── Story.jsx
├── App.jsx              # Main app with routing
├── index.css           # Global styles
└── main.jsx            # Entry point
```

## Database Schema

The complete schema is in `supabase-schema.sql` with:

- **life_story** - Life journey milestones
- **projects** - Portfolio projects
- **advice_museum** - Visitor advice submissions
- **contact_submissions** - Contact form entries
- **testimonials** - Client testimonials
- **admin_users** - Admin authentication
- **site_settings** - Global configuration
- **page_analytics** - Basic analytics

## Customization

### Update Personal Information

1. **Admin Panel**: Use the settings manager at `/admin/settings`
2. **Manual**: Update `src/pages/Home.jsx`, `src/pages/Story.jsx`
3. **Database**: Insert your data via Supabase dashboard or admin panel

### Change Theme Colors

Edit `tailwind.config.js`:

```js
colors: {
  primary: {
    // Your custom colors
  }
}
```

### GitHub Pages Base Path

Update `vite.config.js`:

```js
base: '/your-actual-repo-name/'
```

## Accessibility Features

- Skip to main content link
- ARIA labels on all interactive elements
- Keyboard navigation support
- High contrast mode
- Font size increase option
- Screen reader friendly

## Browser Support

- Chrome/Edge (last 2 versions)
- Firefox (last 2 versions)
- Safari (last 2 versions)
- Mobile browsers

## Contributing

This is a personal website, but feel free to:
- Report bugs
- Suggest features
- Fork for your own use

## License

MIT License - Feel free to use this template for your own website!

## Author

**Rohit Bag**
- Email: rohit@example.com
- LinkedIn: [linkedin.com/in/rohitbag](https://linkedin.com/in/rohitbag)
- Twitter: [@rohitbag](https://twitter.com/rohitbag)
- GitHub: [@rohitbag](https://github.com/rohitbag)

---

Built with ❤️ by Rohit Bag
