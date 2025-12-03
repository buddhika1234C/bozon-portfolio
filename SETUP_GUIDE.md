# Step-by-Step Setup & Testing Guide

Follow these steps to get your admin panel up and running:

## Step 1: Set Up Supabase (5-10 minutes)

### 1.1 Create Supabase Project
1. Go to [https://supabase.com](https://supabase.com)
2. Sign up or log in
3. Click **"New Project"**
4. Fill in:
   - **Name:** portfolio-admin (or any name)
   - **Database Password:** Create a strong password (save it!)
   - **Region:** Choose closest to you
5. Click **"Create new project"**
6. Wait 2-3 minutes for project to initialize

### 1.2 Set Up Database
1. In your Supabase project, go to **SQL Editor** (left sidebar)
2. Click **"New query"**
3. Open the file `supabase/schema.sql` from this project
4. Copy ALL the SQL code from that file
5. Paste it into the SQL Editor
6. Click **"Run"** (or press Ctrl+Enter)
7. You should see "Success. No rows returned"

### 1.3 Verify Storage Bucket
1. Go to **Storage** (left sidebar)
2. You should see a bucket named **"projects"**
3. If it's not there, the SQL might have failed - check for errors

### 1.4 Get Your API Keys
1. Go to **Settings** (gear icon, left sidebar)
2. Click **"API"**
3. You'll see:
   - **Project URL** (looks like: `https://xxxxx.supabase.co`)
   - **anon public** key (long string starting with `eyJ...`)
4. **Copy both** - you'll need them in the next step

## Step 2: Configure Environment Variables (2 minutes)

### 2.1 Create .env.local File
1. In your project root folder (`porfolio`), create a new file named `.env.local`
2. Open it in a text editor
3. Paste this template:

```env
NEXT_PUBLIC_SUPABASE_URL=your_project_url_here
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_anon_key_here
NEXT_PUBLIC_SITE_URL=http://localhost:3000
```

4. Replace:
   - `your_project_url_here` with your **Project URL** from Step 1.4
   - `your_anon_key_here` with your **anon public** key from Step 1.4
5. Save the file

**Example:**
```env
NEXT_PUBLIC_SUPABASE_URL=https://abcdefghijklmnop.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImFiY2RlZmdoaWprbG1ub3AiLCJyb2xlIjoiYW5vbiIsImlhdCI6MTYzODk2ODAwMCwiZXhwIjoxOTU0NTQ0MDAwfQ.example
NEXT_PUBLIC_SITE_URL=http://localhost:3000
```

## Step 3: Create Admin User (2 minutes)

### 3.1 Add User in Supabase
1. In Supabase, go to **Authentication** (left sidebar)
2. Click **"Users"** tab
3. Click **"Add user"** button (top right)
4. Choose **"Create new user"**
5. Fill in:
   - **Email:** `buddhikachandra0001@gmail.com` (MUST be exact)
   - **Password:** Create a password (remember it!)
   - **Auto Confirm User:** ✅ Check this box
6. Click **"Create user"**

## Step 4: Start the Development Server (1 minute)

### 4.1 Run the Server
1. Open terminal/command prompt in your project folder
2. Run:
```bash
npm run dev
```

3. Wait for it to start (you'll see "Ready" message)
4. The server runs at: `http://localhost:3000`

## Step 5: Test the Admin Panel (5 minutes)

### 5.1 Test Login
1. Open your browser
2. Go to: `http://localhost:3000/admin/login`
3. You should see a black login page
4. Enter:
   - **Email:** `buddhikachandra0001@gmail.com`
   - **Password:** (the password you set in Step 3.1)
5. Click **"Sign In"**
6. You should be redirected to `/admin/dashboard`

### 5.2 Test Dashboard
1. You should see:
   - Left sidebar with "Admin Panel" title
   - "Add Project" button
   - Empty projects table (or existing projects)
2. If you see the dashboard, ✅ **SUCCESS!**

### 5.3 Test Adding a Project
1. Click **"Add Project"** button
2. Fill in the form:
   - **Title:** "Test Project"
   - **Description:** "This is a test project"
   - **Video:** 
     - Click the upload area OR drag & drop a video file
     - Wait for upload progress bar
     - Video should appear with preview
3. Click **"Create Project"**
4. The project should appear in the table ✅

### 5.4 Test Edit Project
1. Click the **Edit icon** (pencil) next to a project
2. Change the title or description
3. Click **"Update Project"**
4. Changes should be saved ✅

### 5.5 Test Delete Project
1. Click the **Delete icon** (trash) next to a project
2. Confirm deletion
3. Project should disappear from table ✅

### 5.6 Test Forgot Password
1. Sign out (click "Sign Out" in sidebar)
2. Go to login page
3. Click **"Forgot Password?"**
4. Enter: `buddhikachandra0001@gmail.com`
5. Click **"Send Reset Link"**
6. You should see success message ✅
7. Check your email for reset link

## Troubleshooting

### ❌ "Invalid API key" error
- Check your `.env.local` file has correct values
- Make sure there are no extra spaces
- Restart the dev server after changing `.env.local`

### ❌ "User not found" on login
- Make sure you created the user in Supabase (Step 3)
- Check the email is exactly: `buddhikachandra0001@gmail.com`
- Make sure "Auto Confirm User" was checked

### ❌ "Bucket not found" on upload
- Go to Supabase Storage
- Check if "projects" bucket exists
- If not, re-run the SQL from `supabase/schema.sql`

### ❌ Can't access dashboard
- Make sure you're logged in
- Check browser console for errors (F12)
- Try clearing cookies and logging in again

### ❌ Video upload fails
- Check file size (max 100MB)
- Check file is a video format (MP4, MOV, WebM)
- Check Supabase Storage bucket permissions

## Quick Test Checklist

- [ ] Supabase project created
- [ ] SQL schema executed successfully
- [ ] `.env.local` file created with correct values
- [ ] Admin user created in Supabase
- [ ] Dev server running (`npm run dev`)
- [ ] Can access `/admin/login`
- [ ] Can log in successfully
- [ ] Can access `/admin/dashboard`
- [ ] Can add a new project
- [ ] Can upload a video
- [ ] Can edit a project
- [ ] Can delete a project

## Next Steps

Once everything works:
1. Upload your actual project videos
2. Test the forgot password flow
3. Ready for Phase 2: Creative Frontend! 🎨

---

**Need Help?** Check the browser console (F12) for error messages and share them if you're stuck!

