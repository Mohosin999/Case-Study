# Case Study: AI-Powered Resume Builder Application

## 📄 Project Overview

I developed an AI-Powered Resume Builder Application designed to help users create professional resumes with ease and flexibility. Users can customize their resumes by adding sections, colors, and styles. If they choose not to include certain sections, they can simply leave them empty without any issues. Integrated Google Gemini AI to generate personalized resume summaries. Users can select their own color themes for a personalized look and can download their resumes as PDFs and easily share them. The AI provides a "Resume Score" to indicate professionalism and offers suggestions for improvement.

## 💻 Technologies & Tools Used

- React.js
- Context API
- React Router DOM
- Strapi
- Clerk
- Tailwind CSS
- Framer Motion
- Shadcn
- React Quill
- React Web Share
- Axios
- PropTypes

## 🚀 Challenges Faced & Solutions

1. AI Integration Challenges
   As it was my first time working with AI, I faced difficulties integrating the Google Gemini AI into the project:

Problem: The integration process was complicated, and I needed to ensure the AI-generated summaries were relevant and professional.
Solution: I turned to ChatGPT and YouTube tutorials for guidance. With their help, I was able to implement the AI feature, allowing users to generate high-quality summaries for their resumes. 2. Backend Performance Issues
I deployed the backend using Render's free tier, and encountered a significant delay in fetching data from the backend:

Problem: After a day of deployment, fetching resume data took almost two minutes due to the backend going into sleep mode after inactivity.
Solution: I sought advice from ChatGPT, which suggested using UptimeRobot to regularly ping the backend. By configuring it to send requests every 5 minutes, I was able to prevent the backend from sleeping, improving the response time.
Lessons Learned 📚
AI Integration Skills: I gained hands-on experience integrating AI into a practical application. Working with Google Gemini AI taught me how to manage AI data flows, which will be valuable for future projects involving AI.

Backend Optimization: Through the issue with Render's free tier, I learned the importance of managing backend services, especially on free-tier hosting, and how services like UptimeRobot can improve uptime and performance.

Problem-Solving with Resources: Throughout this project, I relied heavily on resources like ChatGPT and YouTube tutorials. These tools allowed me to overcome technical challenges quickly, reinforcing the importance of leveraging online communities and resources.

User-Centered Design: Creating a user-friendly experience was a key focus. Features like resume section customization and AI-powered suggestions were designed to ensure the user could maintain full control over their resume-building process.

Results & Impact 🎯
Enhanced User Experience: Users can now create professional, AI-optimized resumes with ease, with the ability to customize, download, and share them.
Performance Optimization: Backend performance was significantly improved, ensuring fast load times even with free-tier hosting.
Professional AI Suggestions: The AI integration not only generates tailored summaries but also gives a professionalism score and actionable suggestions to improve resumes.
Conclusion 🏁
This project sharpened my skills in AI integration, problem-solving, and backend management, while also providing a valuable tool for users looking to create professional resumes with the help of AI suggestions and scoring.
