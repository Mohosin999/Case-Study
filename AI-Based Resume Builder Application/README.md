<!-- # Case Study: FullStack AI-Powered Resume Builder App - Next.js

## 📚 Table of Contents

- [Title](#-title)
- [Overview](#-overview)
- [Features](#-features)
- [Technology Stack](#-technology-stack)
- [Problems and Solutions](#-problems-and-solutions)
- [Lessons Learned](#-lessons-learned)

--- -->

## Title: AI-Powered Resume Builder - Enhancing Job Seekers’ Efficiency and Professionalism

## 📄 Overview

I developed a full-stack AI-powered Resume Builder using Next.js with built-in server-side capabilities. It enables users to create professional resumes effortlessly with professional formats and complete CRUD support. Integrated with Google Gemini AI, the app generates professional descriptions and intelligent skill suggestions based on the resume title. Designed to help users overcome formatting and layout challenges, it auto-structures resumes for a polished look. Users can instantly download their resumes as PDFs, ready for job applications.

---

## ⚠️ Problem Statement

I have often seen candidates, especially new job seekers, encounter formatting issues while creating resumes and fail to create resumes that meet global professional standards. They do not understand what a resume should look like and which sections to focus on. Observing this challenge, AI Resume Builder was created to help users create resumes quickly and efficiently, eliminating the need to worry about formatting or professional presentation.

## 🛠️ Approach

`Research`

- Studied existing resume standards and took professional advice from a core team member of one of the world’s largest tech companies to ensure industry relevance.

`Design`

- Built a **user-centric interface** with structured sections for dashboard, personal details, summary, experience, project, education, and skills.
- Followed **UI/UX best practices** to ensure accessibility, responsive layouts, and intuitive navigation across devices.
- Developed **real-time preview and print-ready modes**, enabling users to instantly view and export professional resumes.
- Incorporated **animations and micro-interactions** (Framer Motion) to create a smooth and engaging user experience.
- Applied **global reusable styles** with Tailwind’s `@apply` directive, ensuring consistency and reducing repetitive code.

---

### **AI Integration 🤖**

- Integrated **Google Gemini AI** to generate professional, concise, and ATS-friendly resume summaries.
- Key AI contributions include:
  - Generating context-aware professional descriptions.
  - Suggesting impactful phrasing for skills and experience.
  - Providing multiple AI-generated suggestion cards for user selection.
- Implemented **prompt engineering** to avoid overly generic outputs and ensured **content persistence** with local state + context.
- Optimized AI responses by switching from `gemini-2.5-pro` to **`gemini-1.5-flash`**, reducing response time to 1–2 seconds.
- Maintained user control by allowing **manual edits** after AI suggestions.

- `Tech Stack`

  - Frontend: Next.js 14, TypeScript, Tailwind CSS, Shadcn UI, Framer Motion, React Icons
  - Backend: Next.js API Routes, Prisma ORM, PostgreSQL (Neon Database)
  - AI Integration: Google Gemini AI for resume optimization and content generation
  - Authentication & Others: Clerk (user authentication), React Toastify (real-time notifications)

## 🔑 Features

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

## ⚡ Challenges & Solutions

### **Issue 01: Next.js 15 Typed Routes Bug**

**Challenge:**  
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

**Challenge:**
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

**Challenge:**
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

### **Issue 04: Slow and Unreliable AI Resume Description Generation**

**Challenge:**
The AI-powered resume description sometimes returned empty results and was slow, taking several seconds. TypeScript also reported errors because response.text is a getter property, not a function.

**Solution:**
After discussing the issue with ChatGPT, I implemented the recommended improvements: I switched from `gemini-2.5-pro` to the faster `gemini-1.5-flash`, removed unnecessary tools, and simplified the config. I also updated the code to safely access `response.text` and added a fallback for empty outputs. Testing and experimenting with SDK settings helped identify the optimal configuration. Description now generate quickly and reliably in 1–2 seconds, improving user experience.

---

## 📖 Lessons Learned

- **Global Styles Impact:** Centralized styles in `globals.css` improved consistency and maintainability.
- **AI Integration:** Building AI features requires patience and iteration — tuning prompts, selecting the right model, and optimizing response speed.
- **Reusable Components:** A modular approach simplified development and improved code reusability.
- **Performance Optimization:** Techniques like lazy loading and optimized rendering improved responsiveness and user experience.
- **Debugging Mindset:** Encountering bugs (like typed routes in Next.js 15 and print layout issues) reinforced the importance of deep debugging and fallback strategies.

---

### 🧪 Test Code Journey

- Initially, I attempted to set up a test environment twice but quit due to recurring errors.
- Every fix seemed to trigger a new error, leading to frustration.
- Before trying a third time, I **revised my test knowledge**, re-learned testing classes, and analyzed error patterns.
- On my **third attempt**, I successfully configured the test environment, wrote meaningful test cases, and understood the purpose of each test.
- This experience taught me the importance of **perseverance, structured learning, and error analysis** when working with testing frameworks.
