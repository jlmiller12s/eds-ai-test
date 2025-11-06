# Universal Editor Setup Guide

This guide explains how to configure and use the Universal Editor with your Adobe Edge Delivery Services website.

## What is the Universal Editor?

The Universal Editor is Adobe's next-generation content editing interface that allows you to:
- Edit content directly on the page with real-time preview
- Use a WYSIWYG interface without switching between authoring and preview
- Manage content using your existing tools (Google Docs, SharePoint)
- Collaborate with your team in real-time

## Prerequisites

1. Adobe Experience Manager as a Cloud Service account
2. Content source configured (Google Drive or SharePoint)
3. GitHub repository connected to AEM Edge Delivery
4. AEM Sidekick browser extension installed

## Configuration Steps

### 1. Content Source Setup

Your content source is already configured in `fstab.yaml`:

```yaml
mountpoints:
  /: https://drive.google.com/drive/folders/1MGzOt7ubUh3gu7zhZIPb7R7dyRzG371j
```

**To use your own content source:**

1. Create a folder in Google Drive or SharePoint
2. Share it with `helix@adobe.com` (for Google Drive) or configure SharePoint permissions
3. Update the URL in `fstab.yaml` with your folder's share link
4. Push changes to GitHub

### 2. Enable Universal Editor

The Universal Editor is automatically enabled for AEM Edge Delivery sites. To use it:

1. Navigate to your page with these query parameters:
   ```
   https://main--<repo>--<owner>.hlx.page/<page>?ref=main&repo=<repo>&owner=<owner>
   ```

2. The Universal Editor will load automatically
3. You'll see editing controls overlaid on your content

### 3. Authoring in Google Docs/Word

#### Creating New Pages

1. Create a new Google Doc or Word document in your content folder
2. Name it with the desired URL path (e.g., `about-us` for `/about-us`)
3. Add your content using standard formatting:
   - **Headings**: Use H1 for page title, H2-H6 for sections
   - **Images**: Insert directly from your computer
   - **Links**: Add hyperlinks normally
   - **Tables**: Use for block structures (see below)

#### Block Creation in Documents

Blocks are created using tables with specific formats:

**Hero Block Example:**
```
| Hero |
|------|
| ![Hero Image](image.jpg) |
| # Welcome to Volkswagen |
| Discover our electric future |
| [Learn More](/electric) |
```

**Cards Block Example:**
```
| Cards |
|-------|
| ![Car 1](car1.jpg) |
| ### ID.3 GTX |
| The future is electric |
| [Details](/id3) |
| --- |
| ![Car 2](car2.jpg) |
| ### T-Roc |
| Bold and dynamic |
| [Details](/t-roc) |
```

**Columns Block Example:**
```
| Columns |
|---------|
| ![Feature 1](feat1.jpg) |
| ### Innovation |
| Leading technology |
| --- |
| ![Feature 2](feat2.jpg) |
| ### Sustainability |
| Eco-friendly design |
```

### 4. Using the Sidekick

The AEM Sidekick is a browser extension that provides quick actions:

#### Installation

1. Install from [Chrome Web Store](https://chrome.google.com/webstore/detail/aem-sidekick/igkmdomcgoebiipaifhmpfjhbjccggml)
2. Pin the extension to your toolbar
3. Navigate to your content source or preview URL

#### Key Features

- **Preview**: See your changes immediately
- **Publish**: Push content live to production
- **Bulk Actions**: Preview or publish multiple pages
- **Content Tools**: Access editing utilities

#### Common Actions

1. **Preview a Page**
   - Open your Google Doc/Word file
   - Click the Sidekick extension
   - Click "Preview"
   - Your page opens in a new tab

2. **Publish a Page**
   - Click Sidekick while viewing preview
   - Click "Publish"
   - Content goes live immediately

3. **Bulk Publish**
   - Open the Sidekick
   - Click "Bulk" > "Publish"
   - Select pages to publish
   - Confirm action

### 5. Metadata Configuration

Add metadata to your pages using a table at the end of your document:

```
| Metadata |
|----------|
| Title | Your Page Title |
| Description | Your page description for SEO |
| Keywords | keyword1, keyword2, keyword3 |
| Image | /images/og-image.jpg |
```

Common metadata fields:
- **Title**: Page title for browser tab and SEO
- **Description**: Meta description for search engines
- **Image**: Open Graph image for social sharing
- **Template**: Custom page template name
- **Theme**: Custom theme name
- **Robots**: SEO robots directives (e.g., `noindex`)

### 6. Section Metadata

Control section styling using section metadata tables:

```
[Your content here]

| Section Metadata |
|------------------|
| Style | light, highlight |
| Background | #001e50 |
```

Available section styles:
- **light**: Light gray background
- **highlight**: Highlighted section
- **dark**: Dark background with light text

### 7. Working with Images

#### Image Optimization

Images are automatically optimized by AEM:
- Converted to WebP format
- Resized for responsive delivery
- Lazy-loaded for performance

#### Image Best Practices

1. **Use high-quality originals** (at least 2000px wide)
2. **Name files descriptively** (e.g., `vw-id3-hero.jpg`)
3. **Add alt text** in your document
4. **Use appropriate aspect ratios**:
   - Hero: 16:9 or 21:9
   - Cards: 16:9
   - Thumbnails: 1:1 or 4:3

### 8. Content Structure Best Practices

#### Page Organization

```
# Page Title (H1) - Only one per page

## Section 1 (H2)
Content for section 1

### Subsection 1.1 (H3)
Detailed content

## Section 2 (H2)
Content for section 2
```

#### Block Placement

- Use **Hero blocks** at the top of the page
- Place **Cards** for product/feature highlights
- Use **Columns** for multi-column layouts
- Add **CTAs** throughout for user engagement

### 9. Testing Your Content

1. **Preview First**: Always preview before publishing
2. **Check Responsiveness**: Test on mobile, tablet, and desktop
3. **Verify Links**: Ensure all links work correctly
4. **Test Performance**: Use Lighthouse or PageSpeed Insights
5. **Review SEO**: Check meta tags and structured data

### 10. Publishing Workflow

#### Development Workflow

1. **Create/Edit** content in Google Docs/Word
2. **Preview** using Sidekick (branch: main)
3. **Review** changes at `https://main--<repo>--<owner>.hlx.page`
4. **Publish** when satisfied
5. **Verify** at `https://<repo>--<owner>.hlx.live`

#### Branch-Based Workflow

For multiple authors or staging:

1. Create a branch in GitHub
2. Update documents
3. Preview at `https://<branch>--<repo>--<owner>.hlx.page`
4. Merge branch to main when ready
5. Publish from main branch

## Advanced Features

### Custom Components

Create custom blocks by:

1. Adding a new folder in `/blocks/`
2. Creating `blockname.js` and `blockname.css`
3. Implementing the `decorate()` function
4. Using the block in your documents

Example:
```javascript
// blocks/custom/custom.js
export default function decorate(block) {
  // Your custom logic
  block.innerHTML = '<p>Custom content</p>';
}
```

### Dynamic Content

Use JSON data sheets for dynamic content:

1. Create a spreadsheet in your content folder
2. Name it `data.xlsx`
3. Reference it in your page
4. AEM will convert it to JSON automatically

### Personalization

Add personalization using:
- URL parameters
- Cookies
- Adobe Target integration
- Custom JavaScript logic

## Troubleshooting

### Content Not Updating

1. Clear your browser cache
2. Click "Preview" again in Sidekick
3. Check if you're viewing the correct URL (preview vs. live)
4. Verify permissions on content source

### Blocks Not Rendering

1. Check table format in your document
2. Verify block name matches folder name exactly
3. Look for JavaScript errors in browser console
4. Ensure CSS and JS files exist for the block

### Images Not Loading

1. Verify image permissions in content source
2. Check image file format (JPG, PNG, WebP supported)
3. Ensure images are not too large (< 10MB recommended)
4. Look for CORS errors in browser console

### Sidekick Not Appearing

1. Verify extension is installed and enabled
2. Check that you're on a valid AEM page
3. Clear extension cache
4. Reinstall extension if needed

## Support Resources

- [AEM Documentation](https://www.aem.live/docs/)
- [Universal Editor Guide](https://www.aem.live/docs/authoring)
- [Block Collection](https://www.aem.live/developer/block-collection)
- [Community Forum](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community)

## Best Practices Summary

1. ✅ Always preview before publishing
2. ✅ Use semantic HTML and proper heading hierarchy
3. ✅ Optimize images before uploading
4. ✅ Add meaningful alt text to all images
5. ✅ Test on multiple devices and browsers
6. ✅ Keep content structure simple and clean
7. ✅ Use metadata for SEO optimization
8. ✅ Follow naming conventions for files and blocks
9. ✅ Document custom blocks and components
10. ✅ Keep blocks focused on single responsibilities

---

**Ready to start?** Open your content source, create a new document, and start authoring! The Universal Editor will guide you through the rest.

