# Azure

Azure is a minimal theme for [Ghost](https://github.com/TryGhost/Ghost) focused on professional sites and portfolios. The theme is simple and highly configurable, emphasizing clean aesthetics and reader-friendliness.

**Demo: https://halabi.me**

## Installation

1. [Download the theme ZIP file](https://github.com/Woolball/Azure/raw/main/dist/azure.zip)
2. Log into Ghost and navigate to the `Theme` settings
3. Change theme by uploading the downloaded ZIP file

## Usage

Customize the theme by navigating to `Design & branding` through the following variables:

- **Navigation**
  - Layout configuration
  - Alignment options

- **Header**
  - Cover image positioning
  - Primary and secondary header text

- **Call-to-Action (CTA)**
  - Primary CTA text and link
  - Secondary CTA text and link
  - *Note: Create corresponding pages for CTA links (e.g., contact page, services page)*

- **Page Sections**
  - Customize home page section titles (portfolio and writings)
  - Configure links to full portfolio and writings pages

Optional page templates for portfolio and writings are available and can be linked from the homepage by populating the respective title variables.

## Development

This theme uses Gulp and PostCSS for style compilation. Ensure you have the following installed:
- [Node.js](https://nodejs.org/)
- [Gulp](https://gulpjs.com)

Setup and development workflow:

```bash
# Install dependencies
npm install

# Build and watch for changes
gulp dev

# Generate distribution ZIP
gulp zip
```

CSS files in `/assets/css/` are automatically compiled to `/assets/built/`. 

The `gulp zip` command packages the theme files into `dist/azure.zip`, ready for upload to your Ghost site.

## Contribution

Contributions are welcome! Please fork the repository, commit, push and submit a pull request for review.

## Copyright & License

Copyright (c) 2025 Ammar Halabi - Released under the [MIT license](LICENSE).

## Acknowledgements

This theme is loosely based on the [Solo theme](https://github.com/TryGhost/Solo), and inspired by [Medium](https://medium.com).
