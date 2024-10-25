# Case Study: AI-Powered Resume Builder Application

## 📄 Project Overview

I developed an AI-Powered Resume Builder Application designed to help users create professional resumes with ease and flexibility. Users can customize their resumes by adding sections, colors, and styles. If they choose not to include certain sections, they can simply leave them empty without any issues. Integrated Google Gemini AI to generate personalized resume summaries. Users can select their own color themes for a personalized look and can download their resumes as PDFs and easily share them. The AI provides a "Resume Score" to indicate professionalism and offers suggestions for improvement. To enhance performance, I implemented lazy loading, and used React hooks (useMemo, useCallback) to optimize rendering and improve responsiveness. I also focused on reusable code by developing modular components.

## 💻 Technologies & Tools Used

- **Frontend:** React.js, Context API, React Router DOM, Tailwind CSS, Framer Motion
- **Backend:** Strapi
- **AI Integration:** Google Gemini AI
- **Authentication:** Clerk
- **Text Editor:** React Quill
- **Others:** React Web Share, PropTypes, Axios

## 🎯 Features

### AI Summary Generation

- Google Gemini AI helps generate resume summaries based on user job title.

### AI Resume Scoring

- AI assigns a "Resume Score" to indicate professionalism and provides suggestions.
- I collected all user input and created a prompt using it. When the user clicks the button, the prompt goes to the AI ​​and generates the results.

## 🚀 Challenges Faced & Solutions

### Problem 1: AI Integration Difficulties

**Context:** As it was my first time working with AI, I faced difficulties integrating the Google Gemini AI into the project.

**Solution:** I turned to ChatGPT and YouTube tutorials for guidance. With their help, I was able to implement the AI feature in my application.

### Problem 2: Backend Latency Due to Free Tier Hosting

**Context:** I deployed the backend using Render's free tier and encountered a significant delay when trying to fetch data after a period of inactivity. It took more than a minute to fetch resume data.

**Solution:** I asked for advice from ChatGPT. Then I got to know the cause of this problem from ChatGPT and that is render puts services in a "sleep mode" after a period of inactivity to conserve resources, which causes a delay when the service is "woken up" for the first request. This is a common behavior with free-tier.

It then suggested using UptimeRobot to ping the backend regularly. By configuring it to send requests every 5 minutes, I was able to prevent the backend from sleeping, improving the response time.

## 📚 Lessons Learned

AI Integration Skills: I gained hands-on experience integrating AI into a practical application. Working with Google Gemini AI taught me how to manage AI data flows, which will be valuable for future projects involving AI.

Backend Optimization: Through the issue with Render's free tier, I learned the importance of managing backend services, especially on free-tier hosting, and how services like UptimeRobot can improve uptime and performance.

Problem-Solving with Resources: Throughout this project, I relied heavily on resources like ChatGPT and YouTube tutorials. These tools allowed me to overcome technical challenges quickly, reinforcing the importance of leveraging online communities and resources.

User-Centered Design: Creating a user-friendly experience was a key focus. Features like resume section customization and AI-powered suggestions were designed to ensure the user could maintain full control over their resume-building process.
