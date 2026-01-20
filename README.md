# ☕ The Daily Brew | Universal Coffee Recipe Keeper

**The Daily Brew** is a minimalist, cloud-synced web application designed to track, refine, and standardize your coffee brewing recipes.

Unlike static note-taking apps, this project is a **Universal PWA (Progressive Web App)**. It runs on any device (iOS, Android, Desktop), installs to your home screen, and syncs your recipes instantly across all devices using a personal Google Firebase database.

![Status](https://img.shields.io/badge/status-live-success.svg)
![Hosting](https://img.shields.io/badge/hosting-Netlify-00C7B7)
![Stack](https://img.shields.io/badge/backend-Firebase-orange)
![License](https://img.shields.io/badge/license-MIT-blue.svg)

## ✨ Features

* **☁️ Universal Cloud Sync:** Write a recipe on your iPhone in the kitchen; see it instantly on your Laptop.
* **📱 Native App Experience:** Optimized for iOS/Android. Add it to your Home Screen to remove browser bars and run it full-screen.
* **🧠 Smart Input Fields:** "Method" and "Process" fields use smart suggestions (Datalist), allowing you to pick standard options (V60, Washed) or type custom ones (Siphon, Thermal Shock).
* **⚖️ Live Ratio Calculator:** Automatically calculates the Coffee-to-Water ratio (e.g., `1:16.5`) in real-time as you type.
* **🛡️ Secure & Private:** You own your data. It lives in your personal Firebase instance, locked strictly to your Netlify domain.
* **💸 Zero Cost:** Architected to run entirely on Netlify's free tier and the Firebase Spark (Free) plan.

---

## 🚀 Quick Setup Guide

Because this app uses a private database, you cannot just "use" my link to store your personal recipes. You need to create your own instance.

**Follow these 3 steps to deploy your own personal version in under 5 minutes.**

### Step 1: Fork the Repository
1.  Click the **Fork** button (top-right of this page).
2.  This creates an exact copy of the code in your own GitHub account.

### Step 2: Create Your Database (Firebase)
1.  Go to the [Firebase Console](https://console.firebase.google.com/) and log in.
2.  Click **Add project** (name it `coffee-app`).
3.  **Create the Database:**
    * Go to **Build** → **Firestore Database**.
    * Click **Create Database** → Select **Start in Test Mode**.
    * Choose a location near you and click **Enable**.
4.  **Get the Config:**
    * Click the **Gear Icon ⚙️** (Project Settings).
    * Scroll to "Your apps" → Click the **Web (`</>`)** icon.
    * Copy the `firebaseConfig` code block.
5.  **Connect the Code:**
    * Open `index.html` in your GitHub repo.
    * Replace the existing `const firebaseConfig = { ... }` with your new code.
    * Commit changes.

### Step 3: Go Live with Netlify
1.  Go to [Netlify.com](https://www.netlify.com/) and sign up with GitHub.
2.  Click **"Add new site"** → **"Import from an existing project"**.
3.  Select **GitHub** and choose your `Coffee-Recipe` repository.
4.  Click **Deploy Site**.
5.  *Optional:* Go to **Site Settings > Change site name** to get a cleaner URL (e.g., `my-daily-brew.netlify.app`).

---

## 🔒 Security Configuration (Critical)

To prevent unauthorized use of your database quota, you **must** lock your API key to your specific Netlify domain.

1.  Go to [Google Cloud Credentials](https://console.cloud.google.com/apis/credentials).
2.  Select your project and click the **Pencil Icon** (Edit) on your API Key.
3.  Under **Application restrictions**, choose **Websites**.
4.  Add your Netlify URL with a wildcard:
    ```text
    [https://your-site-name.netlify.app/](https://your-site-name.netlify.app/)*
    ```
5.  Click **Save**.

> **Note:** Security changes may take up to 5 minutes to take effect.

---

## 📱 Installation on Mobile

To get the full "App" experience without an address bar:

### iOS (iPhone)
1.  Open your Netlify link in **Safari**.
2.  Tap the **Share** button (Square with arrow).
3.  Scroll down and tap **"Add to Home Screen"**.

### Android
1.  Open your Netlify link in **Chrome**.
2.  Tap the **Menu** (three dots).
3.  Tap **"Add to Home Screen"** or **"Install App"**.

---

## 🛠️ Tech Stack

* **Frontend:** HTML5, CSS3, Vanilla JavaScript (ES6 Modules)
* **Database:** Google Cloud Firestore (NoSQL)
* **Hosting:** Netlify (Global CDN)

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.
