# Render Deployment Guide for Vite + React App

This guide will help you deploy your Vite + React app to Render.com.

## 1. Prepare your project
- Make sure your project builds locally: `npm run build`
- Your `vite.config.ts` should not have any custom base/publicDir that breaks static hosting.
- Your environment variables (like `VITE_GEMINI_API_KEY`) should be in `.env` (for local) and set in Render's dashboard for production.

## 2. Push your code to GitHub
Render deploys from GitHub, GitLab, or Bitbucket.
- Initialize git if you haven't: `git init`
- Add and commit your code: `git add . && git commit -m "Initial commit"`
- Create a new repo on GitHub and push your code.

## 3. Create a new Static Site on Render
- Go to https://dashboard.render.com/
- Click "New +" > "Static Site"
- Connect your GitHub repo
- Set the following build and publish settings:
  - **Build Command:** `npm run build`
  - **Publish Directory:** `dist`
- Add your environment variable(s) under "Environment" (e.g. `VITE_GEMINI_API_KEY`)
- Click "Create Static Site"

## 4. Wait for build and deploy
- Render will install, build, and deploy your app.
- You will get a public URL when done.

## 5. Troubleshooting
- If you see a blank page, check the Render build logs and browser console.
- Make sure your environment variables are set in Render's dashboard (not just in `.env.local`).
- For client-side routing, add a `static.json` file with:

```
{
  "routes": [
    { "src": "/.*", "dest": "/index.html" }
  ]
}
```

and place it in your project root.

---

For more, see: https://render.com/docs/deploy-create-react-app
