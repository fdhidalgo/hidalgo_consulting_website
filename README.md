# Hidalgo Research Consulting Website

This is the source code for the Hidalgo Research Consulting website, built with [Quarto](https://quarto.org/).

## Building the Site Locally

To preview the website locally:

```bash
quarto preview
```

To render the site:

```bash
quarto render
```

## Deploying to GitHub Pages

### Initial Setup

1. **Create a GitHub repository** and push this code:
   ```bash
   git init
   git add .
   git commit -m "Initial commit of Hidalgo Research Consulting website"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO.git
   git push -u origin main
   ```

2. **Configure GitHub Pages:**
   - Go to your repository on GitHub
   - Navigate to Settings > Pages
   - Under "Build and deployment":
     - Source: Select "GitHub Actions"

3. **Create GitHub Actions workflow:**
   Create `.github/workflows/publish.yml`:
   ```yaml
   name: Publish Quarto Website

   on:
     push:
       branches: main

   permissions:
     contents: read
     pages: write
     id-token: write

   jobs:
     build-deploy:
       runs-on: ubuntu-latest
       steps:
         - name: Check out repository
           uses: actions/checkout@v4

         - name: Set up Quarto
           uses: quarto-dev/quarto-actions/setup@v2

         - name: Render Quarto Project
           uses: quarto-dev/quarto-actions/render@v2

         - name: Upload Pages artifact
           uses: actions/upload-pages-artifact@v2
           with:
             path: _site

         - name: Deploy to GitHub Pages
           id: deployment
           uses: actions/deploy-pages@v2
   ```

4. **Push the workflow file:**
   ```bash
   git add .github/workflows/publish.yml
   git commit -m "Add GitHub Actions workflow for deployment"
   git push
   ```

### Updating the Site

After the initial setup, simply commit and push changes to the `main` branch:

```bash
git add .
git commit -m "Update website content"
git push
```

The site will automatically rebuild and deploy via GitHub Actions.

## Site Structure

- `index.qmd` - Home page with service overview
- `about.qmd` - About page with background and expertise
- `_quarto.yml` - Site configuration
- `styles.css` - Custom styling

## Contact

For questions about the consultancy, visit the website or email contact@hidalgoconsulting.com
