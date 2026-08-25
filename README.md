# BlurShield

BlurShield is a privacy-first browser image redaction tool. Users can blur, pixelate, or cover sensitive areas in JPG, PNG, and WebP images, then export one processed image or download the full batch as a ZIP file.

All image processing happens locally in the browser. The application does not upload user images to a server.

## Features

- Drag and drop images anywhere on the page
- Select multiple images at once
- Rectangle and ellipse regions
- Blur, pixelate, and solid-cover effects
- Adjustable effect intensity and cover color
- Region selection, deletion, undo, and redo
- Individual PNG export
- Batch ZIP export
- Responsive desktop and mobile interface

## Requirements

Install the following before setting up the project:

- [Node.js](https://nodejs.org/) 22.13 or newer
- npm, which is included with Node.js

You can confirm the installed versions with:

```bash
node --version
npm --version
```

## Installation

1. Extract the downloaded source-code archive.
2. Open a terminal in the extracted project folder.
3. Install the dependencies:

```bash
npm install
```

4. Start the local development server:

```bash
npm run dev
```

5. Open the local URL shown in the terminal. It is usually `http://localhost:3000`.

Changes to the source files will automatically refresh the development page.

## Production Build

Create an optimized production build with:

```bash
npm run build
```

Preview the production build locally with:

```bash
npm run preview
```

Before publishing changes, also run:

```bash
npm run lint
```

Both the build and lint commands should finish without errors.

## Project Structure

```text
src/
  App.tsx           Image editor interface and processing logic
  main.tsx          React browser entry point
  styles.css        Global styles and responsive layout
public/
  favicon.svg       Browser icon
index.html          Page metadata and application mount point
eslint.config.mjs   Lint configuration
package.json        Dependencies and project commands
vite.config.ts      Static Vite build configuration
```

## Customization

### Branding and page content

Edit `src/App.tsx` to change the product name, headings, descriptions, footer text, or buttons.

### Colors and responsive design

Edit `src/styles.css`. The main theme colors are defined near the beginning of the file as CSS variables such as `--purple`, `--ink`, `--muted`, and `--cream`.

### Patreon link

Search for `https://www.patreon.com/c/abcd` in `src/App.tsx` and replace it with your own Patreon or product-download URL.

### Page title and description

Edit the `<title>` and metadata tags in `index.html`.

## GitHub Automation

The repository includes the following automation:

- `.github/workflows/ci.yml` runs lint and a production build for pushes and pull requests targeting `main`.
- `.github/workflows/deploy-pages.yml` builds and publishes the static `dist` folder to GitHub Pages after every push to `main`.
- `.github/dependabot.yml` checks npm packages and GitHub Actions for updates every week.

To enable publishing, open the GitHub repository and go to **Settings → Pages**. Under **Build and deployment**, choose **GitHub Actions** as the source. Push to `main`, then follow the deployment from the repository's **Actions** tab. GitHub automatically creates the `github-pages` environment and displays the public URL after a successful deployment. No external hosting credentials are required.

## Privacy Notes

- Imported images are represented by temporary browser object URLs.
- Editing and rendering use the browser Canvas API.
- ZIP files are generated locally with JSZip.
- Images and edits are not permanently saved. Refreshing or closing the tab clears the working session.
- A hosting provider still receives normal website traffic information, but not the images processed inside the editor.

## Troubleshooting

### `npm install` fails

Confirm that Node.js 22.13 or newer is installed. Delete only the incomplete `node_modules` folder, then run `npm install` again.

### The local page does not open

Check the terminal for the exact local URL and confirm that `npm run dev` is still running. If the default port is occupied, the development server may choose another port.

### An image is rejected

Use a valid JPG, PNG, or WebP image. Other file types are intentionally skipped.

### Export does not download

Allow downloads for the website in the browser. Batch export creates one ZIP file, while individual export creates a PNG file.

### Browser performance is slow

Very large images and large batches can use significant memory because processing happens locally. Try fewer images at once or resize extremely large images before importing them.

## Support

When requesting support, include:

- Operating system
- Browser name and version
- Node.js version
- The command that failed
- The complete error message, excluding passwords, tokens, or other secrets
