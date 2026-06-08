# Airtable Form Integration Guide

## Step-by-Step Instructions

### 1. Create Your Airtable Base

1. Go to [airtable.com](https://airtable.com) and sign in (or create a free account)
2. Click "Add a base" → "Start from scratch"
3. Name it "Bobathon 2026 Registration"

### 2. Set Up Your Table Fields

Create these fields in your table:
- **Full Name** (Single line text)
- **Email** (Email)
- **GitHub Username** (Single line text)
- **Brief Introduction** (Long text)

### 3. Create a Form View

1. Click the "+" next to "Grid view" at the top
2. Select "Form"
3. Name it "Registration Form"
4. Customize the form:
   - Add a title: "Bobathon 2026 Registration"
   - Add a description
   - Reorder fields as needed
   - Mark required fields (Full Name and Email should be required)

### 4. Get Your Embed URL

1. Click the "Share form" button in the top right
2. Click "Embed this form on your site"
3. You'll see an iframe code like this:
   ```html
   <iframe class="airtable-embed" src="https://airtable.com/embed/appXXXXXXXXXXXXXX/shrXXXXXXXXXXXXXX?backgroundColor=blue" ...>
   ```
4. **Copy the URL** from the `src` attribute (the part that starts with `https://airtable.com/embed/...`)

### 5. Update Your HTML

Open `index.html` and find line 691-704 (the embed-panel section).

**Replace this:**
```html
<div class="embed-panel">
  <div class="placeholder-text">
    <!-- SVG placeholder code -->
  </div>
</div>
```

**With this:**
```html
<div class="embed-panel">
  <iframe
    class="airtable-embed embed-frame"
    title="Bobathon 2026 Registration Form"
    src="YOUR_AIRTABLE_EMBED_URL_HERE"
    frameborder="0"
    onmousewheel=""
    width="100%"
    height="533"
    style="background: transparent; border: 1px solid #ccc;">
  </iframe>
</div>
```

**Replace `YOUR_AIRTABLE_EMBED_URL_HERE`** with your actual Airtable embed URL.

### 6. Update the Sidebar Link

Find line 723 and update the href with your form's direct link:
```html
<a
  class="form-link"
  href="YOUR_AIRTABLE_FORM_DIRECT_URL"
  target="_blank"
  rel="noopener noreferrer">
  Open Airtable Form
</a>
```

## Example

If your Airtable embed URL is:
```
https://airtable.com/embed/appDu8nD1clOGFPoE/pagUoOCii6OPMWPZd/form
```

Your iframe would look like:
```html
<iframe
  class="airtable-embed embed-frame"
  title="Bobathon 2026 Registration Form"
  src="https://airtable.com/embed/appDu8nD1clOGFPoE/pagUoOCii6OPMWPZd/form"
  frameborder="0"
  onmousewheel=""
  width="100%"
  height="533"
  style="background: transparent; border: 1px solid #ccc;">
</iframe>
```

## Tips

- The form will be fully functional and responsive
- Submissions will automatically appear in your Airtable base
- You can customize the form appearance in Airtable (colors, logo, etc.)
- You can set up email notifications for new submissions in Airtable
- The CSS is already configured to handle the iframe properly

## Need Help?

If you encounter any issues:
1. Make sure your Airtable base is set to allow embedding
2. Check that you copied the full embed URL
3. Verify the form is published and not in draft mode
4. Test the direct form link first before embedding