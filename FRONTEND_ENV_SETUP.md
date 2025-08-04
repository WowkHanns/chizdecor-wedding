# Frontend Environment Variables Setup

## Problem

Frontend tidak bisa mengambil data dari backend karena `VITE_API_URL` tidak diset.

## Solution

### 1. Create `.env` file in frontend root:

```bash
# Backend API URL - Your actual Railway URL
VITE_API_URL=https://backendweddingdecoration-production.up.railway.app

# For React components that use process.env
REACT_APP_API_URL=https://backendweddingdecoration-production.up.railway.app
```

### 2. Set Environment Variables in Vercel:

1. Go to your Vercel project dashboard
2. Go to "Settings" → "Environment Variables"
3. Add these variables:

```
VITE_API_URL=https://backendweddingdecoration-production.up.railway.app
REACT_APP_API_URL=https://backendweddingdecoration-production.up.railway.app
```

### 3. Test Backend URL:

Test if backend is working:

```bash
curl https://backendweddingdecoration-production.up.railway.app/
```

Expected response:

```json
{
  "message": "Hello World!",
  "status": "healthy",
  "timestamp": "...",
  "environment": "production",
  "port": "3000"
}
```

### 4. Redeploy Frontend:

After setting environment variables, redeploy your frontend on Vercel.

## Test

After setup, your frontend should be able to:

- ✅ Load data from backend
- ✅ Show gallery images
- ✅ Display project decorations
- ✅ Handle user authentication

## Troubleshooting

If still not working:

1. Check browser console for CORS errors
2. Verify Railway URL is correct: `https://backendweddingdecoration-production.up.railway.app`
3. Check if backend is responding at `/` endpoint
4. Make sure environment variables are set in Vercel (not just local)
