# Monaco Rentals - Agents & Workflow

<!-- BEGIN:nextjs-agent-rules -->
# Next.js 16.2.9 - Critical Rules

This version has breaking changes — APIs, conventions, and file structure may all differ from your training data. Read the relevant guide in `node_modules/next/dist/docs/` before writing any code. Heed deprecation notices. Use Turbopack for builds.
<!-- END:nextjs-agent-rules -->

## 🎯 Primary Agent: Monaco Rentals System Manager

**Name:** `MonacoManager`

**Purpose:** Manage Monaco Rentals booking system operations, troubleshoot daily errors, handle user issues, and deploy updates.

**Expertise Areas:**
- ✅ Booking system management (reservations, payments, confirmations)
- ✅ Photo management (uploads via Cloudinary, gallery display)
- ✅ User error handling (404s, 500s, permission issues)
- ✅ Admin dashboard operations (stats, filters, reservation status)
- ✅ Email notifications (Resend API)
- ✅ Database operations (Supabase queries, RLS policies)
- ✅ Deployment & testing
- ✅ Performance monitoring
- ✅ Security & authentication

**Daily Responsibilities:**
1. Monitor error logs from `/admin/dashboard`
2. Handle reservation failures (payment, date conflicts)
3. Resolve photo upload issues (Cloudinary errors)
4. Manage admin authentication & permissions
5. Debug API routes and database queries
6. Assist with FAQ updates and terms changes
7. Handle user complaints & edge cases
8. Deploy code changes & verify functionality

**Common Error Codes to Handle:**
- `PGRST205` - Table doesn't exist (create via migration)
- `PGRST116` - JSON path doesn't exist
- `401` - Unauthorized (admin auth token missing/invalid)
- `42501` - Permission denied (RLS policies)
- `500` - Internal server error (API route issue)
- `400` - Bad request (missing required fields)
- Cloudinary errors - Upload failures, config issues

**Tools Used:**
- Supabase SQL Editor (migrations, debugging)
- Cloudinary Console (photo management, limits)
- Next.js Logs (server errors)
- VS Code Debug (TypeScript errors)
- API testing (Postman, browser console)

**Quick Reference Commands:**
```bash
npm run dev          # Start dev server
npm run build        # Build for production
npm run lint         # Check for errors
npm run start        # Start production server

# Database
Supabase Console → SQL Editor → Run migrations
CREATE TABLE public.rental_images (...)
ALTER TABLE rentals DISABLE ROW LEVEL SECURITY;

# Photos
/admin/photos       # Upload & manage photos
POST /api/admin/upload-photo  # Upload endpoint

# Debugging
localhost:3000/admin/setup    # Table initialization
localhost:3000/admin/login    # Admin login
```

---

## 🔧 Sub-Agents (Supporting)

### Alfonso
Handles booking system logic, database queries, and technical implementation details.

### Explore
Fast codebase search and Q&A for understanding system architecture.

---

## 📋 System Overview

**Tech Stack:**
- Frontend: Next.js 16.2.9 + React 19.2.4 + TypeScript
- Database: Supabase (PostgreSQL)
- Storage: Cloudinary (unlimited photo storage)
- Email: Resend API (transactional)
- Maps: Leaflet + OpenStreetMap
- Styling: TailwindCSS 4
- Auth: localStorage token (admin)

**Key Files:**
- `/app/admin/photos/page.tsx` - Photo management UI
- `/app/api/admin/upload-photo/route.ts` - Cloudinary upload
- `/app/rentals/[id]/page.tsx` - Booking calendar with terms
- `/app/admin/dashboard/page.tsx` - Admin stats & filters
- `/app/faq/page.tsx` - Legal terms (11 sections)
- `.env.local` - Cloudinary credentials

**Database Tables:**
- `rentals` - Properties (T1, T2, T3, T4, Villa)
- `reservations` - Bookings (status: pending/approved/rejected)
- `rental_images` - Photos (category, display_order, is_main)

**Common Issues & Solutions:**
| Issue | Solution |
|-------|----------|
| "Table not found" (PGRST205) | Visit `/admin/setup` and run migration |
| Upload fails (500) | Check `.env.local` has Cloudinary credentials |
| Photos not showing | Verify `rental_images` table exists + RLS enabled |
| Admin can't login | Check localStorage `adminAuth` token |
| Reservation fails | Verify date range doesn't conflict + all fields filled |
| Map not loading | Check Leaflet CSS import in component |
| FAQ not visible | Verify page is published & link in nav works |

---

## 🚀 Deployment Workflow

1. **Code changes** → Test locally
2. **Database changes** → Run migration in Supabase Console
3. **Environment vars** → Update `.env.local` for all secrets
4. **Build & test** → `npm run build` + test routes
5. **Deploy** → Push to Vercel/Netlify or run `npm run start`
6. **Verify** → Check all pages load + admin can login + photos upload

---

## 📞 User Support Framework

**Booking Issues:**
- Check date overlap with existing reservations
- Verify all required fields (name, contact, dates, accept terms)
- Confirm payment processed (if applicable)
- Send confirmation email via Resend

**Photo Issues:**
- Verify Cloudinary account has credits
- Check file size < 100MB
- Try re-uploading with different category
- Clear browser cache & retry

**Admin Issues:**
- Clear localStorage for admin token
- Re-login with password `Admin123!`
- Check `/admin/setup` for missing tables
- View server logs for API errors

**General:**
- Check `/faq` for terms and conditions
- Verify property availability in calendar
- Confirm browser compatibility
- Enable cookies/localStorage for sessions

