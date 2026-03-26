# Firebase Setup Guide

To enable cloud storage for your drum practice app, you need to set up a free Firebase project:

## Step 1: Create Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Add project"
3. Enter a project name (e.g., "drum-practice")
4. Disable Google Analytics (not needed)
5. Click "Create project"

## Step 2: Set up Realtime Database

1. In your Firebase project, click "Realtime Database" in the left sidebar
2. Click "Create Database"
3. Choose a location (e.g., US)
4. **Start in test mode** (you can add security rules later)
5. Click "Enable"

## Step 3: Get Your Configuration

1. In Firebase Console, click the gear icon → "Project settings"
2. Scroll down to "Your apps"
3. Click the web icon `</>` to add a web app
4. Give it a nickname (e.g., "drum-practice-web")
5. **Don't** enable Firebase Hosting
6. Click "Register app"
7. Copy the `firebaseConfig` object

## Step 4: Update index.html

1. Open `index.html` in a text editor
2. Find this section near the top of the `<script>` tag:

```javascript
// Firebase Configuration - REPLACE WITH YOUR OWN FIREBASE PROJECT CONFIG
const firebaseConfig = {
    apiKey: "AIzaSyDXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
    authDomain: "your-project.firebaseapp.com",
    databaseURL: "https://your-project-default-rtdb.firebaseio.com",
    projectId: "your-project",
    storageBucket: "your-project.appspot.com",
    messagingSenderId: "123456789012",
    appId: "1:123456789012:web:abcdef1234567890"
};
```

3. Replace it with your actual Firebase config
4. Save the file
5. Commit and push to GitHub:

```bash
git add index.html
git commit -m "Add Firebase configuration"
git push origin main
```

## Step 5: Configure Database Security Rules (Optional but Recommended)

1. In Firebase Console, go to "Realtime Database" → "Rules" tab
2. Replace the rules with:

```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```

**Note:** These rules allow anyone to read/write. For better security, you can add authentication later, but for a personal app this is fine.

## Done!

Your app will now save all songs and patterns to the cloud. Any device accessing your GitHub Pages site will see the same data!
