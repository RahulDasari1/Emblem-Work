# 💼 Emblem Work Job Board

### *Where Purpose Finds Its Profession*

**(Realtime Database Version)**

This project is a single-page, real-time job board application designed to connect users with mission-driven careers focused on positive environmental, social, and governance (ESG) impact. The application uses **Firebase Realtime Database (RTDB)** for immediate, live updates of job listings.

<img width="1885" height="922" alt="image" src="https://github.com/user-attachments/assets/c27bb942-4298-4fb8-8ae3-62cde363f134" />


The entire application—HTML, Tailwind CSS, and JavaScript/Firebase logic—is self-contained within a single `index.html` file, making it easy to deploy and highly portable.

---

## ✨ Features

* **Real-Time Data**
  Live job listing updates using Firebase RTDB with the `onValue` listener.

* **Authentication**
  Secured operations using Firebase Authentication (anonymous or custom token).

* **Job Filtering**
  Search and filter jobs by title, company, tags, or location.

* **Responsive Design**
  Fully responsive UI powered by Tailwind CSS.

* **Data Seeding**
  Automatically seeds mock data into RTDB on first load if the database is empty.

* **Built-in Diagnostics**
  Debug panel included for monitoring Firebase connection and authentication status.

---

## 💻 Technology Stack

**Frontend:** HTML5, Vanilla JavaScript (ES6+), Tailwind CSS (CDN)
**Database:** Firebase Realtime Database (RTDB)
**Authentication:** Firebase Authentication

---

## 🛠 Setup and Installation

### 1. **Critical Firebase Configuration Step**

This application requires a valid Firebase configuration object. If you see an `auth/invalid-api-key` error, your configuration is incomplete.

You must manually update the `firebaseConfig` object inside the `<script type="module">` section of `index.html`.

Locate and update:

```js
// ... inside index.html <script type="module">
// =========================================================================
// !!! CRITICAL: PASTE YOUR FIREBASE WEB APP CONFIG HERE TO FIX API KEY ERROR !!!
// =========================================================================

/*
const firebaseConfig = {
    apiKey: "YOUR_ACTUAL_API_KEY", // <--- REPLACE THIS WITH YOUR KEY
    authDomain: "your-project-id.firebaseapp.com",
    databaseURL: "https://your-project-id.firebaseio.com",
    projectId: "your-project-id",
    // ... other properties
};
*/

const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : {};
// ...
```

Be sure to replace all placeholder values with your real Firebase project credentials.

---

### 2. **Running the Application**

Since this is a self-contained HTML file:

1. Save the file as `index.html`.
2. Open it directly in any modern web browser.

The script will automatically:

* Initialize Firebase
* Authenticate the user
* Seed the database (if empty)
* Listen for real-time updates

---

## 🗄 Data Structure (Firebase Realtime Database)

All job listings are stored under:

```
/artifacts/{__app_id}/public/jobs/{jobId}
```

Each job document contains:

| Field         | Type             | Description                                         |
| ------------- | ---------------- | --------------------------------------------------- |
| `id`          | String           | Unique job ID (RTDB key).                           |
| `title`       | String           | Job title (e.g., “Senior Sustainability Analyst”).  |
| `company`     | String           | Company name.                                       |
| `location`    | String           | Location or “Remote”.                               |
| `type`        | String           | Employment type (e.g., “Full-time”).                |
| `description` | String           | Detailed job description.                           |
| `tags`        | Array of Strings | Keywords for filtering (e.g., `["ESG", "Remote"]`). |

---

## 🎨 Styling

The application uses **Tailwind CSS** via CDN for all styling.

Additional custom styles (such as background images and overlays) are defined within the `<style>` block inside `index.html`.
