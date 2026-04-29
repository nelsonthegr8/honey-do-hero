# Honey-Do Hero LLC - Professional Handyman Website

A modern, responsive website for Honey-Do Hero LLC, a handyman service based in McDonough, GA.

## 📁 Files Included

- `index.html` - Main HTML file with all sections
- `styles.css` - Complete styling with responsive design
- `script.js` - Interactive features and animations
- `README.md` - This file

## 🚀 Quick Start

### Option 1: Serve Locally (for preview)

```bash
# Using Python 3
python3 -m http.server 8000

# Using Node.js (if installed)
npx serve .

# Using PHP
php -S localhost:8000
```

Then open `http://localhost:8000` in your browser.

### Option 2: Deploy to Nginx (for your Proxmox container)

1. Copy files to nginx document root:
```bash
sudo cp -r honey-do-hero/* /var/www/honeydo-hero/
```

2. Create nginx config (e.g., `/etc/nginx/sites-available/honeydo-hero`):
```nginx
server {
    listen 80;
    server_name handyman.yourdomain.com;
    
    root /var/www/honeydo-hero;
    index index.html;
    
    location / {
        try_files $uri $uri/ =404;
    }
}
```

3. Enable and restart:
```bash
sudo ln -s /etc/nginx/sites-available/honeydo-hero /etc/nginx/sites-enabled/
sudo nginx -t && sudo systemctl reload nginx
```

## 🎨 Customization Guide

### 1. Add Your Logo

Replace the icon in the navbar (around line 17 in index.html):
```html
<!-- Current -->
<div class="nav-brand">
    <i class="fas fa-hammer"></i>
    <span>Honey-Do Hero</span>
</div>

<!-- With logo -->
<div class="nav-brand">
    <img src="logo.png" alt="Honey-Do Hero Logo" style="height: 40px;">
    <span>Honey-Do Hero</span>
</div>
```

### 2. Add Project Photos

Replace placeholder project images in the Projects section (around line 220):

```html
<!-- Current placeholder -->
<div class="project-image placeholder">
    <i class="fas fa-image"></i>
    <span>Before & After</span>
</div>

<!-- Replace with actual photo -->
<div class="project-image">
    <img src="projects/room-makeover.jpg" alt="Room Makeover Project">
</div>
```

Create a `projects/` folder and add your photos there.

### 3. Add Real Customer Reviews

Replace the placeholder reviews in the Reviews section (around line 260):

```html
<!-- Replace placeholder with actual review -->
<div class="review-card">
    <div class="review-stars">
        <i class="fas fa-star"></i>
        <i class="fas fa-star"></i>
        <i class="fas fa-star"></i>
        <i class="fas fa-star"></i>
        <i class="fas fa-star"></i>
    </div>
    <p class="review-text">"Actual customer review text here..."</p>
    <div class="review-author">
        <div class="author-avatar">JD</div>
        <span>John Doe</span>
    </div>
</div>
```

### 4. Update Color Scheme

Edit CSS variables in `styles.css` (lines 6-28):

```css
:root {
    --primary-color: #FF6B35;      /* Main orange color */
    --primary-dark: #E55A2B;       /* Darker shade */
    --secondary-color: #2C3E50;    /* Dark blue-gray */
    /* ... */
}
```

### 5. Add Social Media Links

Update footer social links (around line 360):

```html
<div class="footer-social">
    <a href="https://facebook.com/yourpage" aria-label="Facebook"><i class="fab fa-facebook"></i></a>
    <a href="https://instagram.com/yourpage" aria-label="Instagram"><i class="fab fa-instagram"></i></a>
</div>
```

### 6. Set Up Contact Form Backend

The form currently opens the user's email client. For a real backend:

**Option A: Use Formspree (easiest)**
```html
<form action="https://formspree.io/f/your-form-id" method="POST">
```

**Option B: Use Netlify Forms**
Add `netlify` attribute to the form tag.

**Option C: Build PHP handler**
Create `submit.php`:
```php
<?php
$name = $_POST['name'];
$email = $_POST['email'];
$service = $_POST['service'];
$message = $_POST['message'];

$to = 'honeydoherohenrycounty@gmail.com';
$subject = "New Estimate Request - $service";
$body = "Name: $name\nEmail: $email\n\n$message";

mail($to, $subject, $body);
header('Location: ?success=1');
?>
```

Then update form action: `<form action="submit.php" method="POST">`

## 📱 Mobile Responsive

The website is fully responsive and tested on:
- Desktop (1920px+)
- Laptop (1366px - 1920px)
- Tablet (768px - 1024px)
- Mobile (320px - 768px)

## 🎯 SEO Optimization

### Add Meta Tags

Already included in `index.html`:
- Meta description
- Viewport for mobile
- Open Graph tags (add your own)

### Add to Google My Business

1. Claim your business listing
2. Add website URL
3. Upload project photos
4. Encourage customer reviews

### Add Schema Markup

Add this to `<head>` for local business SEO:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "HomeAndConstructionBusiness",
  "name": "Honey-Do Hero LLC",
  "image": "https://yourdomain.com/logo.png",
  "email": "honeydoherohenrycounty@gmail.com",
  "address": {
    "@type": "PostalAddress",
    "addressLocality": "McDonough",
    "addressRegion": "GA",
    "addressCountry": "US"
  },
  "priceRange": "$$",
  "openingHoursSpecification": {
    "@type": "OpeningHoursSpecification",
    "dayOfWeek": ["Saturday", "Sunday"],
    "opens": "08:00",
    "closes": "18:00"
  }
}
</script>
```

## 🔒 SSL Certificate (Let's Encrypt)

```bash
sudo apt install certbot python3-certbot-nginx
sudo certbot --nginx -d handyman.yourdomain.com
```

## 📊 Analytics

### Add Google Analytics

Add this to `<head>` after the title tag:

```html
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_MEASUREMENT_ID');
</script>
```

## 🛠️ Maintenance

### Update Services

Edit the Services section in `index.html` (lines 100-170). Add/remove service cards as needed.

### Add New Projects

1. Add photos to `projects/` folder
2. Copy a `.project-card` div and update content
3. Replace placeholder images with real photos

### Update Reviews

As you get customer permission, replace placeholder reviews with real testimonials.

## 📞 Contact Information

Current contact info in the website:
- **Email:** honeydoherohenrycounty@gmail.com
- **Service Area:** McDonough, GA and Henry County
- **Availability:** Weekend work (currently)

## 🎨 Color Palette

- **Primary:** #FF6B35 (Orange)
- **Secondary:** #2C3E50 (Dark Blue)
- **Accent:** #F4A261 (Light Orange)
- **Background:** #FFFFFF (White)
- **Text:** #2C3E50 (Dark)

## 📄 License

This website template is provided as-is for Honey-Do Hero LLC use.

---

**Built with ❤️ for Honey-Do Hero LLC**

For questions or updates, contact: honeydoherohenrycounty@gmail.com
