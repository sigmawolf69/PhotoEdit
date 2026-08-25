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

Start the production build locally with:

```bash
npm run start
```

Before publishing changes, also run:

```bash
npm run lint
```

Both the build and lint commands should finish without errors.

## Project Structure

```text
app/
  globals.css       Global styles and responsive layout
  layout.tsx        Page metadata, fonts, and root layout
  page.tsx          Image editor interface and processing logic
public/
  favicon.svg       Browser icon
.openai/
  hosting.json      OpenAI Sites hosting configuration
eslint.config.mjs   Lint configuration
package.json        Dependencies and project commands
vite.config.ts      Vinext, Vite, and Cloudflare configuration
```

## Customization

### Branding and page content

Edit `app/page.tsx` to change the product name, headings, descriptions, footer text, or buttons.

### Colors and responsive design

Edit `app/globals.css`. The main theme colors are defined near the beginning of the file as CSS variables such as `--purple`, `--ink`, `--muted`, and `--cream`.

### Patreon link

Search for `https://www.patreon.com/c/abcd` in `app/page.tsx` and replace it with your own Patreon or product-download URL.

### Page title and description

Edit the `metadata` object in `app/layout.tsx`.

## Deployment

This project builds to a Cloudflare Worker-compatible Vinext application. It can be deployed through OpenAI Sites using the included `.openai/hosting.json` and `vite.config.ts` configuration.

For a different hosting provider, confirm that it supports the project's Vinext/Vite output and Node.js runtime requirements. Always run `npm run build` successfully before deployment.

No database, API key, image-storage service, or other environment variable is required for the current application.

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

