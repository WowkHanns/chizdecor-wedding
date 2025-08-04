# Supabase Environment Variables Setup

## Problem

Frontend dan backend menggunakan Supabase project yang berbeda, menyebabkan data tidak sinkron.

## Current Setup

### Backend (Railway) - Project 1:

```
SUPABASE_URL=https://xzdmtcetmnorzlywwkwt.supabase.co
SUPABASE_SERVICE_ROLE_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6Inh6ZG10Y2V0bW5vcnpseXd3a3d0Iiwicm9sZSI6InNlcnZpY2Vfcm9sZSIsImlhdCI6MTc0ODYwMTkxMiwiZXhwIjoyMDY0MTc3OTEyfQ.WVmuMkMJBSIIc1Qll4ilI2XAwsFYkSpAsBUfoZXnkoc
```

### Frontend - Project 2 (WRONG):

```
VITE_SUPABASE_URL=https://klbagrwkhkrbkprmiwqd.supabase.co
VITE_SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImtsYmFncndraGtyYmtwcm1pd3FkIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NDY5NTM3NjIsImV4cCI6MjA2MjUyOTc2Mn0.ccycQwXXqD3yUq7vq4usz-cjJeJCHx73IVkALEJe_8s
```

## Solution

### 1. Get Correct Anon Key

1. Go to Supabase Dashboard: https://supabase.com/dashboard
2. Select project: `xzdmtcetmnorzlywwkwt`
3. Go to Settings → API
4. Copy the "anon public" key

### 2. Update Frontend Environment Variables

Set in Vercel Environment Variables:

```
VITE_SUPABASE_URL=https://xzdmtcetmnorzlywwkwt.supabase.co
VITE_SUPABASE_ANON_KEY=your_correct_anon_key_here
```

### 3. Update Local .env File

Replace the current `.env` with:

```
VITE_API_URL=https://backendweddingdecoration-production.up.railway.app
REACT_APP_API_URL=https://backendweddingdecoration-production.up.railway.app
VITE_SUPABASE_URL=https://xzdmtcetmnorzlywwkwt.supabase.co
VITE_SUPABASE_ANON_KEY=your_correct_anon_key_here
```

## Important Notes

- ✅ **Use same Supabase project** for frontend and backend
- ✅ **Anon key is different** from service role key
- ✅ **Service role key** is for backend only
- ✅ **Anon key** is for frontend only

## Test After Setup

1. Frontend should be able to connect to same database as backend
2. Data should be synchronized between frontend and backend
3. User authentication should work properly
