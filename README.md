# Creative Portfolio - Admin Panel

A high-end creative portfolio with an immersive frontend and secure admin CMS panel.

## Tech Stack

- **Framework:** Next.js 14 (App Router)
- **Database/Auth/Storage:** Supabase
- **Styling:** Tailwind CSS
- **Animation:** Framer Motion, React Three Fiber
- **Form Handling:** React Hook Form + Zod
- **Icons:** Lucide React

## Setup Instructions

### 1. Install Dependencies

```bash
npm install
```

### 2. Set Up Supabase

1. Create a new project at [supabase.com](https://supabase.com)
2. Go to **SQL Editor** and run the SQL from `supabase/schema.sql`
3. Go to **Storage** and verify the `projects` bucket was created
4. Get your project URL and anon key from **Settings > API**

### 3. Configure Environment Variables

Create a `.env.local` file in the root directory:

```env
NEXT_PUBLIC_SUPABASE_URL=your_supabase_project_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
NEXT_PUBLIC_SITE_URL=http://localhost:3000
```

### 4. Create Your Admin User

1. Go to **Authentication > Users** in Supabase
2. Click **Add User** and create a user with email: `buddhikachandra0001@gmail.com`
3. Set a password (you can change it later via forgot password)

### 5. Run the Development Server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

## Admin Panel

### Access

- **Login:** `/admin/login`
- **Dashboard:** `/admin/dashboard`

### Features

- ✅ Secure authentication with email/password
- ✅ Forgot password (restricted to `buddhikachandra0001@gmail.com`)
- ✅ Project management (Create, Read, Update, Delete)
- ✅ Video upload with progress tracking
- ✅ Drag-and-drop file upload
- ✅ Protected routes via middleware

### Usage

1. Log in at `/admin/login`
2. Click **Add Project** to create a new project
3. Fill in:
   - **Title:** Project name
   - **Description:** Brief explanation
   - **Video:** Upload a video file (30-40s recommended)
4. Click **Create Project**
5. Edit or delete projects from the table

## Database Schema

```sql
projects
├── id (UUID, Primary Key)
├── title (TEXT)
├── description (TEXT)
├── video_url (TEXT)
└── created_at (TIMESTAMP)
```

## Security

- All admin routes are protected by middleware
- Password reset is restricted to the authorized email address
- Row Level Security (RLS) is enabled on the projects table
- Storage policies restrict uploads to authenticated users

## Next Steps

After the admin panel is functional, we'll build:
- Immersive frontend with 3D sea bubbles
- Scroll-triggered video reveals
- Physics-based interactions
- Black & white aesthetic with sea-tone accents

## Project Structure

```
├── app/
│   ├── actions/          # Server actions
│   │   ├── auth.ts       # Authentication actions
│   │   ├── projects.ts   # Project CRUD actions
│   │   └── upload.ts     # Video upload action
│   ├── admin/
│   │   ├── login/        # Login page
│   │   └── dashboard/    # Admin dashboard
│   └── layout.tsx        # Root layout
├── components/
│   └── VideoUpload.tsx   # Video upload component
├── lib/
│   └── supabase/         # Supabase client utilities
├── middleware.ts         # Route protection
└── supabase/
    └── schema.sql        # Database schema
```
