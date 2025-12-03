# Folder System Setup Guide

## Step 1: Run Database Migration

1. Go to your Supabase project dashboard
2. Navigate to **SQL Editor**
3. Copy and paste the entire contents of `supabase/folders_schema.sql`
4. Click **Run** to execute the SQL

This will create:
- `folders` table with 4 default folders
- `videos` table linked to folders
- Proper indexes and security policies

## Step 2: Verify Folders Created

After running the migration, you should see 4 folders:
1. Web & Mobile Solutions
2. Web3 & Blockchain
3. Social Media & Growth
4. Brand Identity

## Step 3: Admin Panel Usage

### Access Folder Management:
1. Log in to `/admin/dashboard`
2. You'll see a grid of 4 folders
3. Click any folder to manage its videos

### For Each Folder:
- **Primary Video**: Set one main video that appears on the homepage
- **Other Videos**: Add unlimited additional videos that appear in the gallery

### To Set Primary Video:
1. Click on a folder
2. Upload a video in the "Primary Video" section
3. Click "Set as Primary Video"
4. The video will now appear on the homepage for that folder

### To Add Other Videos:
1. Scroll to "Other Videos" section
2. Upload a video
3. Optionally add a title
4. Click "Add Video"
5. These videos will appear in the horizontal gallery when users click the primary video

## Step 4: Client Side Features

### Homepage:
- Shows all 4 folders stacked vertically
- Each folder displays its primary video
- BOZON logo in top-left (click to refresh/go home)

### Folder Gallery:
- Click any primary video to open the gallery
- All videos for that folder appear horizontally
- Scroll/swipe to navigate between videos
- Click X or BOZON logo to exit
- Keyboard: Arrow keys to navigate, Escape to close

## Troubleshooting

### If folders don't appear:
- Check that the SQL migration ran successfully
- Verify you're logged in as admin
- Check browser console for errors

### If videos don't upload:
- Verify Supabase Storage bucket 'projects' exists
- Check file size (max 100MB)
- Ensure video format is supported (MP4, MOV, WebM)

### WebGL Errors:
- The BackgroundCanvas now has error handling
- If WebGL fails, it falls back to a black background
- This is normal if your GPU/browser doesn't support WebGL

## Next Steps

1. Upload primary videos for each folder
2. Add additional videos to folders
3. Test the client-side gallery experience
4. Customize styling as needed

