# Database Migration Instructions

## Step 1: Run the SQL Migration

To fix the "category column not found" error, you need to run the SQL migration in Supabase:

1. Go to your Supabase project: https://supabase.com/dashboard
2. Navigate to **SQL Editor** (left sidebar)
3. Click **"New query"**
4. Copy and paste the following SQL:

```sql
-- Add category column to projects table
ALTER TABLE projects 
ADD COLUMN IF NOT EXISTS category TEXT;

-- Set default value for existing projects
UPDATE projects 
SET category = 'Web & Mobile Solutions' 
WHERE category IS NULL;

-- Make it NOT NULL after setting defaults
ALTER TABLE projects 
ALTER COLUMN category SET NOT NULL;

-- Add a check constraint to ensure only valid categories are allowed
ALTER TABLE projects 
ADD CONSTRAINT check_category 
CHECK (category IN (
  'Web & Mobile Solutions',
  'Web3 & Blockchain',
  'Social Media & Growth',
  'Brand Identity'
));
```

5. Click **"Run"** (or press Ctrl+Enter)
6. You should see "Success. No rows returned"

## Step 2: Verify Migration

After running the migration:
1. Go to **Table Editor** in Supabase
2. Select the `projects` table
3. Verify that the `category` column exists
4. Check that existing projects have a category assigned

## Step 3: Test

1. Go to your admin panel: `/admin/dashboard`
2. Try adding a new project with a category
3. The error should be gone!

---

**Note:** The code has been updated to handle missing category column gracefully, but you should still run the migration for full functionality.

