# Coffee-Recipe
A serverless Progressive Web Application (PWA) designed to track and standardize coffee brewing variables. The application solves the problem of inconsistent brewing by logging precise metrics such as coffee dosage, water weight, temperature, and immersion time.

Markdown

# ☕ The Daily Brew | Universal Recipe Keeper

A minimal, cloud-synced web application for tracking and refining coffee recipes. Built with a focus on simplicity, this app runs universally on any device (iOS, Android, Desktop) and syncs data instantly using Google Firestore.

![Status](https://img.shields.io/badge/status-active-success.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Platform](https://img.shields.io/badge/platform-Universal%20Web-orange)

## ✨ Key Features

* **☁️ Universal Cloud Sync:** Add a recipe on your iPhone, and it instantly appears on your laptop. Powered by Google Firebase (Free Tier).
* **📱 Native App Feel:** Designed with iOS meta tags to hide browser bars and function like a native app when added to the Home Screen.
* **⚖️ Smart Ratio Calculator:** Automatically calculates the Coffee-to-Water ratio (e.g., 1:16.5) in real-time as you type.
* **⚙️ Equipment Manager:** Built-in support for V60, Aeropress, etc., plus a simplified UI for logging grind size, temp, and time.
* **💸 Zero Cost:** Uses the Firebase "Spark" plan, allowing for storage of millions of recipes for free without a credit card.

## 🛠️ Tech Stack

* **Frontend:** Vanilla HTML5, CSS3 (Grid/Flexbox), JavaScript (ES6 Modules).
* **Backend / Database:** Google Firebase (Firestore NoSQL).
* **Hosting:** Static HTML hosting (Netlify / Tiiny / GitHub Pages).

## 🚀 Setup Instructions

### 1. Clone the Repository
```bash
git clone [https://github.com/mayankjaiswal12/daily-brew.git](https://github.com/mayankjaiswal12/daily-brew.git)
cd daily-brew
2. Firebase Configuration
This app requires a Firebase project to store data.

Go to Firebase Console and create a new project.

Navigate to Build > Firestore Database and create a database in Test Mode.

Go to Project Settings, scroll down, and register a Web App.

Copy your firebaseConfig object.

3. Connect Your Database
Open index.html and locate the config section:

JavaScript

// REPLACE THIS WITH YOUR OWN CONFIG
const firebaseConfig = {
    apiKey: "AIzaSyD-YOUR-API-KEY",
    authDomain: "your-project.firebaseapp.com",
    projectId: "your-project-id",
    // ...
};
4. Deploy
Since this is a static file, you can deploy it anywhere:

GitHub Pages: Go to Repo Settings > Pages > Source: Main.

Netlify Drop: Drag and drop the folder.

📱 iPhone / iOS Installation
For the best experience:

Visit your deployed URL in Safari.

Tap the Share button.

Select "Add to Home Screen".

The app will launch full-screen without browser UI.

🔒 Privacy & Data
Data Location: All recipes are stored in your private Google Firestore database.

Cost: The project runs on the Firebase Free Tier, which allows for 40,000 reads/writes per day (effectively free for personal use).

🤝 Contributing
Contributions are welcome!

Fork the project.

Create your feature branch (git checkout -b feature/NewBrewMethod).

Commit your changes.

Push to the branch.

Open a Pull Request.

Maintained by Mayank Jaiswal
