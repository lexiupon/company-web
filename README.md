# Lexiupon - Coming Soon Page

Professional coming soon page for Lexiupon, an AI agent data conversation platform.

**Tagline**: "Let Data Talk"

## Tech Stack

- **Framework**: [Astro 5.2+](https://astro.build) - Zero-JS static site generation
- **Styling**: [Tailwind CSS v4](https://tailwindcss.com) with Vite plugin
- **Language**: TypeScript (strict mode)
- **Package Manager**: [Bun](https://bun.sh) (fast, modern JavaScript runtime)
- **Deployment**: GitHub Pages with GitHub Actions
- **Hosting**: Custom domain via GitHub Pages

## Project Structure

```
company-web/
├── .github/workflows/
│   └── deploy.yml              # GitHub Actions deployment
├── public/
│   ├── CNAME                   # Custom domain
│   └── favicon.svg             # Logo as favicon
├── src/
│   ├── components/
│   │   └── Logo.astro          # Reusable logo component
│   ├── layouts/
│   │   └── Layout.astro        # Base HTML layout
│   ├── pages/
│   │   └── index.astro         # Coming soon page
│   └── styles/
│       └── global.css          # Tailwind + custom styles
├── astro.config.mjs            # Astro config with Tailwind v4
├── package.json                # Dependencies
├── bun.lock                    # Bun lockfile
├── tsconfig.json               # TypeScript config
└── README.md                   # This file
```

## Getting Started

### Prerequisites

- [Bun 1.0+](https://bun.sh/docs/installation) - Modern JavaScript runtime and package manager

### Local Development

```bash
# Install dependencies
bun install

# Start dev server with hot reload
bun run dev

# Open http://localhost:4321 in your browser
```

### Build for Production

```bash
# Build static site
bun run build

# Preview production build locally
bun run preview
```

The build output is in the `dist/` directory.

## Deployment

The site automatically deploys to GitHub Pages when you push to the `main` branch.

### First-Time Setup

1. **Configure GitHub Pages**:
   - Go to repository Settings → Pages
   - Set Source to "GitHub Actions"
   - Enable "Enforce HTTPS"

2. **Update Custom Domain** (optional):
   - Edit `public/CNAME` with your domain
   - Add DNS records at your domain provider:
     - **Option A**: Add CNAME pointing to `lexiupon.github.io`
     - **Option B**: Add A records for GitHub Pages IPs (see GitHub docs)

3. **Push to Deploy**:
   ```bash
   git add .
   git commit -m "feat: Lexiupon coming soon page with Bun"
   git push origin main
   ```

4. **Monitor Deployment**:
   - Check GitHub Actions tab for workflow status
   - Visit your domain URL (DNS may take 24-48 hours to propagate)

## Features

- ✨ Modern, responsive design
- 📱 Mobile-first approach (fully responsive)
- 🎨 Professional branding with hexagon logo
- 📧 Email signup form (localStorage for demo, ready for backend integration)
- 🎯 Optimized Lighthouse scores (90+)
- ♿ Semantic HTML, accessible design
- 🚀 Zero JavaScript by default (client-side validation only)
- 🌙 Supports dark mode (via CSS media queries)

## Email Signup Integration

Currently, signups are stored in browser localStorage for demonstration. To integrate a real email service:

1. **Choose a service**:
   - [ConvertKit](https://convertkit.com) - Creator-friendly
   - [Mailchimp](https://mailchimp.com) - Popular, free tier
   - [EmailOctopus](https://emailoctopus.com) - Simple, affordable
   - [Buttondown](https://buttondown.email) - Minimal, reliable

2. **Update the form handler** in `src/pages/index.astro`:
   - Replace localStorage logic with API call to your service
   - Handle success/error responses

3. **Example with ConvertKit**:
   ```typescript
   const response = await fetch('https://api.convertkit.com/v3/forms/{form_id}/subscriptions', {
     method: 'POST',
     body: JSON.stringify({ email, first_name: '' }),
   });
   ```

## Performance

- **Build time**: ~370ms
- **Page size**: ~4KB (gzipped)
- **Lighthouse**: Target 95+ on all metrics
- **No runtime JS**: Uses Astro's zero-JS approach

## Future Enhancements

- [ ] Add analytics (Google Analytics, Plausible)
- [ ] Email integration (Mailchimp, ConvertKit)
- [ ] Social links (Twitter, LinkedIn)
- [ ] Expand to full landing page
- [ ] Blog section
- [ ] Team/About pages

## Development Notes

### Astro vs Alternatives

- ✅ Zero-JS by default (unlike React/Vue)
- ✅ Tailwind v4 Vite integration
- ✅ Automatic code splitting
- ✅ Image optimization
- ✅ Built-in sitemap/RSS

### Why Not `@astrojs/tailwind`?

The deprecated `@astrojs/tailwind` integration doesn't support Tailwind CSS v4's Vite plugin. We use `@tailwindcss/vite` directly instead.

## Troubleshooting

### Build fails with Tailwind errors
- Ensure `@tailwindcss/vite` is installed: `bun add -d @tailwindcss/vite@latest`
- Check that `astro.config.mjs` includes the Vite plugin configuration

### CNAME issues
- Verify `public/CNAME` contains your domain (no https://, no trailing slash)
- DNS changes can take 24-48 hours to propagate
- Use `dig` or online tools to verify DNS records

### GitHub Actions fails
- Check Actions tab for error logs
- Verify Bun version (1.0+ required)
- Clear `.astro` cache: `rm -rf .astro && bun run build`

## License

© 2026 Lexiupon. All rights reserved.

## Support

For issues or questions:
- Create a GitHub issue
- Check [Astro docs](https://docs.astro.build)
- Check [Tailwind docs](https://tailwindcss.com/docs)
