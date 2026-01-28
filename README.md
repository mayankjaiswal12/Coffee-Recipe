# ☕ The Daily Brew | V10.1 Pro Builder

**The Daily Brew** is a professional-grade coffee recipe builder and library.

This project is a **Universal PWA (Progressive Web App)** that runs on any device (iOS, Android, Desktop). It features a **Step-by-Step Timeline Builder** (inspired by apps like Aramse) to construct complex brew recipes with precise timing, color-coded stages, and auto-calculated ratios—all synced to your personal cloud.

![Status](https://img.shields.io/badge/version-v10.1-blue)
![Hosting](https://img.shields.io/badge/hosting-Netlify-00C7B7)
![Stack](https://img.shields.io/badge/database-Firebase_V10-orange)
![License](https://img.shields.io/badge/license-MIT-green)

---

## ✨ Features

* **🏗️ Visual Recipe Builder:** Create recipes step-by-step (e.g., "Bloom 0:00 → 0:45", "Pour to 150g").
* **🎨 Color-Coded Timeline:** Visual bars help you distinguish between Pours (Blue), Agitation (Red), and Waits (Gray).
* **📚 Recipe Library:** Browse your entire collection of saved recipes with a single click.
* **🧠 Smart Inputs:** Auto-calculates your Coffee:Water ratio and offers smart suggestions for Methods (V60, Aeropress, etc.).
* **☁️ Universal Sync:** Build on your laptop, brew with your phone. Data lives in your private Google Firestore.
* **🔒 Secure:** Your API Key is locked to your specific domain, preventing unauthorized use.

---

## 🚀 Setup Guide (Start Here)

Since this app uses a private database, you cannot just "use" a public link to store your personal recipes. **Follow these 4 steps to deploy your own instance in under 10 minutes.**

### Step 1: Get the Code
1.  **Fork this Repository:** Click the **Fork** button (top-right of this page) to create a copy in your own GitHub account.
2.  (Optional) Clone it to your local machine if you want to edit it locally, but you can also edit directly in GitHub.

### Step 2: Set Up Firebase (Your Database)
1.  Go to the [Firebase Console](https://console.firebase.google.com/) and log in with your Google account.
2.  **Create a Project:** Click **Add project** (name it something like `my-coffee-app`).
3.  **Create the Database:**
    * On the left sidebar, go to **Build** → **Firestore Database**.
    * Click **Create Database**.
    * Select **Start in Test Mode** (we will secure it later).
    * Choose a location close to you (e.g., `asia-south1` or `us-central1`).
    * Click **Enable**.
4.  **Get Your Config Code:**
    * Click the **Gear Icon ⚙️** (Project Settings) at the top left.
    * Scroll down to "Your apps".
    * Click the **`</>` (Web)** icon.
    * Give the app a nickname (e.g., "Web App") and click **Register app**.
    * **COPY** the `firebaseConfig` code block (the part between `const firebaseConfig = { ... };`).

### Step 3: Connect the Code
1.  Open the `index.html` file in your GitHub repository.
2.  Scroll down to the bottom script section.
3.  **Replace** the placeholder config with the code you just copied from Firebase.
    ```javascript
    // REPLACE THIS PART
    const firebaseConfig = {
        apiKey: "PASTE_YOUR_API_KEY_HERE",
        authDomain: "coffee-database-92533.firebaseapp.com",
        projectId: "coffee-database-92533",
        storageBucket: "coffee-database-92533.firebasestorage.app",
        messagingSenderId: "788577377347",
        appId: "1:788577377347:web:3ed7f39df2bfb7828348f6"
    };
    ```
4.  **Commit** your changes.

### Step 4: Deploy to Netlify (Free Hosting)
1.  Go to [Netlify.com](https://www.netlify.com/) and sign up (log in with GitHub).
2.  Click **"Add new site"** → **"Import from an existing project"**.
3.  Select **GitHub**.
4.  Search for and select your `Coffee-Recipe` repository.
5.  Click **Deploy Site**.
6.  Netlify will give you a live URL (e.g., `fast-coffee-123.netlify.app`).
    * *Tip: Go to Site Settings > Change site name to make it look nicer.*

---

## 🛡️ Important: Security Rules

Now that your app is live, you must configure the database to accept your new V10 data format.

1.  Go back to the [Firebase Console](https://console.firebase.google.com/).
2.  Go to **Build** → **Firestore Database** → **Rules** tab.
3.  **Delete everything** and paste these exact rules:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /recipes/{recipeId} {
      // Allow anyone to read and delete recipes
      allow read, delete: if true;
      
      // Only allow creation if the data format is correct (V10 Strict Mode)
      allow create: if 
         request.resource.data.coffee is number &&
         request.resource.data.water is number &&
         request.resource.data.name is string &&
         request.resource.data.steps is list; // Required for the timeline builder
         
      // Block edits (Updates) to keep it simple
      allow update: if false;
    }
  }
}
```

## 🔒 Final Step: API Key Lockdown

To prevent others from using your database quota, lock your API key to your Netlify site.

1. Go to [Google Cloud Credentials](https://console.cloud.google.com/apis/credentials).
2. Find the API Key used in your project and click the **Pencil Icon** (Edit).
3. Under **Application restrictions**, choose **Websites**.
4. Add your Netlify URL with a wildcard:
   ```text
   https://your-site-name.netlify.app/*
   ```
5. Click Save

Congratulations! You now have a secure, professional, and private coffee recipe app.

📱 Installation on Mobile
To install as a native app (PWA):

iOS: Open in Safari → Share Icon → "Add to Home Screen".

Android: Open in Chrome → Menu (3 dots) → "Install App" or "Add to Home Screen".
