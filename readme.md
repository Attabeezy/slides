# Slides for programming courses

This is a collection of slides for programming courses, created from markdown sources.

See <http://attabeezy.github.io/slides> for the slides.

The presentations are standalone HTML files that can be downloaded and viewed offline.

## Build process

To build from the sources:

- clone this repository
- run `npm ci` (to install dependencies from _package-lock.json_)
- run `npm run build`

This process starts with _sections/index.json_ and recursively includes materials

It creates output in the _docs_ folder

## Hosting on GitHub Pages

This repository is configured to automatically build and deploy to GitHub Pages. When you push to the `master` branch, a GitHub Actions workflow will:

1. Build the slides using `npm run build`
2. Deploy the contents of the `docs` folder to GitHub Pages

To enable GitHub Pages for your fork:

1. Go to your repository's Settings → Pages
2. Under "Source", select "GitHub Actions"
3. Push changes to the `master` branch to trigger a deployment
4. Your slides will be available at `https://<username>.github.io/<repository-name>/`

The workflow can also be triggered manually from the Actions tab.

## Technical details, writing your own

The slides in this repository are created from markdown sources via [rehype-slides](https://github.com/marko-knoebl/rehype-slides)

If you want to create your own presentations, see [rehype-slides-starter](https://github.com/marko-knoebl/rehype-slides-starter)

## Philosophy

These materials are organized so that _relevant_ and _generic_ content is prioritized

principles applied in these slides:

- Cover the most important aspects first, dive deeper later
  - do sensible exercises as early as possible
  - keep details for later or provide references for self-study
- Prioritize general priniples that can be applied elsewhere (e.g. focus on "SQL basics" instead of "SQL in Python")
