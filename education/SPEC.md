# EduLearn - Online Learning Platform (LMS) Mobile UI

## 1. Project Overview

**Project Name:** EduLearn
**Project Type:** Single-page Android-style WebApp
**Core Functionality:** A mobile-first LMS interface with multiple screens for authentication, course browsing, video learning, live classes, and user profile management.
**Target Users:** Students and learners accessing via mobile browser or WebView

---

## 2. UI/UX Specification

### Layout Structure

**Screen Architecture:**
- Single HTML file with multiple screen sections
- Only one screen visible at a time (display: block/none toggling)
- Fixed bottom navigation bar (visible on all main screens after login)
- Status bar simulation at top

**Screen List:**
1. Splash Screen
2. Login Screen (with OTP UI)
3. Home Dashboard
4. Course List Screen
5. Course Detail Screen
6. Video Player Screen
7. Live Class Screen
8. Profile Screen
9. Admin Panel

**Responsive Breakpoints:**
- Mobile-first: 320px - 480px (primary target)
- Tablet: 481px - 768px
- Max-width container: 480px (centered on larger screens to simulate mobile)

### Visual Design

**Color Palette:**
- Background Dark: `#0F0F1A` (deep navy black)
- Surface: `#1A1A2E` (card backgrounds)
- Surface Elevated: `#252542` (elevated cards)
- Primary: `#6366F1` (indigo)
- Primary Light: `#818CF8` (lighter indigo)
- Secondary: `#EC4899` (pink accent)
- Gradient Start: `#6366F1` (indigo)
- Gradient End: `#8B5CF6` (purple)
- Success: `#10B981` (emerald)
- Warning: `#F59E0B` (amber)
- Error: `#EF4444` (red)
- Text Primary: `#FFFFFF`
- Text Secondary: `#A1A1AA`
- Text Muted: `#71717A`
- Border: `#27272A`

**Typography:**
- Font Family: `'Outfit', sans-serif` (headings), `'DM Sans', sans-serif` (body)
- Heading 1: 28px, weight 700
- Heading 2: 22px, weight 600
- Heading 3: 18px, weight 600
- Body: 14px, weight 400
- Caption: 12px, weight 400
- Line height: 1.5

**Spacing System:**
- Base unit: 4px
- XS: 4px
- SM: 8px
- MD: 16px
- LG: 24px
- XL: 32px
- 2XL: 48px

**Visual Effects:**
- Card shadow: `0 4px 24px rgba(0, 0, 0, 0.3)`
- Elevated shadow: `0 8px 32px rgba(99, 102, 241, 0.15)`
- Border radius (cards): 16px
- Border radius (buttons): 12px
- Border radius (inputs): 10px
- Glassmorphism on nav: `backdrop-filter: blur(12px)`

### Components

**Bottom Navigation Bar:**
- Height: 64px
- Background: rgba(26, 26, 46, 0.95) with blur
- 4 tabs: Home, Courses, Live, Profile
- Active state: Primary color icon + label
- Inactive: Muted text color
- Notification badge on Live tab (red dot)
- Border top: 1px solid rgba(255,255,255,0.05)

**Cards:**
- Background: Surface color
- Border: 1px solid rgba(255,255,255,0.05)
- Padding: 16px
- Hover: Slight scale (1.02) + elevated shadow
- Transition: 0.3s ease

**Buttons:**
- Primary: Gradient background (indigo to purple), white text
- Secondary: Surface background, primary text
- Height: 48px (standard), 56px (large)
- Active state: Scale down (0.98)
- Ripple effect simulation

**Input Fields:**
- Background: Surface elevated
- Border: 1px solid transparent
- Focus border: Primary color
- Placeholder: Text muted
- Height: 52px

**Accordion (Course Detail):**
- Expandable sections for chapters
- Smooth height animation
- Chevron rotation on expand

**Loading Skeletons:**
- Shimmer animation effect
- Matches card/element shapes

---

## 3. Functionality Specification

### Core Features

**Splash Screen:**
- Duration: 2.5 seconds
- Logo with glow animation
- App name fade in
- Auto transition to Login

**Login Screen:**
- Mobile number input (10 digits)
- "Send OTP" button triggers OTP input
- 6-digit OTP input with auto-focus next field
- "Verify" button transitions to Home
- Validation: Show error for invalid input

**Home Dashboard:**
- Welcome message: "Welcome back, [User]!"
- Quick stats row (courses enrolled, hours learned, certificates)
- Horizontal scroll: Enrolled Courses cards
- Horizontal scroll: Upcoming Live Classes
- Horizontal scroll: Recent Videos
- Pull-to-refresh simulation (pull down shows spinner)

**Course List Screen:**
- Search bar at top
- Category filter chips (All, Math, Science, Languages, etc.)
- Course cards in grid (2 columns)
- Each card: Thumbnail, title, instructor, rating, duration

**Course Detail Screen:**
- Hero image/video preview
- Course title and description
- Instructor info
- Progress bar
- Accordion sections:
  - Subject → Chapters → Lessons
- Each lesson: Icon, title, duration, completion status

**Video Player Screen:**
- YouTube iframe (16:9 aspect ratio, responsive)
- Video title below
- Tab: Notes | Resources | Discussion
- Notes: Scrollable text area
- Previous/Next lesson buttons
- Mark as complete button

**Live Class Screen:**
- Class thumbnail/illustration
- Class title
- Date and time display (formatted)
- Instructor name
- Big "Join Live Class" button
- Opens external link (simulated with alert)
- Add to calendar option

**Profile Screen:**
- User avatar (circular, 80px)
- Name, email, phone
- Stats: Courses completed, hours, certificates
- Settings list (notifications, privacy, help)
- Logout button (returns to Login)

**Admin Panel:**
- Accessible via Profile (secret tap on version number)
- Add Course form (title, description, thumbnail URL, category)
- Add Lesson form (select course, chapter, lesson title, video URL)
- Schedule Live Class form (title, date, time, meeting link)
- List of existing items
- Toast notifications on actions

### User Interactions

- Tab navigation: Click bottom nav items
- Screen transitions: GSAP slide left/right
- Card clicks: Navigate to detail screens
- Back button: Return to previous screen (simulated)
- Pull down: Refresh animation on Home

### Data Handling

- All data is dummy/static JavaScript objects
- LocalStorage for: login state, user data
- Session simulation with mock data

### Edge Cases

- Empty states: "No courses enrolled" with illustration
- Loading states: Skeleton loaders (1.5s simulated)
- Error states: Toast messages
- Offline simulation: N/A (frontend only)

---

## 4. Acceptance Criteria

### Visual Checkpoints

- [ ] App displays in mobile-style container (max 480px)
- [ ] Dark theme applied consistently
- [ ] Gradient accents visible on buttons and highlights
- [ ] Cards have proper shadows and rounded corners
- [ ] Bottom nav has glassmorphism effect
- [ ] All screens transition smoothly with GSAP

### Functional Checkpoints

- [ ] Splash shows for 2.5s then transitions
- [ ] Login: Can enter mobile and verify OTP
- [ ] Home: Shows enrolled courses, live classes, videos
- [ ] Course List: Search and filter work
- [ ] Course Detail: Accordion expands/collapses
- [ ] Video Player: YouTube embed responsive
- [ ] Live Class: Button shows external link alert
- [ ] Profile: Shows user info and logout works
- [ ] Admin: Forms accept input and show toast

### Technical Checkpoints

- [ ] Single HTML file, no external dependencies except CDNs
- [ ] GitHub Pages compatible (no server-side code)
- [ ] Works in mobile Chrome/Safari
- [ ] No console errors
- [ ] All CDN links valid

---

## 5. Technical Implementation

### Libraries (CDN)

- Tailwind CSS: https://cdn.tailwindcss.com
- GSAP: https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js
- FontAwesome: https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css
- Google Fonts: Outfit, DM Sans

### Screen IDs

- `#splash-screen`
- `#login-screen`
- `#home-screen`
- `#courses-screen`
- `#course-detail-screen`
- `#video-screen`
- `#live-screen`
- `#profile-screen`
- `#admin-screen`

### Navigation IDs

- `#nav-home`, `#nav-courses`, `#nav-live`, `#nav-profile`

### CSS Custom Properties

```css
--bg-dark: #0F0F1A;
--surface: #1A1A2E;
--surface-elevated: #252542;
--primary: #6366F1;
--primary-light: #818CF8;
--secondary: #EC4899;
--gradient-start: #6366F1;
--gradient-end: #8B5CF6;
--success: #10B981;
--warning: #F59E0B;
--error: #EF4444;
--text-primary: #FFFFFF;
--text-secondary: #A1A1AA;
--text-muted: #71717A;
--border: #27272A;
```
