# Dreamory Website

A static Single Page Application (SPA) for the Dreamory personal experience database app. Built with vanilla HTML, CSS, and JavaScript for optimal performance and S3 hosting compatibility.

## 🌟 Features

- **Fully Responsive Design** - Works perfectly on all devices
- **Single Page Application** - Client-side routing for smooth navigation
- **Component-Based Architecture** - Reusable components for maintainability
- **Optimized for S3** - Static hosting ready with proper error handling
- **SEO Friendly** - Proper meta tags and semantic HTML
- **Privacy-First** - Comprehensive privacy policy and terms of service

## 📁 Project Structure

```
website/
├── index.html              # Main SPA entry point
├── error.html              # 404 error page for S3
├── pages/                  # Individual page content
│   ├── home.html
│   ├── features.html
│   ├── how-it-works.html
│   ├── download.html
│   ├── about.html
│   ├── privacy.html
│   └── terms.html
├── components/             # Reusable components
│   └── footer.html
├── deploy-s3.sh           # S3 deployment script
├── .s3-website.json       # S3 website configuration
└── README.md              # This file
```

## 🚀 Local Development

1. **Serve the website locally** using any static file server:

   ```bash
   # Using Python (Python 3)
   cd website
   python -m http.server 8000

   # Using Python (Python 2)
   python -m SimpleHTTPServer 8000

   # Using Node.js (if you have live-server installed)
   npx live-server

   # Using PHP
   php -S localhost:8000
   ```

2. **Open your browser** to `http://localhost:8000`

## 🏠 Pages

### Main Pages
- **Home** (`/`) - Hero section with app overview and testimonials
- **Features** (`/features`) - Detailed feature list and roadmap
- **How It Works** (`/how-it-works`) - Step-by-step guide with interactive demo
- **Download** (`/download`) - App download links and system requirements
- **About** (`/about`) - Company story, team, and contact information

### Legal Pages
- **Privacy Policy** (`/privacy`) - Comprehensive privacy protection details
- **Terms of Service** (`/terms`) - Clear, fair terms of use

## ☁️ S3 Deployment

### Prerequisites

1. **AWS CLI installed and configured**:
   ```bash
   aws configure
   ```

2. **S3 bucket created**:
   ```bash
   aws s3 mb s3://your-bucket-name
   ```

### Quick Deploy

```bash
./deploy-s3.sh your-bucket-name your-aws-profile
```

### Manual Deployment

1. **Upload files**:
   ```bash
   aws s3 sync . s3://your-bucket-name --delete
   ```

2. **Enable static website hosting**:
   ```bash
   aws s3 website s3://your-bucket-name \
     --index-document index.html \
     --error-document error.html
   ```

3. **Set public read policy**:
   ```bash
   aws s3api put-bucket-policy --bucket your-bucket-name --policy '{
     "Version": "2012-10-17",
     "Statement": [{
       "Sid": "PublicReadGetObject",
       "Effect": "Allow",
       "Principal": "*",
       "Action": "s3:GetObject",
       "Resource": "arn:aws:s3:::your-bucket-name/*"
     }]
   }'
   ```

## 🔧 Architecture

### Client-Side Routing
- Custom lightweight router handling all navigation
- History API for proper back/forward button support
- Automatic 404 handling with redirect to home

### Component System
- Page-based components loaded dynamically
- Shared footer component across all pages
- Inline CSS for optimal performance (no external stylesheets)

### Performance Optimizations
- Minimal JavaScript bundle
- Inline CSS to prevent FOUC (Flash of Unstyled Content)
- Lazy loading of page content
- Proper caching headers in S3 deployment

## 🎨 Theming

The site uses CSS custom properties for consistent theming:

```css
:root {
  --primary: #667eea;
  --secondary: #764ba2;
  --accent: #ff6b6b;
  --accent-secondary: #feca57;
  --text-dark: #2d3748;
  --text-light: #718096;
  --bg-light: #f7fafc;
  --white: #ffffff;
}
```

## 📱 Mobile-First Design

- Responsive breakpoints at 768px and 1024px
- Touch-friendly navigation and interactions
- Optimized images and content for mobile devices
- Progressive enhancement approach

## 🔍 SEO Considerations

- Semantic HTML structure
- Proper heading hierarchy (H1, H2, H3)
- Meta descriptions and titles
- Open Graph tags for social media sharing
- Structured data markup

## 🚧 Future Enhancements

- [ ] Service Worker for offline capability
- [ ] Image optimization and lazy loading
- [ ] CSS/JS minification for production
- [ ] CloudFront CDN setup
- [ ] Custom domain configuration
- [ ] Analytics integration
- [ ] A/B testing framework

## 📞 Support

For questions about the website or deployment:
- Email: hello@webjackl.com
- Technical Issues: hello@webjackl.com

## 📄 License

Copyright © 2024 Dreamory. All rights reserved.