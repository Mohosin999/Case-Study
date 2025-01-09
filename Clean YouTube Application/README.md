# Case Study: Clean YouTube Application

## 📚 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Technologies Used](#-technologies-used)
- [Problems and Solutions](#-problems-and-solutions)
- [Lessons Learned](#-lessons-learned)

---

## 📄 Overview

Clean YouTube is a React-based web application designed to enhance your YouTube video-watching experience by providing a clean, ad-free, and distraction-free interface. Users can easily manage playlists, track recent activities, and save their favorites for an enjoyable and seamless experience.

---

## ✨ Features

- **Add Playlists by ID or URL:**  
  Quickly add a playlist by pasting its YouTube URL or Playlist ID.

- **View All Playlist Videos:**  
  Browse all videos from an added playlist in a clean, ad-free interface.

- **Favorites Management:**

  - Add frequently watched playlists to your favorites.
  - Remove playlists from the favorites section.

- **Recent Playlist Tracking:**  
  Automatically tracks and displays recently accessed playlists and videos.

- **Permanent Playlist Deletion:**  
  Delete unwanted playlists permanently to keep your library clean.

---

## 💻 Technologies Used

- **React.js**: For building the frontend interface.
- **React Router DOM**: For handling routing and navigation.
- **React YouTube**: To embed and play YouTube videos seamlessly.
- **YouTube Data API**: To fetch playlist and video data from YouTube.
- **Material UI**: For responsive and modern UI components.
- **EasyPeasy**: For state management.
- **Axios**: For making API requests.
- **PropTypes**: For type-checking React components.

---

## 🛠 Problems and Solutions

### **Issue 01: Low-Resolution Playlist Thumbnails**

**Problem:**  
The playlist thumbnails displayed in low resolution, affecting the visual quality.

**Solution:**  
Replaced the default playlist thumbnail with the thumbnail of the first item in the playlist, which is of higher resolution, ensuring better visuals.

---

### **Issue 02: Duplicate Success Messages When Adding a Playlist**

**Problem:**  
A success message appeared twice:

- Before the playlist was fetched.
- After the playlist was successfully displayed.

**Solution:**  
Implemented `async/await` in the handler function to ensure the success message is displayed only after the playlist fetch operation is completed.

---

### **Issue 03: Excessive API Calls on Playlist Page Visits**

**Problem:**  
Each visit to the playlist page triggered an API call to fetch data, leading to slower performance and unnecessary server load.

**Solution:**  
Cached fetched playlist data in local storage on the first visit. Subsequent visits load the data from local storage, significantly reducing API calls and improving performance.

---

## 📖 Lessons Learned

- **Effective Data Utilization:** Using higher-quality data sources (e.g., item thumbnails) enhances user experience.
- **Asynchronous Handling:** Proper use of `async/await` ensures predictable and user-friendly operations.
- **Performance Optimization:** Caching with local storage reduces server load and improves app responsiveness.
- **User-Centric Design:** A distraction-free and ad-free interface boosts user satisfaction.
