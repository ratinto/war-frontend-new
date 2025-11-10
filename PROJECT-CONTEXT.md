# WAR (WashingAtRishihood) - Project Context & Architecture

## 📋 Project Overview

**WAR** is a modern web application for managing laundry services at Rishihood University. It's a multi-role platform connecting students with washermen for laundry services.

### Key Details:
- **Type**: Full-stack web application (Frontend)
- **Framework**: Next.js 15.5.6 with React 19.1.0
- **Build Tool**: Turbopack (for faster builds)
- **Styling**: Tailwind CSS 4.1.14
- **Language**: TypeScript
- **Database Integration**: Connected to WAR-Backend-Express API
- **Repository**: https://github.com/ratinto/war

---

## 🏗️ Project Structure

```
war/
├── src/
│   ├── app/                           # Next.js App Router (modern)
│   │   ├── layout.tsx                # Root layout
│   │   ├── page.tsx                  # Home page (routes to Launchpage)
│   │   ├── student/                  # Student routes
│   │   │   ├── StudentSignup1.tsx    # Email & password signup
│   │   │   ├── StudentSignup2.tsx    # Additional student info
│   │   │   ├── StudentSignup3.tsx    # Final confirmation
│   │   │   └── ... (more student pages)
│   │   ├── favicon.ico
│   │   ├── global.css
│   │   └── globals.css
│   │
│   ├── pages/                         # Old Pages Router (legacy)
│   │   ├── _app.tsx                  # App wrapper
│   │   ├── Launchpage.tsx            # Initial welcome page
│   │   ├── Home.tsx                  # Home page
│   │   └── ... (more pages)
│   │
│   ├── components/
│   │   └── ui/                       # Reusable UI components
│   │       ├── button.tsx
│   │       ├── input.tsx
│   │       ├── card.tsx
│   │       └── ... (more UI components)
│   │
│   └── lib/
│       └── utils.ts                  # Utility functions
│
├── public/                            # Static assets
│   ├── logo.webp                     # Rishihood logo
│   ├── next.svg
│   ├── vercel.svg
│   └── ... (other assets)
│
├── package.json                       # Dependencies and scripts
├── next.config.ts                     # Next.js configuration
├── tsconfig.json                      # TypeScript configuration
├── tailwind.config.js                 # Tailwind CSS configuration
├── postcss.config.js                  # PostCSS configuration
├── .eslintrc.mjs                      # ESLint configuration
└── README.md                          # Project documentation
```

---

## 🔄 User Flows

### Student Flow
1. **Launchpage** (`/`) - Welcome screen
2. **StudentSignup1** - Email & password validation
   - Checks for `@rishihood.edu.in` email domain
   - Password matching validation
   - Passes email to next step via URL params

3. **StudentSignup2** - Personal information collection
4. **StudentSignup3** - Confirmation and completion
5. **Dashboard** - Main student interface

### Key Pages

#### Launchpage.tsx
- Welcome screen with brand styling
- Rishihood University branding
- Single "Continue" button to navigate to Home

#### StudentSignup1.tsx
- Email input (with Rishihood domain validation)
- Password creation with visibility toggle
- Confirm password field
- Error handling for validation
- Loading state during submission
- Routes to signup2 with email as query param

---

## 📦 Key Dependencies

### Frontend Frameworks
- **next**: 15.5.6 - React framework with file-based routing
- **react**: 19.1.0 - UI library
- **react-dom**: 19.1.0 - React DOM utilities

### UI & Components
- **@radix-ui/\***: Headless UI components (avatar, dialog, select, etc.)
- **lucide-react**: Icon library
- **react-icons**: Additional icon set
- **class-variance-authority**: CSS utility management
- **clsx**: Conditional CSS class management
- **tailwindcss**: Utility-first CSS framework
- **tailwindcss-animate**: Animation utilities

### Forms & Validation
- **react-hook-form**: Form state management
- **@hookform/resolvers**: Form validation resolvers
- **zod**: TypeScript-first schema validation

### Animations
- **framer-motion**: Animation library

### Development Tools
- **typescript**: Type safety
- **eslint**: Code linting
- **autoprefixer**: CSS prefixing
- **@tailwindcss/postcss**: Tailwind CSS processing

---

## 🎨 Design System & Styling

### Color Scheme
- **Primary Brand**: `#990A2C` (Maroon/Burgundy)
- **Secondary**: `#a30c34` (Darker Maroon)
- **Background**: `#FFF8F6`, `#faf6f3` (Light beige/off-white)
- **Text**: `#333`, `#333333` (Dark gray/black)
- **Borders**: Gray-400, gray-200

### Typography
- **Font**: System fonts (via Tailwind)
- **Headings**: Bold, semibold weights
- **Text Sizes**: Responsive (sm:, md:, lg: breakpoints)

### UI Components Used
- **Button**: Custom styled with hover states
- **Input**: Text and password inputs with validation
- **Card**: Container component for content grouping
- **Icons**: From lucide-react and react-icons

---

## 🔌 API Integration

### Backend Connection
- **Base URL**: `https://war-backend-express.vercel.app/api`
- **Type**: RESTful API
- **Backend**: Express.js with PostgreSQL (Prisma ORM)

### API Endpoints (Expected)
- `/auth/student/signup` - Student registration
- `/auth/student/login` - Student login
- `/orders` - Order management
- `/dashboard` - Dashboard data
- `/student/profile` - Student profile

### Integration Pattern
- Likely using Axios or Fetch API (to be confirmed)
- Environment-based API URL configuration
- JWT token-based authentication

---

## 🚀 Scripts & Commands

### Development
```bash
npm run dev           # Start dev server with Turbopack
npm run build         # Build for production with Turbopack
npm start             # Start production server
npm run lint          # Run ESLint
```

### Features of Development Setup
- **Turbopack**: Faster builds and hot reload
- **Next.js App Router**: Modern routing with `src/app`
- **TypeScript**: Full type safety
- **Tailwind CSS 4**: Latest version with JIT

---

## 📱 Responsive Design

### Breakpoints Used
- **Base (mobile)**: 320px+
- **sm**: 640px+ (tablets)
- **md**: 768px+ (small laptops)
- **lg**: 1024px+

### Responsive Implementation
```tsx
// Example from StudentSignup1.tsx
className="text-2xl sm:text-3xl font-semibold"
// 2xl on mobile, 3xl on tablets and up

width={160} // Desktop size
className="w-28 sm:w-32 md:w-36"
// Different widths for different screen sizes
```

---

## 🔐 Security & Validation

### Email Validation
- Domain check: `@rishihood.edu.in` required
- Prevents external email registrations

### Password Validation
- Confirm password matching
- Visual toggle for password visibility
- Client-side validation (backend validation needed)

### Form Handling
- Prevents form submission without required fields
- Error state management
- Loading state during async operations

---

## 🎯 Current State & TODOs

### Working Features
✅ Landing page with branding
✅ Student signup flow (UI)
✅ Form validation and error handling
✅ Password visibility toggle
✅ Responsive design
✅ Tailwind CSS styling

### To Implement
- [ ] API integration for signup
- [ ] Backend authentication
- [ ] JWT token storage
- [ ] Student dashboard
- [ ] Order management interface
- [ ] Washerman portal
- [ ] Real-time order updates
- [ ] Profile management
- [ ] Error boundary components
- [ ] Loading skeletons

---

## 🔗 Connected Systems

### Backend
- **Repository**: https://github.com/ratinto/WAR-Backend-Express
- **Status**: Deployed on Vercel
- **API**: `https://war-backend-express.vercel.app/api`
- **Database**: PostgreSQL with Prisma ORM

### Related Frontends
- **Admin Panel**: https://github.com/ratinto/WAR-Admin-Panel
- **Washerman Panel**: https://github.com/ratinto/WAR-Washerman-Panel

---

## 🔄 Next.js App Structure Details

### App Router vs Pages Router
This project uses **both**:
- **`src/app/`** - Modern App Router (recommended)
  - File-based routing
  - Server/client component separation
  - Simpler API routes
  
- **`src/pages/`** - Legacy Pages Router
  - Kept for backwards compatibility
  - Contains main pages (Launchpage, Home)
  - Being gradually migrated

### Key Files
- **`layout.tsx`**: Root layout wrapping all pages
- **`page.tsx`**: Home page (renders Launchpage)
- **`student/`**: All student-related routes

---

## 📊 Build Optimization

### Turbopack Benefits
- ~3x faster builds than Webpack
- Incremental computation
- Better caching
- Faster dev server startup

### Bundle Size Considerations
- Tailwind CSS purges unused styles (production)
- React 19 is more efficient
- Code splitting via Next.js dynamic imports

---

## 🧪 Testing & Quality

### Code Quality Tools
- **ESLint**: Code style enforcement
- **TypeScript**: Type checking at compile time
- **Tailwind**: Consistent styling

### Best Practices Applied
- Component-based architecture
- Separation of concerns (UI, pages, lib)
- Type-safe development with TypeScript
- Responsive mobile-first design
- Accessible HTML/ARIA attributes

---

## 📝 File Conventions

### Component Files
- Named exports preferred
- PascalCase for component names
- Props typed with TypeScript interfaces
- `"use client"` for client components in App Router

### Styling
- Tailwind utility classes
- Inline `className` attributes
- No CSS modules (for consistency with Tailwind)
- Responsive modifiers (sm:, md:, lg:)

---

## 🔍 Environment Setup

### Recommended IDE
- VS Code with:
  - Tailwind CSS IntelliSense
  - TypeScript Vue Plugin
  - ESLint extension

### Required Node Version
- Node.js 18+ (Next.js 15 requirement)
- npm 8+ or yarn 3+

---

## 📚 Documentation Links

- [Next.js Docs](https://nextjs.org/docs)
- [React 19 Docs](https://react.dev)
- [Tailwind CSS](https://tailwindcss.com/docs)
- [Radix UI](https://www.radix-ui.com)
- [TypeScript](https://www.typescriptlang.org/docs)

---

## 🎓 Key Learning Points

1. **Next.js App Router**: Modern file-based routing with `src/app`
2. **Server/Client Components**: Clear separation in React 19
3. **Tailwind CSS**: Utility-first approach to styling
4. **TypeScript**: Full type safety across the application
5. **Responsive Design**: Mobile-first approach with breakpoints
6. **Form Validation**: Client-side validation patterns
7. **State Management**: React hooks (useState) for simple state
8. **Navigation**: Next.js router for programmatic navigation

---

## 🚀 Deployment Ready?

**Current Status**: ✅ UI Ready, ❌ Backend Integration Pending

To deploy:
1. Complete API integration
2. Set up environment variables (API_BASE_URL)
3. Create `.env.local`:
   ```
   NEXT_PUBLIC_API_URL=https://war-backend-express.vercel.app/api
   ```
4. Test all flows
5. Deploy to Vercel (Git push auto-deploys)

---

**Last Updated**: November 11, 2025
**Project Status**: Active Development (UI Phase Complete)
