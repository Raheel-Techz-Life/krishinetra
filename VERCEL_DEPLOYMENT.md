# Vercel Deployment Guide

## 404 Error Fix

If you're seeing a `404: NOT_FOUND` error on Vercel, follow these steps:

### 1. Environment Variables

Add these environment variables in your Vercel project settings:

**Dashboard → Settings → Environment Variables:**

```
NEXT_PUBLIC_API_URL = (leave empty for mock data)
NEXT_PUBLIC_API_TIMEOUT = 30000
```

Or if you have a deployed backend:
```
NEXT_PUBLIC_API_URL = https://your-api.com/api
```

### 2. Build Configuration

The `vercel.json` file is already configured. No additional action needed.

### 3. Redeploy After Changes

After setting environment variables:
1. Go to **Deployments**
2. Click the three dots on the last deployment
3. Select **Redeploy**

Or simply push a new commit to the main branch to trigger automatic redeploy.

### 4. Check Build Logs

If 404 persists:
1. Go to **Deployments** → Last deployment
2. Click **Logs** to see build errors
3. Check **Runtime Logs** for runtime errors

### 5. Common Issues

**Issue: Cannot find module errors**
- Solution: Reinstall dependencies in Vercel
- Click **Settings → Git** and toggle "Ignored Build Step" off

**Issue: Pages not rendering**
- Solution: Check that all UI components are properly imported
- Verify no environment variables are missing

**Issue: Slow initial load**
- Solution: This is normal for Next.js first deploy
- Subsequent loads will be cached

## Development Mode

To test locally before deploying:

```bash
npm run build    # Test production build
npm start        # Run production build locally
# Open http://localhost:3000
```

## With Backend API

If using a backend API:

1. Deploy backend API separately (Node.js, Python, etc.)
2. Get the API URL (e.g., `https://api.example.com`)
3. Add `NEXT_PUBLIC_API_URL=https://api.example.com` to Vercel environment variables
4. Redeploy the frontend

## Current Status

- Frontend: Deployed on Vercel ✓
- Backend: Not included (uses mock data)
- You can add a backend API anytime and configure the URL

For more help, check the [BACKEND_INTEGRATION.md](./BACKEND_INTEGRATION.md) file.
