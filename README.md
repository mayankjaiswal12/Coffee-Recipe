# ☕ The Daily Brew | Universal Coffee Recipe Keeper

**The Daily Brew** is a minimalist, cloud-synced web application designed to track, refine, and standardize your coffee brewing recipes.

Unlike static note-taking apps, this project is a **Universal PWA (Progressive Web App)**. It runs on any device (iOS, Android, Desktop), installs to your home screen, and syncs your recipes instantly across all devices using a personal Google Firebase database.

![Project Status](https://img.shields.io/badge/status-live-success.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Stack](https://img.shields.io/badge/backend-Firebase-orange)

## ✨ Features

* **☁️ Universal Cloud Sync:** Write a recipe on your iPhone in the kitchen; see it instantly on your Laptop.
* **📱 Native App Experience:** Optimized for iOS/Android. Add it to your Home Screen to remove browser bars and run it full-screen.
* **⚖️ Live Ratio Calculator:** Automatically calculates the Coffee-to-Water ratio (e.g., `1:16.5`) in real-time as you input grams.
* **⚙️ Equipment Manager:** Built-in support for V60, Aeropress, French Press, etc., with options to add custom brew methods.
* **🛡️ Secure & Private:** You own your data. It lives in your personal Firebase instance, not on a shared public server.
* **💸 Zero Cost:** Architected to run entirely on the GitHub Pages free tier and Firebase Spark (Free) plan.

---

## 🚀 How to Setup Your Own (The "Fork" Method)

Because this app uses a private database, you cannot just "use" my link to store your personal recipes. You need to create your own instance.

**Follow these 4 steps to deploy your own personal version in under 10 minutes.**

### Step 1: Fork the Repository
1.  Look at the top-right corner of this page.
2.  Click the **Fork** button.
3.  This creates an exact copy of the code in your own GitHub account.

### Step 2: Create Your Database (Firebase)
1.  Go to the [Firebase Console](https://console.firebase.google.com/) and log in with your Google account.
2.  Click **Add project** and give it a name (e.g., `my-coffee-app`).
3.  **Disable Google Analytics** (you don't need it) and click **Create Project**.
4.  **Create the Database:**
    * On the left sidebar, go to **Build** → **Firestore Database**.
    * Click **Create Database**.
    * Select **Start in Test Mode** (this is easiest for setup).
    * Choose a location near you (e.g., `asia-south1` or `us-central`).
    * Click **Enable**.

### Step 3: Connect the Code
1.  **Get your Keys:**
    * In Firebase, click the **Gear Icon ⚙️** (Project Settings).
    * Scroll down to "Your apps" and click the **Web (`</>`)** icon.
    * Register the app (name it "Daily Brew").
    * Copy the `firebaseConfig` object (the code inside `const firebaseConfig = { ... }`).
2.  **Paste into GitHub:**
    * Go to your forked GitHub repository.
    * Open the `index.html` file and click the **Pencil Icon (Edit)**.
    * Scroll down to around line 170 where it says `// --- PASTE YOUR FIREBASE CONFIG HERE ---`.
    * Replace the placeholder config with your own code.
    * Click **Commit changes**.

### Step 4: Go Live!
1.  In your GitHub repository, click **Settings** (top menu).
2.  On the left sidebar, click **Pages**.
3.  Under **Branch**, select `main` (or `master`) and click **Save**.
4.  Wait 60 seconds and refresh the page. You will see your live URL (e.g., `https://yourname.github.io/Coffee-Recipe/`).

---

## 🔒 Security Best Practices

Since your API key is visible in the code, you should lock it to your website to prevent others from using your quota.

1.  Go to [Google Cloud Credentials](https://console.cloud.google.com/apis/credentials).
2.  Select your project.
3.  Click the **Edit (Pencil)** icon next to your Browser Key.
4.  Under **Application restrictions**, choose **Websites**.
5.  Add your URL: `https://yourname.github.io/*`.
6.  Click **Save**.

Now, your key will only work when the app is opened from your specific website.

---

## 📱 Installation on iPhone / Android

To get the full app experience:

1.  Open your new website link in **Safari** (iOS) or **Chrome** (Android).
2.  Tap the **Share** button (iOS) or **Menu** dots (Android).
3.  Select **"Add to Home Screen"**.
4.  Launch the app from the new icon on your home screen.

---

## 🛠️ Tech Stack

* **Frontend:** HTML5, CSS3, Vanilla JavaScript (ES6 Modules).
* **Database:** Google Cloud Firestore (NoSQL).
* **Hosting:** GitHub Pages.

---
Maintained by Mayank Jaiswal
