# FIT5032 Week 12 Studio

A small Vue 3 + Vite application with a counter, Home and About routes, and GitHub Actions deployment to GitHub Pages.

## Local Development

Use Node.js 24 (the version used in CI), or a supported Vite version of Node.js (20.19+ or 22.12+).

```sh
npm ci
npm run dev
```

```sh
npm run build
npm run preview
```

Open the URL printed by Vite. The development base is `/`; the production preview base is `/fit5032-week-12-studio/`.

## CI/CD

The workflow in [.github/workflows/deploy.yml](.github/workflows/deploy.yml) runs on pushes to `main`, or manually through the Actions tab. It checks out the source, sets up Node.js 24 with npm caching, runs `npm ci`, builds, and publishes `dist` to `gh-pages` using `JamesIves/github-pages-deploy-action@v4`. Deployment requires `contents: write`, which is declared in the workflow.

The production base path is configured in [vite.config.js](vite.config.js). This is a Vite project, so `vue.config.js` from Vue CLI is not used. If the repository name changes, update the production base path.

The router uses `createWebHistory(import.meta.env.BASE_URL)` and lazy-loads the About view. The build copies `index.html` to `404.html` because GitHub Pages has no server-side SPA rewrite support. A direct visit to `/fit5032-week-12-studio/about` therefore renders the application through GitHub Pages' custom 404 document. The initial HTTP response still has a 404 status; internal navigation uses normal history URLs.

## Publish to GitHub

The repository remote is already configured as `https://github.com/jacob-delapaz/fit5032-week-12-studio.git`.

```sh
git add .
git commit -m "Set up Vue app and GitHub Pages CI/CD"
git push -u origin main
```

1. Open the repository's **Actions** tab and wait for **Deploy to GitHub Pages** to succeed. This creates the `gh-pages` branch.
2. Open **Settings > Pages**.
3. Set **Source** to **Deploy from a branch**.
4. Choose **gh-pages** and **/ (root)**, then save.
5. Wait for GitHub's Pages publishing workflow to finish.

Use a public repository unless your GitHub plan supports Pages for private repositories. Organization or repository policies must also allow Actions and the deployment action.

Expected site URL after publishing:

https://jacob-delapaz.github.io/fit5032-week-12-studio/

Subsequent changes deploy automatically:

```sh
git add .
git commit -m "Update studio"
git push
```

If no deployment starts, check that the push reached `main`, Actions are enabled, and the workflow has permission to write repository contents.
