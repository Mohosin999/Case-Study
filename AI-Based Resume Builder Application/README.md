# Case Study: FullStack AI Resume Builder App - Next.js

## 📚 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Technology Stack](#-technology-stack)
- [Problems and Solutions](#-problems-and-solutions)
- [Lessons Learned](#-lessons-learned)

---

## 📄 Overview

I developed a full-stack AI-powered Resume Builder using Next.js with built-in server-side capabilities. It enables users to create professional resumes effortlessly with world-class formats and complete CRUD support. Integrated with Google Gemini AI, the app generates professional descriptions and intelligent skill suggestions based on the resume title. Designed to help beginners overcome formatting and layout challenges, it auto-structures resumes for a polished look. Users can instantly download their resumes as PDFs, ready for job applications.

---

## ✨ Features

- **Customizable Resume Sections:**

  - Users can add, edit, or delete any resume section.
  - Support for multiple entries within a section.
  - Edit or delete specific entries.

- **AI Description Generation:**

  - Generate professional resume descriptions using Google Gemini AI.

- **AI Skill Suggestions:**

  - Provides intelligent skill suggestions based on the user’s resume title.

- **Download as PDF:**
  - Users can download their resume in a PDF format.

---

## 💻 Technology Stack

**Frontend** - Next.js 14, TypeScript, Tailwind CSS, Shadcn UI, Framer Motion, React Icons

**Backend** - Next.js API Routes, Prisma ORM, PostgreSQL (Neon Database)

**AI Integration** - Google Gemini AI

**Others** - Clerk (Authentication), React Toastify

---

## 🛠 Problems and Solutions

### **Issue 01: Next.js 15 Typed Routes Bug**

**Problem:**  
While upgrading my full-stack AI Resume Builder to Next.js 15 (App Router), I encountered a critical TypeScript error during production builds. Despite correctly typing dynamic route params and trying all recommended fixes (typedRoutes config, generateStaticParams, async/await adjustments), the build kept failing with:

```
Type '{ params: { id: string } }' does not satisfy the constraint 'PageProps'.
Type '{ id: string }' is missing the following properties from type 'Promise<any>': then, catch, finally, [Symbol.toStringTag]
```

The root cause was Next.js 15’s experimental typed routes feature. It enforced strict type checking on dynamic route parameters in a way that was broken for some cases, expecting params to behave like Promises unnecessarily.

**Solution:**

- Downgraded from Next.js 15 to 14.2.x for stability.
- Adjusted minor configurations in next.config.js and font imports.
- Production builds ran successfully, and the app now works flawlessly.

### **Issue 02: Mobile Print Styles Showing Instead of Desktop Styles**

**Problem:**
After making the resume responsive for mobile, printing the resume caused it to use mobile-optimized styles (stacked layouts, centered text) instead of the cleaner desktop layout. This resulted in unprofessional print output, as desktop styles (side-by-side sections, proper alignment) are much better for printed resumes.

**Solution:**

- Leveraged Tailwind CSS’s `print:` modifier to enforce desktop-specific styles during printing.
- Updated the layout code:

`Before (Problematic Code):`

```
<div className="flex flex-col lg:flex-row">
  <!-- Content -->
</div>
```

Printed layout: `flex-col` (mobile stacked layout)

`After (Fixed Code):`

```
<div className="flex flex-col lg:flex-row print:!flex-row">
  <!-- Content -->
</div>
```

### **Issue 03: Managing Reusable Styles in Tailwind CSS**

**Problem:**
While building the app’s design, I felt exhausted from repeatedly writing the same Tailwind utility classes across multiple components. This repetition made the JSX messy and harder to maintain.

**Solution:**

- Used Tailwind CSS’s @apply directive inside globals.css to create reusable, clean styles.
- Example: instead of repeating className="bg-gray-100 p-4 rounded-lg shadow", I defined a reusable class in CSS:

```
.card {
  @apply bg-gray-100 p-4 rounded-lg shadow;
}
```

Now components can simply use `className="card"`.

`Benefits:`

- Avoids repeating utility classes (DRY principle)
- Easier to maintain and update styles globally
- Cleaner JSX, making the project more organized and maintainable

---

## 📖 Lessons Learned

<!--
- **Global Styles Impact:** Styles in the global CSS file play a crucial role in ensuring visual consistency across different components.

- **AI Integration:** Implementing AI features can significantly enhance user experience but requires patience and thorough research.

- **Reusable Components:** Modular and reusable components streamline development and improve maintainability.

- **Performance Optimization:** Techniques like lazy loading and optimized rendering improve responsiveness and ensure a seamless user experience. -->
