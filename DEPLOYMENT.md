# Deployment Instructions

## Option 1: Serve from `/docs` (Recommended)

1.  Go to your GitHub Repository **Settings**.
2.  Click on **Pages** in the left sidebar.
3.  Under **Build and deployment** > **Source**, select **Deploy from a branch**.
4.  Under **Branch**, select `main` and then choose the `/docs` folder (instead of `/(root)`).
5.  Click **Save**.

This will serve the production build located in the `docs` folder, which is correctly optimized and configured.

## Option 2: Deploy to `gh-pages` branch

If you prefer to keep the source on `main` and deploy the site to a separate branch:

1.  Run the following command locally:
    ```bash
    npm run deploy
    ```
2.  This will push the `docs` folder content to a `gh-pages` branch.
3.  Go to **Settings** > **Pages**.
4.  Under **Branch**, select `gh-pages` and `/(root)`.
5.  Click **Save**.

## Troubleshooting

-   **"MIME type of application/octet-stream"**: This error happens when GitHub Pages tries to serve the *source code* (`index.tsx`) instead of the built application. **You are serving the root folder, which is incorrect.** Ensure you are serving the `docs` folder (Option 1) or the `gh-pages` branch (Option 2), NOT the root of the `main` branch.
-   **"cdn.tailwindcss.com should not be used in production"**: This warning appears if you are serving the development `index.html`. The production build in `docs/` does not use the CDN.
-   **"Failed to load module script"**: This confirms you are loading `index.html` from the root. Please follow Option 1 or Option 2 above.
