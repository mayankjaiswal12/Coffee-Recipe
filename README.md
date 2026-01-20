Here is the updated `README.md` tailored specifically for **Netlify**.

The setup instructions are now much simpler because Netlify handles the deployment automatically.

---

```markdown
# ☕ The Daily Brew | Universal Coffee Recipe Keeper

**The Daily Brew** is a minimalist, cloud-synced web application designed to track, refine, and standardize your coffee brewing recipes.

Unlike static note-taking apps, this project is a **Universal PWA (Progressive Web App)**. It runs on any device (iOS, Android, Desktop), installs to your home screen, and syncs your recipes instantly across all devices using a personal Google Firebase database.

![Project Status](https://img.shields.io/badge/status-live-success.svg)
![Hosting](https://img.shields.io/badge/hosting-Netlify-00C7B7)
![Stack](https://img.shields.io/badge/backend-Firebase-orange)

## ✨ Features

* **☁️ Universal Cloud Sync:** Write a recipe on your iPhone in the kitchen; see it instantly on your Laptop.
* **📱 Native App Experience:** Optimized for iOS/Android. Add it to your Home Screen to remove browser bars and run it full-screen.
* **⚖️ Live Ratio Calculator:** Automatically calculates the Coffee-to-Water ratio (e.g., `1:16.5`) in real-time.
* **⚙️ Smart Equipment Manager:** Built-in support for V60, Aeropress, etc., plus the ability to type custom methods (e.g., "Siphon").
* **🛡️ Secure & Private:** You own your data. It lives in your personal Firebase instance, locked to your specific Netlify domain.
* **💸 Zero Cost:** Architected to run entirely on Netlify's free tier and the Firebase Spark (Free) plan.

---

## 🚀 How to Setup Your Own (The Netlify Method)

Because this app uses a private database, you cannot just "use" my link to store your personal recipes. You need to create your own instance.

**Follow these 3 steps to deploy your own personal version in under 5 minutes.**

### Step 1: Fork the Repository
1.  Look at the top-right corner of this page.
2.  Click the **Fork** button.
3.  This creates an exact copy of the code in your own GitHub account.

### Step 2: Create Your Database (Firebase)
1.  Go to the [Firebase Console](https://console.firebase.google.com/) and log in with your Google account.
2.  Click **Add project** and give it a name (e.g., `my-coffee-app`).
3.  **Create the Database:**
    * Go to **Build** → **Firestore Database**.
    * Click **Create Database** → Start in **Test Mode**.
    * Select a location near you and click **Enable**.
4.  **Get the Config Code:**
    * Click the **Gear Icon ⚙️** (Project Settings).
    * Scroll down to "Your apps" and click the **Web (`</>`)** icon.
    * Copy the `firebaseConfig` code block.
5.  **Paste into Code:**
    * Go to your GitHub repository -> `index.html`.
    * Replace the existing `const firebaseConfig = { ... }` with your new code.
    * Commit the changes.

### Step 3: Go Live with Netlify
1.  Go to [Netlify.com](https://www.netlify.com/) and sign up with GitHub.
2.  Click **"Add new site"** → **"Import from an existing project"**.
3.  Select **GitHub** and choose your `Coffee-Recipe` repository.
4.  Click **Deploy Site**.
5.  Netlify will give you a live URL (e.g., `fast-coffee-123.netlify.app`). You can change this in **Site Settings > Change site name**.

---

## 🔒 Security Setup (Critical)

To prevent others from using your database quota, you must lock your API key to your Netlify site.

1.  Go to [Google Cloud Credentials](https://console.cloud.google.com/apis/credentials).
2.  Select your project and edit the API Key.
3.  Under **Application restrictions**, choose **Websites**.
4.  Add your Netlify URL with a wildcard:
    * `https://your-site-name.netlify.app/*`
5.  Click **Save**.

Now, your app will only work when accessed from your secure Netlify link.

---

## 📱 Installation on iPhone / Android

To get the full app experience:

1.  Open your new Netlify link in **Safari** (iOS) or **Chrome** (Android).
2.  Tap the **Share** button (iOS) or **Menu** dots (Android).
3.  Select **"Add to Home Screen"**.
4.  Launch the app from the new icon on your home screen.

---

## 🛠️ Tech Stack

* **Frontend:** HTML5, CSS3, Vanilla JavaScript (ES6 Modules).
* **Database:** Google Cloud Firestore (NoSQL).
* **Hosting:** Netlify (Global CDN).

Maintained by Mayank Jaiswal
