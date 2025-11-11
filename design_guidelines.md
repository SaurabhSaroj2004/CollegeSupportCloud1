# College Support Web App - Design Guidelines

## Design Approach
**Selected System**: Material Design 3 principles adapted for utility-focused service discovery
**Rationale**: Information-dense application requiring clear hierarchy, efficient data scanning, and reliable interaction patterns for both casual browsing and emergency service access.

## Typography System

**Font Family**: 
- Primary: Inter (Google Fonts) for UI and body text
- Headings: Inter Bold/Semibold

**Hierarchy**:
- Hero/Page Titles: text-4xl md:text-5xl font-bold
- Section Headers: text-2xl md:text-3xl font-semibold  
- Card Titles: text-lg font-semibold
- Body Text: text-base leading-relaxed
- Labels/Meta: text-sm text-gray-600
- Buttons: text-sm font-medium uppercase tracking-wide

## Layout System

**Spacing Primitives**: Use Tailwind units of 3, 4, 6, 8, 12, 16
- Component padding: p-4 or p-6
- Section spacing: py-12 md:py-16
- Card gaps: gap-6 or gap-8
- Element margins: mb-4, mb-6, mb-8

**Grid Strategy**:
- Service cards: grid-cols-1 md:grid-cols-2 lg:grid-cols-3
- Filter panels: Sidebar (w-64) + Main content
- Admin dashboard: Two-column layout for forms + preview

**Container Widths**:
- Main content: max-w-7xl mx-auto px-4
- Forms: max-w-md mx-auto
- Listing details: max-w-4xl mx-auto

## Component Library

### Navigation
- Sticky header with logo, search bar (prominent), category filters, profile menu
- Mobile: Hamburger menu with full-screen overlay
- Icons: Heroicons (outline style)

### Authentication Pages
- Centered card layout (max-w-md) with subtle shadow
- Social login buttons prominently displayed
- Form fields with floating labels
- Clear error states with inline validation messages

### Home Page
**Hero Section** (60vh):
- Large hero image showing college campus/student life with overlay gradient
- Centered search bar (large, w-full md:w-2/3) with category dropdown
- Heading: "Find Support Services Near Your Campus"
- Subheading: Quick access stats ("500+ verified services")

**Quick Category Cards** (below hero):
- 4-column grid showing Hospital, Pharmacy, E-Rickshaw, Food
- Each card: Icon (size-12), title, service count
- Hover: subtle lift effect (shadow-lg transition)

**Featured/Recent Listings**: 
- 3-column card grid with service previews
- Each card: Image thumbnail, name, category badge, distance, rating (if available)

### Listings Page
**Layout**: Filter sidebar (desktop) + Results grid
- Filters: Category checkboxes, distance radius, verified only toggle, opening hours
- Results: Service cards with compact info (image, name, phone, address snippet, distance)
- Empty state: Friendly illustration with "No services found" message

### Service Detail Page
**Hero Image**: Full-width service photo (h-64 md:h-96)

**Information Cards** (two-column grid):
- Contact card: Phone (click-to-call button), opening hours, verified badge
- Location card: Address, embedded map placeholder, directions button
- Additional info: Notes, amenities, accessibility info

**Action Buttons**: 
- Primary: "Call Now" (CTA button)
- Secondary: "Get Directions" (outlined button)
- Buttons on image overlays: backdrop-blur-md bg-white/90 (no hover interactions)

### Profile Page
- Avatar upload section with camera icon
- Editable fields in clean form layout
- Recently viewed services list
- Saved favorites grid

### Admin Dashboard
**Layout**: Sidebar navigation + Content area

**Sections**:
- Pending verifications: List view with approve/reject actions
- Add new service: Comprehensive form with image upload
- Analytics cards: Total services, pending reviews, user count (3-column grid)
- Recent activity feed: Timeline-style list

### Form Elements
- Input fields: border rounded-lg with focus:ring-2 states
- Dropdowns: Custom styled with chevron icons
- File upload: Drag-and-drop zone with preview
- Submit buttons: Full-width on mobile, auto-width on desktop

### Cards & Containers
- Service cards: Rounded-xl with shadow-md, hover:shadow-xl
- Category badges: Rounded-full text-xs px-3 py-1
- Status indicators: Verified badge (green), Open/Closed status (red/green dots)

## Interactive Elements

**Buttons**:
- Primary CTA: Solid with ample padding (px-6 py-3)
- Secondary: Outlined with border-2
- Icon buttons: Square aspect ratio, p-2
- All buttons: Built-in hover/active states (no custom overlays needed)

**Search Bar**:
- Large input with left-aligned search icon
- Category dropdown integrated on the right
- Clear button (X) when text present
- Autocomplete suggestions dropdown

**Map Integration**:
- Embedded iframe or map component placeholder
- Markers for service locations
- Distance radius visualization

## Images

**Hero Image** (Home Page):
- Large, vibrant photo of college students or campus environment
- Overlay: Linear gradient from transparent to dark (for text readability)
- Position: Center-center crop

**Service Images**:
- Aspect ratio: 16:9 for listings, 3:2 for detail pages
- Fallback: Category-specific placeholder icons on solid backgrounds

**Profile Avatars**:
- Circular, size-16 in header, size-24 on profile page
- Default: Initials on gradient background

## Accessibility
- All interactive elements: min-h-11 (44px touch target)
- Form labels: Always visible, not placeholder-only
- Color contrast: WCAG AA compliant
- Focus indicators: Prominent ring-2 outline

## Mobile Optimization
- Bottom navigation bar for key actions (Search, Categories, Profile)
- Sticky search bar on listings page
- Touch-friendly spacing (min gap-4 between interactive elements)
- Single-column layouts on mobile with expanded touch targets