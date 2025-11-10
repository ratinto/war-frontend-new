# WAR Frontend - Quick Reference Guide

## 🎯 Project At a Glance

| Aspect | Details |
|--------|---------|
| **Name** | WAR (WashingAtRishihood) |
| **Type** | Next.js Frontend for Laundry Management |
| **Framework** | Next.js 15.5.6 + React 19.1.0 |
| **Build Tool** | Turbopack |
| **Styling** | Tailwind CSS 4.1.14 |
| **Language** | TypeScript 5 |
| **Status** | UI Complete, Backend Integration Pending |
| **Repository** | https://github.com/ratinto/war-frontend-new |

---

## 📁 Quick Navigation

### Key Directories
```
src/
├── app/              # Modern Next.js routing (use this)
│   └── student/      # Student signup pages
├── pages/            # Legacy routing (being migrated)
├── components/       # Reusable UI components
└── lib/              # Utility functions
```

### Important Files
| File | Purpose |
|------|---------|
| `src/app/page.tsx` | Home page (→ Launchpage) |
| `src/pages/Launchpage.tsx` | Welcome screen |
| `src/app/student/StudentSignup1.tsx` | Email/password signup |
| `src/app/layout.tsx` | Root layout |
| `package.json` | Dependencies & scripts |
| `tailwind.config.js` | Tailwind configuration |

---

## 🚀 Common Commands

```bash
# Start development server
npm run dev

# Build for production
npm run build

# Start production server
npm start

# Lint code
npm run lint
```

---

## 🎨 Design System

### Brand Colors
- **Primary**: `#990A2C` (Maroon)
- **Hover**: `#7e0824` (Darker)
- **Background**: `#FFF8F6` (Off-white)
- **Text**: `#333` (Dark gray)

### Spacing & Sizing
- Uses Tailwind's default scale
- Responsive: `sm:`, `md:`, `lg:` prefixes
- Example: `text-2xl sm:text-3xl md:text-4xl`

---

## 📋 Current Features

✅ **Landing Page** - Welcome with branding  
✅ **Student Signup Flow** - Multi-step form  
✅ **Email Validation** - Rishihood domain check  
✅ **Password Management** - With visibility toggle  
✅ **Responsive Design** - Mobile to desktop  
✅ **Error Handling** - Form validation  

---

## 🔌 Backend Integration

### API Endpoint
```
https://war-backend-express.vercel.app/api
```

### Expected Endpoints
```
POST /auth/student/signup
POST /auth/student/login
GET  /student/profile
GET  /orders
POST /orders
PUT  /orders/:id
```

### Setup Required
Create `.env.local`:
```env
NEXT_PUBLIC_API_URL=https://war-backend-express.vercel.app/api
```

---

## 🔐 Student Signup Flow

### Step 1: StudentSignup1
- ✉️ Email field (must be @rishihood.edu.in)
- 🔑 Password field
- ✓ Confirm password field
- Error handling & validation
- Proceeds to Step 2 with email param

### Step 2: StudentSignup2
- (To be implemented)
- Collect additional info (name, bag number, etc.)

### Step 3: StudentSignup3
- (To be implemented)
- Final confirmation & completion

---

## 📱 Responsive Breakpoints

```
Mobile   : 0px (default)
sm       : 640px+ (tablets)
md       : 768px+ (small laptops)
lg       : 1024px+ (desktops)
xl       : 1280px+ (large screens)
```

Example:
```tsx
<div className="text-sm sm:text-base md:text-lg lg:text-xl">
  Responsive text size
</div>
```

---

## 🧩 Component Structure

### UI Components (in `/components/ui/`)
- `button.tsx` - Styled button
- `input.tsx` - Text input
- `card.tsx` - Container component
- `avatar.tsx` - User avatar (Radix UI)
- More from Radix UI library

### Usage Pattern
```tsx
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";

export function MyComponent() {
  return (
    <div>
      <Input placeholder="Enter text" />
      <Button>Click me</Button>
    </div>
  );
}
```

---

## ⚡ Performance Optimization

### Turbopack Benefits
- 3x faster builds than Webpack
- Fast dev server
- Incremental builds

### Next.js Optimization
- Automatic code splitting
- Image optimization (next/image)
- CSS-in-JS (Tailwind) purging

---

## 🧪 Code Quality

### Tools in Place
- ✅ TypeScript - Type safety
- ✅ ESLint - Code linting
- ✅ Tailwind - Consistent styling
- ✅ Next.js - Best practices

### Best Practices
- Component-based architecture
- Type-safe props with TypeScript
- Mobile-first responsive design
- Semantic HTML structure
- Accessibility considerations

---

## 📚 Useful Patterns

### Form Handling
```tsx
const [email, setEmail] = useState("");
const [error, setError] = useState("");

const handleSubmit = (e: React.FormEvent) => {
  e.preventDefault();
  // Validation
  if (!email) {
    setError("Email required");
    return;
  }
  // Submit
};
```

### Navigation
```tsx
import { useRouter } from "next/navigation";

const router = useRouter();
router.push("/student/signup2?email=user@rishihood.edu.in");
```

### Responsive Image
```tsx
import Image from "next/image";

<Image
  src="/logo.webp"
  alt="Logo"
  width={160}
  height={45}
  className="w-28 sm:w-32 md:w-36"
/>
```

---

## 🔗 Related Projects

| Project | Purpose | Status |
|---------|---------|--------|
| WAR-Backend-Express | API server | ✅ Deployed |
| WAR-Admin-Panel | Admin interface | 🚀 Ready |
| WAR-Washerman-Panel | Washerman interface | 🚀 Ready |
| war-frontend (this) | Student interface | 🔨 In Progress |

---

## 🐛 Common Issues & Solutions

### Issue: TypeScript errors
```bash
# Clear Next.js cache
rm -rf .next
npm run build
```

### Issue: Styles not applying
```bash
# Ensure Tailwind is configured
# Check tailwind.config.js includes src/
```

### Issue: Components not found
```bash
# Verify path aliases in tsconfig.json
# "@/*": "./src/*"
```

---

## 📖 Documentation Files

- `PROJECT-CONTEXT.md` - Full architecture & details
- `README.md` - General project info
- This file - Quick reference

---

## ✅ Next Steps (TODO)

- [ ] Connect API endpoints for signup
- [ ] Implement JWT authentication
- [ ] Create student dashboard
- [ ] Build order management UI
- [ ] Add order tracking features
- [ ] Implement washerman portal
- [ ] Set up real-time updates
- [ ] Error boundary components
- [ ] Loading skeletons/states
- [ ] Test on multiple devices

---

## 🚀 Deployment Checklist

- [ ] API integration complete
- [ ] Environment variables set
- [ ] All flows tested locally
- [ ] No console errors/warnings
- [ ] Responsive tested (mobile, tablet, desktop)
- [ ] Performance acceptable
- [ ] Ready for Vercel deployment

---

**Repository**: https://github.com/ratinto/war-frontend-new  
**Last Updated**: November 11, 2025
