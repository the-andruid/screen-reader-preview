# Screen Reader Preview

An open-source tool for previewing how text sounds when spoken aloud. Detects ASCII tables, maps, art, and decorative borders that create accessibility barriers in text games such as MUDs.

**Live tool:** [writing-games.org/screen-reader-preview](https://writing-games.org/screen-reader-preview)

## Features

- Paste text to hear how a screen reader would read it
- Detects problematic ASCII art, tables, maps, and decorative borders and makes recommendations
- Simulates behavior of popular screen readers (NVDA, JAWS, VoiceOver)
- Runs entirely in the browser using the Web Speech API

## Usage

Open `index.html` in a browser or visit the live site. Paste your text into the input area and click Analyze & Read Aloud to hear how it sounds. Any detected issues and recommendations will be shown below.

## Hosting Your Own Version

This is a single-file tool - just `index.html` - so hosting your own copy is straightforward. Drop it on any web server or embed it in your game's website. Here's what you'll want to customize:

### 1. Remove the analytics script

The `<script>` tag near the end of `<head>` loads Litlyx analytics for the original site. Litlyx is a privacy-respecting, cookieless analytics tool. Leaving the script in won't hurt anything, but you might as well remove it or replace it with your own.

### 2. Update the Content Security Policy for your domain

The CSP meta tag near the top of `<head>` controls which external resources the page is allowed to load. Update it for your own domain:

- **`script-src`** - remove `https://static.cloudflareinsights.com` if you use cloudflare and want to block it; remove `https://cdn.jsdelivr.net` (only needed for the Litlyx script you just removed)
- **`img-src`** - change `https://writing-games.org` to your domain (or `'self'` if images are local)
- **`style-src`** and **`font-src`** - keep the Google Fonts entries if you use the same fonts, or adjust for your own

### 3. Update meta tags and SEO

- **`<title>`** - update the page title
- **`<link rel="canonical">`** - change to your URL
- **Open Graph tags** - update `og:url`, `og:site_name`, and `og:image` to your own (search for `og:` in `<head>`)
- **Twitter card tags** - update title, description, and image (search for `twitter:` in `<head>`)
- **`<meta name="description">`** and **`<meta name="keywords">`** - adjust if needed

### 4. Swap out images and branding

- **`og:image`** - replace with your own icon/logo
- **Footer icon** - the `<img>` in the footer points to the Writing Games logo; replace or remove it
- **Footer links** - update the site name, URL, and contact link to your own

### 5. Adjust CSS to match your theme

The styles are all inline in `index.html`. Key things you might want to change:

- Color variables (search for `background`, `color`, `border-color`)
- Font choices (currently uses Atkinson Hyperlegible via Google Fonts)
- Layout widths and spacing

### 6. Update the feedback/contact link

The FAQ section includes a link to the GitHub Issues page and Discord. Point these to your own support channels, or remove them.

### 7. Update the FAQ schema

The `<head>` contains a `<script type="application/ld+json">` block with structured data for the FAQ section. If you change any FAQ text, links, or questions, update the schema to match -- AI search engines and answer engines (ChatGPT, Perplexity, Google AI Overviews) actively crawl and cite FAQ structured data.

Or you can take the entire FAQSchema out for easier maintainability. Your choice.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
