# Track Zone Application

### Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Problems and Solutions](#problems-and-solutions)
- [Lessons Learned](#lessons-learned)

### Overview

Track Zone is a React.js application designed to help users manage clocks and events efficiently. The application comes with a default local clock whose timezone can be updated. Additionally, users can create and manage multiple clocks and events, all while enjoying a streamlined user experience.

### Features
**`Default Local Clock:`**
  - Users can update the timezone of the default clock.

2. Custom Clocks:

- Create, update (timezone and offset), and delete custom clocks.

Event Management:

Add, update, and delete events under any clock.

View all created events on a single page.

Clear all events or search for specific events.

Enhanced User Experience:

Responsive design using Styled Components.

Efficient date handling with Date-fns.

Seamless navigation with React Router DOM.

Technologies Used

React.js: Frontend framework.

Styled Components: For dynamic and reusable styling.

Date-fns: For date and time manipulation.

PropTypes: For type checking React components.

React Router DOM: For client-side routing.

Problems and Solutions

Description

While developing the application, a critical bug surfaced when attempting to update an event. Instead of updating the existing event, the system created a new event. Debugging and resolving this issue took approximately 9 hours.

Root Cause Analysis

The bug was traced to the event ID format. Events were created with a composite ID format of clockId|eventId. However, during the update process, only the eventId was being referenced. This mismatch in the ID format caused the application to treat the update operation as a request to create a new event.

Solution

To resolve the issue, the full composite ID (clockId|eventId) was consistently utilized for both creation and update operations. By aligning the ID format across these functionalities, the bug was effectively eliminated. The updated logic ensures that the correct event is identified and updated without creating duplicates.

Key Steps:

Identified the mismatch in ID handling during the update process.

Updated the logic to use the composite ID (clockId|eventId) for event identification.

Tested the solution across various scenarios to confirm the issue was resolved.

Lessons Learned

Consistent Data Handling: Ensuring data consistency across operations is crucial to avoid bugs.

Composite ID Usage: Composite IDs can be powerful but require careful implementation to prevent mismatches.

Debugging Strategies: Methodical debugging and root cause analysis are key to resolving complex issues.

Testing Importance: Comprehensive testing helps identify and fix edge cases, ensuring reliable application performance.
