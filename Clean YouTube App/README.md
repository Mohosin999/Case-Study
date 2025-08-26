## Title: Clean YouTube – Minimalist & Ad-Free Viewing Experience

## 📄 Overview

Clean YouTube is a React-based web application designed to enhance your YouTube video-watching experience by providing a clean, ad-free, and distraction-free interface. Users can efficiently manage playlists, track recent activities, and save their favorite playlists for a seamless and enjoyable experience.

## ❗ Problem Statement

YouTube’s default interface, while feature-rich, can often be overwhelming and distracting for users. Ads, recommendations, and cluttered layouts disrupt the viewing experience, and managing multiple playlists efficiently can be challenging. Users lack a simple, organized, and distraction-free platform to focus solely on their selected videos.

## 🎯 Objective

To develop a clean, user-friendly web application that provides an ad-free and distraction-free YouTube experience, allowing users to efficiently manage playlists, track recently accessed content, and save favorites for a seamless and enjoyable viewing experience.

## 🛠️ Approach

`Research`

- Based on personal experiences of decreased attention and productivity due to YouTube ads and overly engaging content, the need for a distraction-free viewing experience has been identified.

- Although I could have optimized the process by fetching only a subset of videos initially and then requesting the rest, for now, I chose to fetch all videos at once. This optimization can be implemented later.

`Design & UI/UX`

- Built a clean and intuitive interface using React.js and Material UI.
- Focused on minimalism and responsiveness for all devices.
- Designed playlist, favorites, and recent history sections for easy navigation.

`Implementation`

- Integrated React YouTube to embed videos without ads or clutter.
- Used YouTube Data API to fetch playlist and video data dynamically.
- Managed app state efficiently with EasyPeasy for playlist, favorites, and recent history tracking.
- Implemented playlist addition by URL or ID or by search, favorites management, and permanent deletion functionality.

## 💻 Tech Stack

- React.js, React Router DOM, React YouTube, YouTube Data API, Material UI, EasyPeasy, Axios, PropTypes

## 🔑 Features

- **Add Playlists by ID, URL, or Search:**

  - Users can quickly add a playlist by pasting its YouTube URL or Playlist ID.
  - Users can also search directly within the app to find and add their own playlists.

- **Favorites Management:**

  - Add frequently watched playlists to a favorites section for quick access.
  - Remove playlists from favorites as needed.

- **Recent Playlist Tracking:**

  - Automatically tracks and displays recently accessed playlists and videos for easy revisiting.

- **Permanent Playlist Deletion:**

  - Remove unwanted playlists permanently to keep your library organized and clutter-free.

- **Live Video Search:**

  - Users can search in real-time within a playlist to quickly find a specific video

## ⚡ Challenges & Solutions

### **Issue 01: Duplicate Success Messages When Adding a Playlist**

**Challenge:**  
When adding a new playlist, the success notification was triggered twice:

- Before the playlist was fetched.
- After the playlist was successfully displayed.

This created confusion and an inconsistent user experience.

**Solution:**  
Refactored the playlist addition handler to use `async/await`, ensuring that the success message is displayed only after the playlist fetch operation is completed successfully. This provided users with a clear and accurate confirmation flow.

### **Issue 02: AI Generating Invalid Playlist IDs**

**Challenge:**
Attempted to integrate Google Gemini AI into the app to allow users to search for playlist links or IDs directly. While Gemini’s official website returned valid playlist links during testing, the implementation inside the app produced invalid, AI-generated playlist IDs instead of fetching real ones. This happened because Gemini, when used via API, cannot directly query YouTube’s database and instead generated IDs based on patterns, leading to unusable results.

**Solution:**
Replaced the AI-based search with the YouTube Data API Search endpoint to reliably fetch playlist IDs. This ensured that:

- Users always receive valid playlist IDs directly from YouTube.
- The search functionality became accurate, consistent, and production-ready.
- The app avoided reliance on AI hallucinations and delivered a more dependable user experience.

### **Issue 03: Low-Resolution Playlist Thumbnails**

**Challenge:**  
Default playlist thumbnails were displayed in low resolution, which negatively affected the overall visual quality and user experience.

**Solution:**
Replaced the default playlist thumbnail with the first video’s thumbnail, which provides a higher resolution image. This improved the visual presentation and made the interface more appealing and professional.

### **Issue 04: Excessive API Calls on Playlist Page Visits**

**Challenge:**  
Every time users navigated to the playlist page, a new API request was made to fetch playlist data. This caused:

- Slower performance due to repeated network calls.
- Increased and unnecessary load on the YouTube Data API.

**Solution:**  
Implemented local storage caching for playlist data:

- On the first visit, playlist data is fetched from the API and stored locally.
- On subsequent visits, the app retrieves data directly from local storage instead of making redundant API calls.

This optimization significantly reduced API usage, improved performance, and provided a faster, smoother user experience.

## 📖 Lessons Learned

- **Asynchronous Handling:** Proper use of `async/await` ensures predictable and user-friendly operations.
- **Performance Optimization:** Implementing local storage caching minimized redundant API calls, reduced server load, and delivered faster navigation.
- **User-Centric Design:** Prioritizing an ad-free, distraction-free interface created a more focused and enjoyable user experience.
