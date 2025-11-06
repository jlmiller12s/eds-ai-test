# Volkswagen Website - Adobe Edge Delivery Services

A modern, high-performance website built with Adobe Edge Delivery Services (AEM.live) featuring the Volkswagen brand design and Universal Editor integration.

## 🚀 Features

- **Lightning Fast**: Edge-optimized delivery with instant page loads
- **Universal Editor**: User-friendly content editing with real-time preview
- **Responsive Design**: Beautiful on all devices, from mobile to desktop
- **Modern Architecture**: Framework-free, semantic HTML and vanilla JavaScript
- **SEO Optimized**: Built-in performance and accessibility features
- **Volkswagen Design**: Matches the official VW design language

## 📋 Prerequisites

- Node.js 18 or newer
- Git
- npm or yarn

## 🛠️ Installation

### 1. Install AEM CLI

```bash
npm install -g @adobe/aem-cli
```

### 2. Clone this repository

```bash
git clone <your-repo-url>
cd EDS-AI-test
```

### 3. Start local development server

```bash
aem up
```

Your site will be available at `http://localhost:3000`

## 📁 Project Structure

```
├── blocks/              # Reusable content blocks
│   ├── header/         # Navigation header
│   ├── hero/           # Hero sections
│   ├── cards/          # Card grids
│   ├── columns/        # Column layouts
│   └── footer/         # Footer component
├── scripts/            # JavaScript functionality
│   ├── aem.js         # AEM core library
│   └── scripts.js     # Custom scripts
├── styles/             # CSS styling
│   └── styles.css     # Main stylesheet
├── tools/              # Authoring tools
│   └── sidekick/      # Sidekick configuration
├── fstab.yaml         # Content source configuration
├── head.html          # Common head elements
├── index.html         # Homepage
├── nav.html           # Navigation content
└── footer.html        # Footer content
```

## 🎨 Available Blocks

### Hero Block
Large hero sections with background images, headlines, and CTAs.

```html
<div class="hero">
  <div>
    <div><picture>...</picture></div>
    <div>
      <h1>Your Headline</h1>
      <p>Your description</p>
      <p><a href="/link" class="button">CTA Button</a></p>
    </div>
  </div>
</div>
```

### Cards Block
Grid of content cards with images and text.

```html
<div class="cards">
  <div>
    <div><picture>...</picture></div>
    <div>
      <h3>Card Title</h3>
      <p>Card description</p>
      <p><a href="/link" class="button">Learn More</a></p>
    </div>
  </div>
  <!-- More cards... -->
</div>
```

### Columns Block
Multi-column layouts for content organization.

```html
<div class="columns">
  <div>
    <div>
      <picture>...</picture>
      <h3>Column Title</h3>
      <p>Column content</p>
    </div>
    <!-- More columns... -->
  </div>
</div>
```

## ✏️ Content Authoring

### Using Google Docs / Microsoft Word

1. Create your content in Google Docs or Microsoft Word
2. Use the AEM Sidekick browser extension to preview and publish
3. Content is automatically converted to HTML

### Using the Universal Editor

1. Navigate to your page with `?ref=<branch>&repo=<repo>&owner=<owner>` query parameters
2. The Universal Editor will load automatically
3. Edit content directly on the page
4. Click "Publish" to make changes live

### Document-Based Authoring Guidelines

- **Headings**: Use H1 for page title, H2-H6 for sections
- **Images**: Insert images directly, they'll be optimized automatically
- **Links**: Use regular hyperlinks
- **Buttons**: Add a link and it will be styled as a button in the appropriate context
- **Sections**: Use horizontal rules (---) to separate sections
- **Blocks**: Use tables with specific formats to create blocks

## 🎯 Customization

### Colors

Edit `styles/styles.css` to change the color scheme:

```css
:root {
  --primary-blue: #001e50;
  --vw-blue: #00b1eb;
  --text-color: #1a1a1a;
  --background-light: #fafafa;
}
```

### Typography

Fonts are defined in the CSS variables:

```css
:root {
  --body-font-family: -apple-system, blinkmacsystemfont, 'Segoe UI', ...;
  --heading-font-family: var(--body-font-family);
}
```

### Adding New Blocks

1. Create a new folder in `/blocks/` with your block name
2. Add `blockname.js` and `blockname.css`
3. The block will be automatically loaded when used in content

Example block structure:

```javascript
export default function decorate(block) {
  // Your block decoration logic
}
```

## 🚢 Deployment

### Prerequisites

1. GitHub repository connected to Adobe Edge Delivery
2. Install the [AEM GitHub bot](https://github.com/apps/helix-bot)

### Publishing Process

1. **Preview**: Push to any branch to see preview at `https://<branch>--<repo>--<owner>.hlx.page`
2. **Production**: Merge to `main` branch to publish at `https://<repo>--<owner>.hlx.live`
3. **Custom Domain**: Configure your own domain in the AEM admin panel

### Environment URLs

- **Preview**: `https://main--<repo>--<owner>.hlx.page`
- **Live**: `https://<repo>--<owner>.hlx.live`
- **Production**: `https://your-domain.com`

## 🔧 Development Tools

### AEM CLI Commands

```bash
# Start local development server
aem up

# Check page status
aem status <url>

# Preview content
aem preview <url>

# Publish content
aem live <url>
```

### Debugging

Enable debug mode by adding `?rum=on` to any URL to see detailed performance metrics.

### Browser Extension

Install the [AEM Sidekick](https://chrome.google.com/webstore/detail/aem-sidekick/igkmdomcgoebiipaifhmpfjhbjccggml) for:
- One-click preview and publish
- Content management
- Performance monitoring

## 📚 Resources

- [AEM Edge Delivery Documentation](https://www.aem.live/docs/)
- [AEM Developer Tutorial](https://www.aem.live/developer/tutorial)
- [Block Collection](https://www.aem.live/developer/block-collection)
- [AEM.live Homepage](https://www.aem.live/)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'Add amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

## 📄 License

Copyright © 2025 Volkswagen. All rights reserved.

## 🆘 Support

For issues and questions:
- Check the [AEM Documentation](https://www.aem.live/docs/)
- Open an issue in this repository
- Contact the development team

---

**Built with ❤️ using Adobe Edge Delivery Services**

