# Eternity — Anniversary Website

A romantic, static anniversary story featuring a cinematic envelope opening, shared memories, chapters from the first year, a personal letter, and future dreams. The site uses only HTML, CSS, JavaScript, and local image/font assets at runtime; it does not require a backend.

## Features

- Responsive, full-screen envelope landing page and animated story reveal
- Clickable chapter photos, memory gallery, and future-dream cards
- Scroll reveals, lightweight canvas particles, and heart click effects
- Single-file HTML with inline CSS and JavaScript, plus local images and fonts (no runtime CSS framework or font CDN)
- SEO metadata, social-sharing tags, favicon, sitemap, and robots file
- Static deployment to GitHub Pages, Vercel, or Netlify

## Project structure

```text
/
├── index.html
├── *.jpg (photos)
├── *.woff2 (fonts)
├── heart.svg (icon)
├── .github/
│   └── workflows/
│       └── pages.yml
├── favicon.ico
├── robots.txt
├── sitemap.xml
└── README.md
```

All site styles and interactions are embedded in `index.html`. Photos, fonts, and the SVG icon stay beside `index.html` in the repository root, with relative paths. No build tools or package installation are needed.

## Replace photos

All photos live beside `index.html` in the repository root. The HTML includes `Replace … Here` comments beside the corresponding image elements. Keep each replacement filename simple and update that element's `src` in `index.html` to match, for example:

```html
<!-- Replace Chapter 1 Photo Here -->
<img src="./day%20we%20met.jpg" ... />
```

The landing backdrop, hero center image, hero memory photos, seven chapter images, five gallery photos, featured couple image, and four dream images are all in that folder. CSS backgrounds are defined in the `<style>` block in `index.html`.

Use optimized JPG, WebP, or AVIF images at an appropriate display resolution. The content images are lazy-loaded where practical; the first-screen images are loaded eagerly.

## Set the public site URL (SEO and sharing)

For deployments outside GitHub Pages, replace **every** `https://YOUR-DOMAIN.example` placeholder with the site's final public origin in:

- `index.html` (`og:url`, `og:image`, Twitter image, and canonical link)
- `robots.txt` (sitemap URL)
- `sitemap.xml` (page URL)

The GitHub Pages workflow fills these URLs from the configured Pages base URL in the deployment artifact; the checked-in source files remain reusable. For Vercel or Netlify, use the host's public URL. Social-sharing crawlers generally need absolute, publicly reachable URLs; local or relative image paths are not sufficient for reliable previews. Preview caches may take time to refresh after deployment.

## Deploy

### GitHub Pages

1. Push the project files to a GitHub repository on the `main` branch.
2. In **Settings → Pages**, set **Build and deployment → Source** to **GitHub Actions**.
3. The workflow in `.github/workflows/pages.yml` publishes the static site after each push to `main` and fills in the SEO URLs automatically. Check the **Actions** tab for the deployment URL.

If your default branch is not `main`, update the workflow's push branch first. The site uses relative asset paths, so it also works at a repository URL such as `https://OWNER.github.io/REPOSITORY/`.

### Vercel

1. Import the GitHub repository in Vercel, or deploy the project folder using the Vercel CLI.
2. Choose **Other** as the framework preset if prompted. No build command or output directory is required; serve the project root.
3. Deploy, update the public URL placeholders, and redeploy.

### Netlify

1. Import the GitHub repository in Netlify, or drag the project folder into Netlify Drop.
2. Set the publish directory to the project root (`.`). Leave the build command empty.
3. Deploy, update the public URL placeholders, and redeploy.

## Notes

- The site is static and does not include music or an audio player.
- The GitHub Pages workflow generates production URLs in its deployment artifact; set the host URL manually for other providers.
