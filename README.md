# Azure

Azure is a minimal theme for [Ghost](https://github.com/TryGhost/Ghost) focused on professional sites and portfolios. The theme is simple and highly configurable, emphasizing clean aesthetics and reader-friendliness.

**Demo: https://halabi.me**

## Installation

1. [Download the theme ZIP file](https://github.com/Woolball/Azure/raw/main/dist/azure.zip)
2. Log into Ghost and navigate to the `Theme` settings
3. Change theme by uploading the downloaded ZIP file

## Features

- Customizable header with primary and secondary text options
- Flexible hero layout with configurable image positioning
- Call-to-Action (CTA) buttons with customizable text and links
- Portfolio section for showcasing your projects
- Writing section for your blog posts
- Multiple navigation layout options
- Custom typography options

## Content Setup

### Projects/Portfolio

Projects are implemented as **pages** with the tag `#portfolio-case`:

1. Create a page in Ghost for each project
2. Add the `#portfolio-case` tag to the page
3. Set a featured image for visual appeal
4. Write a custom excerpt that will appear in the project listings
5. Projects are ordered by their published date on both the home page and the projects page

### Writing/Blog Posts

Writings are implemented as regular **posts**:

1. Create posts normally in Ghost
2. No special tags are required
3. Posts are ordered by their published date on both the home page and the writing page

### Template Pages

To create dedicated listing pages for projects and writings:

1. **Projects Page**: Create a page with the URL `/projects`
   - The theme automatically applies the project listing template
   - You can add a title and content to this page - the project listings will appear below
   
2. **Writing Page**: Create a page with the URL `/writing`
   - The theme automatically applies the writing listing template
   - Any content you add to this page will appear above the post listings

## Theme Configuration

Customize the theme by navigating to `Design & branding` in Ghost. The following options are available:

### General Settings

- **Background Color**: Set the main background color for your site
- **Typography**: Choose from:
  - Modern sans-serif (default)
  - Elegant serif 
  - Consistent mono
- **Footer Text**: Customize the text in the footer (defaults to site name + current year)

### Navigation

- **Navigation Layout**: Choose from Logo on the left (default), Logo in the middle, or Stacked
- **Navigation Alignment**: Set to Left (default) or Right

### Homepage Settings

- **Hero Layout**: Choose from Image Left (default) or Image Right
- **Primary Header**: Main heading text on the homepage
- **Secondary Header**: Subheading text on the homepage

### Call-to-Action Buttons

- **Primary CTA Label**: Text for the main CTA button
- **Primary CTA Link**: URL for the main CTA button (e.g., `/contact`)
- **Secondary CTA Label**: Text for the secondary CTA button
- **Secondary CTA Link**: URL for the secondary CTA button (e.g., `/services`)
*Note: Create corresponding pages for CTA links (e.g., contact page, services page)*

### Section Settings

- **Portfolio Section Title**: Customize the portfolio section heading (default: "Projects")
- **Portfolio Page URL**: Set the URL for the full portfolio page (default: "/projects")
- **Writings Section Title**: Customize the writings section heading (default: "Writing")
- **Writings Page URL**: Set the URL for the full writings page (default: "/writing")

## Optional Features

Azure includes support for several optional features that can be enabled through Ghost's code injection:

- [Contact Modal](docs/features/contact-modal.md) - Display a contact form when users click on your CTA buttons
- [Emoji to Icons Conversion](docs/features/emoji-to-icons.md) - Automatically convert emojis to Bootstrap icons

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
