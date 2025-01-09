# Track Zone Application

### 📚 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Technologies Used](#-technologies-used)
- [Problems and Solutions](#-problems-and-solutions)
- [Lessons Learned](#-lessons-learned)

[![Demo Video]](./asset/demo.mp4)

### 📄 Overview

Track Zone is a React.js application designed to help users manage clocks and events efficiently. The application comes with a default local clock whose timezone can be updated. Additionally, users can create and manage multiple clocks and events, all while enjoying a streamlined user experience.

### ✨ Features

**Default Local Clock:**

- Users can update the timezone of the default clock.

**Custom Clocks:**

- Create, update (timezone and offset), and delete custom clocks.

**Event Management:**

- Add, update, and delete events under any clock.
- View all created events on a single page.
- Clear all events or search for specific events.

**Enhanced User Experience:**

- Responsive design using Styled Components.
- Efficient date handling with Date-fns.
- Seamless navigation with React Router DOM.

### 💻 Technologies Used

- **React.js:** Frontend framework.
- **Styled Components:** For dynamic and reusable styling.
- **Date-fns:** For date and time manipulation.
- **PropTypes:** For type-checking React components.
- **React Router DOM:** For client-side routing.

### 🛠 Problems and Solutions

**Problem**

While developing the application, an issue arose during the event update process. Instead of modifying the existing event, the system was creating a new one. This behavior was caused by a mismatch in the event identification logic. Events were created using a composite ID format (clockId|eventId), but during updates, only the eventId was being used. As a result, the system could not properly identify the event to be updated, leading it to treat the operation as a request to create a new event.

**Solution**

To address the issue, the application logic was updated to consistently use the composite ID (clockId|eventId) for both creating and updating events. By ensuring that the same format was applied throughout, the system was able to correctly identify and modify existing events without creating duplicates. Extensive testing was performed to verify the fix across different scenarios, ensuring the solution was robust and reliable.

### 📖 Lessons Learned

- **Consistent Data Handling:** Ensuring data consistency across operations is crucial to avoid bugs.

- **Composite ID Usage:** Composite IDs can be powerful but require careful implementation to prevent mismatches.

- **Debugging Strategies:** Methodical debugging and root cause analysis are key to resolving complex issues.

- **Testing Importance:** Comprehensive testing helps identify and fix edge cases, ensuring reliable application performance.
