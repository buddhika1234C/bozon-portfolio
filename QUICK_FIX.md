# 🚨 QUICK FIX: Missing Supabase Credentials

## The Problem
You're seeing: **"Your project's URL and Key are required to create a Supabase client!"**

This means your `.env.local` file is either:
- Missing
- Empty
- Has incorrect values

## The Solution (3 Steps)

### Step 1: Get Your Supabase Credentials

1. **Go to Supabase Dashboard:**
   - Visit: https://supabase.com/dashboard
   - Log in to your account

2. **Select Your Project:**
   - Click on your project (or create one if you haven't)

3. **Get API Keys:**
   - Click **Settings** (gear icon) in the left sidebar
   - Click **API** in the settings menu
   - You'll see two important values:
     - **Project URL** (looks like: `https://xxxxx.supabase.co`)
     - **anon public** key (long string starting with `eyJ...`)

### Step 2: Update .env.local File

1. **Open `.env.local` file** in your project root folder
   - It's in: `C:\Users\buddh\OneDrive\Desktop\porfolio\.env.local`

2. **Replace the placeholder values** with your actual Supabase credentials:

```env
NEXT_PUBLIC_SUPABASE_URL=https://your-project-id.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.your-actual-key-here
NEXT_PUBLIC_SITE_URL=http://localhost:3000
```

**Example:**
```env
NEXT_PUBLIC_SUPABASE_URL=https://abcdefghijklmnop.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImFiY2RlZmdoaWprbG1ub3AiLCJyb2xlIjoiYW5vbiIsImlhdCI6MTYzODk2ODAwMCwiZXhwIjoxOTU0NTQ0MDAwfQ.example
NEXT_PUBLIC_SITE_URL=http://localhost:3000
```

3. **Save the file**

### Step 3: Restart the Server

1. **Stop the current server:**
   - In your terminal, press `Ctrl + C`

2. **Start it again:**
   ```bash
   npm run dev
   ```

3. **Check if it works:**
   - The error should be gone
   - You should see "Ready" message
   - Visit `http://localhost:3000`

---

## ⚠️ Important Notes

- **No spaces** around the `=` sign
- **No quotes** around the values (unless they contain spaces)
- Make sure you're using the **anon public** key, NOT the service_role key
- The file must be named exactly `.env.local` (with the dot at the start)

## 🆘 Still Having Issues?

1. **Check the file location:**
   - Make sure `.env.local` is in the root folder: `C:\Users\buddh\OneDrive\Desktop\porfolio\`

2. **Check for typos:**
   - Make sure there are no extra spaces
   - Make sure the URL starts with `https://`
   - Make sure the key is complete (they're very long)

3. **Restart everything:**
   - Close the terminal
   - Reopen it
   - Run `npm run dev` again

4. **Verify in Supabase:**
   - Make sure your Supabase project is active
   - Check that the API keys are correct in Settings > API

---

## 📝 Don't Have Supabase Set Up Yet?

If you haven't created a Supabase project yet, follow these steps:

1. **Create Supabase Account:**
   - Go to https://supabase.com
   - Sign up or log in

2. **Create New Project:**
   - Click "New Project"
   - Fill in project details
   - Wait 2-3 minutes for setup

3. **Run Database Schema:**
   - Go to SQL Editor in Supabase
   - Copy code from `supabase/schema.sql`
   - Paste and run it

4. **Get API Keys:**
   - Settings > API
   - Copy URL and anon key

5. **Add to .env.local:**
   - Follow Step 2 above

Then restart your server!

