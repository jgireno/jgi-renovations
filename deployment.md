# Deployment Guide for JGI Renovations Website

This guide will help you deploy your JGI Renovations website to various hosting platforms.

## GitHub Pages Deployment (Recommended - FREE)

### Step 1: Create GitHub Repository
1. Go to [GitHub.com](https://github.com) and sign in
2. Click the "+" icon → "New repository"
3. Name it `jgi-renovations` (or your preferred name)
4. Make it **Public** for free GitHub Pages
5. Check "Add a README file"
6. Click "Create repository"

### Step 2: Upload Website Files
**Option A: Using GitHub Web Interface**
1. Click "uploading an existing file"
2. Drag and drop your `index.html` file
3. Add commit message: "Initial website upload"
4. Click "Commit changes"

**Option B: Using Git Commands**
```bash
# Clone your new repository
git clone https://github.com/jgireno/jgi-renovations.git
cd jgi-renovations

# Add your files
cp /path/to/your/index.html .
cp /path/to/your/README.md .
cp /path/to/your/LICENSE .
cp /path/to/your/.gitignore .

# Commit and push
git add .
git commit -m "Initial website upload"
git push origin main
```

### Step 3: Enable GitHub Pages
1. Go to your repository → **Settings** tab
2. Scroll down to **Pages** section (left sidebar)
3. Under "Source", select **"Deploy from a branch"**
4. Choose **main** branch
5. Select **/ (root)** folder
6. Click **Save**
7. Wait 2-5 minutes for deployment

Your site will be live at: `https://jgirno.github.io/jgi-renovations`

## Custom Domain Setup (Optional)

### Step 1: Purchase a Domain
- Recommended: Namecheap, Google Domains, or GoDaddy
- Suggested domains: `jgirenovations.com`, `jgibrampton.com`

### Step 2: Configure GitHub Pages
1. In your repository settings → Pages
2. Enter your domain in "Custom domain" field
3. Check "Enforce HTTPS"
4. Add a `CNAME` file to your repository:
   ```
   www.yourdomain.com
   ```

### Step 3: Configure DNS
Add these DNS records with your domain provider:

```
Type    Name    Value
CNAME   www     jgireno.github.io
A       @       185.199.108.153
A       @       185.199.109.153
A       @       185.199.110.153
A       @       185.199.111.153
```

## Alternative Hosting Options

### Netlify (FREE with great features)
1. Go to [Netlify.com](https://netlify.com)
2. Sign up with GitHub account
3. Click "Add new site" → "Import an existing project"
4. Choose GitHub → Select your repository
5. Deploy settings:
   - Branch: `main`
   - Build command: (leave empty)
   - Publish directory: (leave empty)
6. Click "Deploy site"

**Benefits:**
- Free custom domain
- Automatic SSL certificates
- Form handling
- Continuous deployment

### Vercel (FREE for personal projects)
1. Go to [Vercel.com](https://vercel.com)
2. Sign up with GitHub
3. Click "New Project"
4. Import your GitHub repository
5. Click "Deploy"

**Benefits:**
- Excellent performance
- Global CDN
- Easy custom domain setup

### Traditional Web Hosting
For shared hosting (GoDaddy, Bluehost, etc.):
1. Download all files from GitHub
2. Upload via FTP to your hosting provider
3. Place files in the `public_html` or `www` folder

## Adding Real Images

### Step 1: Optimize Images
Before uploading, optimize your images:
- **File formats**: Use WebP or JPEG for photos, PNG for graphics
- **Size**: Resize to maximum 1920px width for desktop
- **Compression**: Use tools like TinyPNG or ImageOptim
- **File size**: Keep under 500KB per image

### Step 2: Create Image Structure
```
images/
├── gallery/
│   ├── kitchen-remodel-1.jpg
│   ├── kitchen-remodel-2.jpg
│   ├── bathroom-renovation-1.jpg
│   ├── basement-apartment-1.jpg
│   └── exterior-deck-1.jpg
├── logo/
│   ├── jgi-logo.svg
│   └── jgi-logo-white.svg
└── blog/
    ├── smart-home-2025.jpg
    ├── color-trends-2025.jpg
    └── roi-renovations.jpg
```

### Step 3: Update HTML
Replace placeholder gallery items:
```html
<!-- Before -->
<div class="gallery-item">
    <div>🏠 Modern Kitchen Remodel</div>
</div>

<!-- After -->
<div class="gallery-item">
    <img src="images/gallery/kitchen-remodel-1.jpg" 
         alt="Modern kitchen remodel with white cabinets and quartz countertops"
         loading="lazy">
    <div class="gallery-overlay">
        <h4>Modern Kitchen Remodel</h4>
        <p>Complete kitchen transformation</p>
    </div>
</div>
```

## SEO Optimization

### Google Search Console
1. Go to [Google Search Console](https://search.google.com/search-console)
2. Add your website property
3. Verify ownership via HTML file upload
4. Submit your sitemap (create using online generators)

### Local SEO for Brampton
Add this structured data to your HTML head:
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "JGI Renovations & Remodeling",
  "telephone": ["647-303-5159", "647-991-4413"],
  "email": "jgireno5159@gmail.com",
  "address": {
    "@type": "PostalAddress",
    "addressLocality": "Brampton",
    "addressRegion": "Ontario",
    "addressCountry": "Canada"
  },
  "areaServed": ["Brampton", "Mississauga", "Toronto", "GTA"],
  "serviceType": ["Home Renovation", "Kitchen Remodeling", "Bathroom Renovation"]
}
</script>
```

## Analytics Setup

### Google Analytics 4
1. Go to [Google Analytics](https://analytics.google.com)
2. Create new property
3. Add tracking code before closing `</head>` tag:
```html
<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_MEASUREMENT_ID');
</script>
```

## Security & Performance

### Security Headers
If using Netlify, add `_headers` file:
```
/*
  X-Frame-Options: DENY
  X-Content-Type-Options: nosniff
  Referrer-Policy: strict-origin-when-cross-origin
  Content-Security-Policy: default-src 'self'; style-src 'self' 'unsafe-inline'
```

### Performance Optimization
1. **Enable Gzip compression** (automatic on most platforms)
2. **Use a CDN** (automatic with Netlify/Vercel)
3. **Optimize images** with proper sizing and formats
4. **Minimize CSS/JS** for production

## Contact Form Setup

### Netlify Forms (Recommended)
Add to your form tag:
```html
<form name="quote-request" method="POST" data-netlify="true">
```

### Alternative: Formspree
1. Go to [Formspree.io](https://formspree.io)
2. Create form endpoint
3. Update form action:
```html
<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
```

## Continuous Deployment

Once set up, your workflow will be:
1. Make changes to your files locally
2. Commit and push to GitHub
3. Your site automatically updates!

```bash
# Make changes to index.html
git add .
git commit -m "Updated services section"
git push origin main
# Site automatically deploys!
```

## Pro Tips

1. **Test on multiple devices** before going live
2. **Use browser dev tools** to test mobile responsiveness
3. **Check loading speed** with Google PageSpeed Insights
4. **Regular backups** of your code and content
5. **Monitor site performance** with analytics
6. **Keep content updated** regularly for better SEO

## Troubleshooting

### Common Issues:

**Site not loading after deployment:**
- Wait 5-10 minutes for DNS propagation
- Check GitHub Pages settings
- Ensure `index.html` is in root directory

**Images not displaying:**
- Check file paths are correct
- Ensure images are committed to repository
- Verify image file names match HTML references

**Mobile layout issues:**
- Test with browser dev tools mobile view
- Check CSS media queries
- Validate HTML structure

**Form not working:**
- Verify form action URL
- Check form field names
- Test with simple form first

---

Need help? Contact us:
- Email: jgireno5159@gmail.com
- Phone: 647-303-5159

