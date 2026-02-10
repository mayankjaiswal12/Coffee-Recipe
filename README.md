# ☕ The Daily Brew | V11.5 Smart Journal

**The Daily Brew** is a professional-grade coffee recipe builder and smart journal.

This project is a **Universal PWA (Progressive Web App)** that runs on any device. It combines a **Step-by-Step Timeline Builder** with a **Smart Journal** that remembers your beans, lets you rate your brews, and instantly search your entire history.

![Status](https://img.shields.io/badge/version-v11.5-blue)
![Hosting](https://img.shields.io/badge/hosting-Netlify-00C7B7)
![Stack](https://img.shields.io/badge/database-Firebase_V11-orange)

## ✨ New in V11.5

* **🧠 Smart Bean Memory:** The app "learns" every coffee bean you use. Next time you brew, it auto-suggests the name (e.g., "Ethiopia Guji") instantly.
* **⭐ Star Ratings:** Rate your brews (1-5 Stars) to remember which recipes were perfect and which need tweaking.
* **🔍 Instant Search:** A powerful search bar filters your history by Bean Name, Method, or Notes in milliseconds.
* **🏗️ Visual Builder:** Create recipes with a drag-and-drop style timeline (Pours, Blooms, Waits).
* **☁️ Universal Sync:** Build on your laptop, brew with your phone.

---

## 🚀 Setup Guide (Start Here)

### Step 1: Fork the Code
1.  **Fork this Repository** to your own GitHub account.

### Step 2: Set Up Firebase
1.  Go to [Firebase Console](https://console.firebase.google.com/) and create a project.
2.  **Create Database:** Build → Firestore Database → Start in **Test Mode**.
3.  **Get Config:** Project Settings ⚙️ → General → Your Apps (`</>`) → Copy `firebaseConfig`.

### Step 3: Connect the Code
1.  Open `index.html` in your repo.
2.  Replace the `const firebaseConfig = { ... }` block with your own keys.
3.  Commit changes.

### Step 4: Deploy to Netlify
1.  Log in to [Netlify](https://www.netlify.com/).
2.  **Add new site** → **Import from GitHub**.
3.  Select your repo and click **Deploy**.

---

## 🛡️ Database Rules (V11.5 Updated)

To support the new **Star Rating** system, update your Firestore Rules to this:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /recipes/{recipeId} {
      allow read, delete: if true;
      
      allow create: if 
         request.resource.data.coffee is number &&
         request.resource.data.name is string &&
         // Allow the new Rating field (optional)
         (request.resource.data.rating is number || request.resource.data.rating == null) &&
         request.resource.data.steps is list;
         
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
