# Quick Setup Guide - Volkswagen AEM Website

Follow these steps to get your Volkswagen-style website running with Adobe Edge Delivery Services.

## 📋 Prerequisites

- [ ] Node.js 18 or newer
- [ ] Git installed
- [ ] GitHub account
- [ ] Google Drive or SharePoint account
- [ ] Text editor or IDE (VS Code recommended)

## 🚀 Quick Start (5 minutes)

### Step 1: Install AEM CLI

Open your terminal and run:

```bash
npm install -g @adobe/aem-cli
```

Verify installation:

```bash
aem --version
```

### Step 2: Clone & Setup

```bash
# Clone this repository
git clone <your-repo-url>
cd EDS-AI-test

# Install dependencies
npm install

# Start local development server
aem up
```

Your site is now running at **http://localhost:3000** 🎉

### Step 3: View the Website

Open your browser and navigate to:
- Homepage: http://localhost:3000
- Any changes you make to files will auto-reload

## 🎨 Customizing Your Site

### Change Colors

Edit `styles/styles.css`:

```css
:root {
  --primary-blue: #001e50;    /* Main brand color */
  --vw-blue: #00b1eb;         /* Accent color */
  --text-color: #1a1a1a;      /* Text color */
}
```

### Add Your Logo

Replace `icons/vw-logo.svg` with your own logo SVG file.

### Update Content

Edit `index.html` to change homepage content, or see the Universal Editor guide for document-based authoring.

## 🌐 Content Source Setup

### Option A: Google Drive (Recommended)

1. **Create a folder** in Google Drive for your content
2. **Share it** with `helix@adobe.com` (Editor permissions)
3. **Get the folder URL** (right-click folder > Get link)
4. **Update `fstab.yaml`**:

```yaml
mountpoints:
  /: https://drive.google.com/drive/folders/YOUR_FOLDER_ID
```

### Option B: SharePoint

1. **Create a SharePoint folder** for your content
2. **Configure permissions** (see detailed SharePoint guide)
3. **Update `fstab.yaml`**:

```yaml
mountpoints:
  /: https://yourorg.sharepoint.com/sites/yoursite/Shared%20Documents/website
```

## 🔧 GitHub Setup

### 1. Create GitHub Repository

```bash
# Initialize git (if not already done)
git init

# Add remote
git remote add origin https://github.com/yourusername/your-repo.git

# Push code
git add .
git commit -m "Initial commit"
git push -u origin main
```

### 2. Install AEM GitHub Bot

1. Visit https://github.com/apps/helix-bot
2. Click "Install"
3. Select your repository
4. Authorize the app

### 3. Configure Project

1. Go to https://admin.hlx.page
2. Log in with GitHub
3. Add your project
4. Configure domain (optional)

## 🌍 Your Site URLs

After GitHub setup, your site will be available at:

- **Preview**: `https://main--<repo>--<owner>.hlx.page`
- **Production**: `https://<repo>--<owner>.hlx.live`

Replace `<repo>` and `<owner>` with your GitHub repository name and username.

## 🛠️ Essential Commands

```bash
# Start local server
aem up

# Preview a page
aem preview <url>

# Publish a page
aem live <url>

# Check page status
aem status <url>
```

## 📦 Browser Extension Setup

### Install AEM Sidekick

1. Visit [Chrome Web Store](https://chrome.google.com/webstore/detail/aem-sidekick/igkmdomcgoebiipaifhmpfjhbjccggml)
2. Click "Add to Chrome"
3. Pin the extension to your toolbar

### Using Sidekick

1. **Configure**: Click Sidekick icon > Settings
2. **Add Project**: Enter your project details
3. **Preview**: Open a document and click "Preview"
4. **Publish**: Click "Publish" to make changes live

## 📝 Creating Your First Page

### Using HTML (Direct Editing)

Create a new file `about.html`:

```html
<!DOCTYPE html>
<html>
<head>
  <title>About Us - Volkswagen</title>
  <meta name="description" content="Learn about Volkswagen">
</head>
<body>
  <header></header>
  <main>
    <div>
      <h1>About Volkswagen</h1>
      <p>Your content here...</p>
    </div>
  </main>
  <footer></footer>
</body>
</html>
```

### Using Google Docs (Document Authoring)

1. Create a new Google Doc in your content folder
2. Name it `about-us`
3. Add content:

```
# About Volkswagen

Welcome to our company page...

## Our Mission

We are committed to...
```

4. Click Sidekick > Preview
5. Click Publish when ready

## 🎯 Adding Blocks

### Hero Block

In your document:

```
| Hero |
|------|
| ![Hero Image](./media/hero.jpg) |
| # Welcome Title |
| Description text |
| [Call to Action](/link) |
```

### Cards Block

```
| Cards |
|-------|
| ![Image 1](./media/card1.jpg) |
| ### Card Title |
| Card description |
| [Learn More](/link) |
| --- |
| ![Image 2](./media/card2.jpg) |
| ### Card Title 2 |
| Card description 2 |
| [Learn More](/link2) |
```

## 🚀 Going Live

### 1. Test Everything

- [ ] Preview all pages
- [ ] Check on mobile devices
- [ ] Test all links
- [ ] Verify images load
- [ ] Check performance (Lighthouse)

### 2. Publish to Production

```bash
# Publish all pages
aem live

# Or publish specific page
aem live /about-us
```

### 3. Configure Custom Domain (Optional)

1. Go to https://admin.hlx.page
2. Select your project
3. Add custom domain
4. Update DNS records
5. Enable HTTPS

## 🔍 Troubleshooting

### Local Server Won't Start

```bash
# Kill any process using port 3000
npx kill-port 3000

# Try starting again
aem up
```

### Changes Not Appearing

1. Hard refresh browser (Ctrl+Shift+R / Cmd+Shift+R)
2. Clear browser cache
3. Check if file was saved
4. Restart `aem up`

### Images Not Loading

1. Check file path is correct
2. Verify image file exists
3. Check image file permissions
4. Use relative paths (./media/image.jpg)

### Blocks Not Rendering

1. Verify block name matches folder name
2. Check table format in document
3. Look for console errors (F12)
4. Ensure block .js and .css files exist

## 📚 Next Steps

1. **Read the documentation**: Check out [README.md](./README.md)
2. **Configure Universal Editor**: See [UNIVERSAL-EDITOR-SETUP.md](./UNIVERSAL-EDITOR-SETUP.md)
3. **Customize blocks**: Explore `/blocks/` directory
4. **Add more pages**: Create new HTML files or documents
5. **Optimize performance**: Follow AEM best practices

## 🆘 Need Help?

- 📖 [AEM Documentation](https://www.aem.live/docs/)
- 💬 [Community Forum](https://experienceleaguecommunities.adobe.com/)
- 🎥 [Video Tutorials](https://www.youtube.com/@AdobeExperienceManager)
- 📧 Contact your development team

## ✅ Checklist

Before launching:

- [ ] All pages reviewed and tested
- [ ] Mobile responsiveness verified
- [ ] SEO metadata added to all pages
- [ ] Images optimized and have alt text
- [ ] Links tested and working
- [ ] Performance score > 90 (Lighthouse)
- [ ] Accessibility score > 90 (Lighthouse)
- [ ] Browser testing complete (Chrome, Firefox, Safari)
- [ ] Content reviewed by stakeholders
- [ ] Backup of all content created

---

**Congratulations! 🎉** Your Volkswagen-style website is ready to go live!

For detailed information, see the full [README.md](./README.md).

