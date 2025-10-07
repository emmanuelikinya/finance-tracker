# Firebase Setup Instructions

## Step 1: Create Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Add Project" or "Create a project"
3. Enter project name: **"Financial Tracker"** (or your preferred name)
4. Disable Google Analytics (optional for personal use)
5. Click "Create Project"

## Step 2: Enable Authentication

1. In Firebase Console, click "Authentication" in left sidebar
2. Click "Get Started"
3. Click "Sign-in method" tab
4. Enable these methods:
   - **Email/Password** - Toggle ON
   - **Google** (optional) - Toggle ON if you want Google sign-in
5. Click "Save"

## Step 3: Create Firestore Database

1. In Firebase Console, click "Firestore Database" in left sidebar
2. Click "Create database"
3. Choose **"Start in production mode"** (we'll add security rules)
4. Choose your location (e.g., us-central, europe-west)
5. Click "Enable"

## Step 4: Configure Security Rules

1. In Firestore Database, click "Rules" tab
2. Open the file `firestore.rules` from your project folder
3. Copy ALL the content from that file
4. Paste it into the Firestore Rules editor (replace everything)
5. Click "Publish"

**Important:** These rules ensure:
- Users can only see their own financial data
- Admins can view all users (for admin panel)
- All data is protected and isolated by user ID

## Step 5: Get Your Firebase Config

1. In Firebase Console, click the gear icon (⚙️) → "Project settings"
2. Scroll down to "Your apps" section
3. Click the **Web icon** (</>)
4. Register app name: "Financial Tracker Web"
5. Check "Also set up Firebase Hosting" (optional)
6. Click "Register app"
7. **COPY** the firebaseConfig object - it looks like this:

```javascript
const firebaseConfig = {
  apiKey: "AIzaSyXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
  authDomain: "your-project.firebaseapp.com",
  projectId: "your-project-id",
  storageBucket: "your-project.appspot.com",
  messagingSenderId: "123456789012",
  appId: "1:123456789012:web:abcdef1234567890"
};
```

8. **SAVE THIS CONFIG** - you'll need it in the next step

## Step 6: Set Admin Email

1. Open the file: `budget_tracker_pro.html` in a text editor
2. Find this line (around line 312):

```javascript
const ADMIN_EMAILS = ['YOUR_ADMIN_EMAIL@example.com']; // Replace with your email
```

3. **Replace** `YOUR_ADMIN_EMAIL@example.com` with your actual email address
4. Example: `const ADMIN_EMAILS = ['john@example.com', 'admin@company.com'];`
5. You can add multiple admin emails separated by commas
6. Save the file

## Step 7: Update Your App Firebase Config

1. In the same file: `budget_tracker_pro.html`
2. Find this section (around line 302):

```javascript
// REPLACE THIS WITH YOUR FIREBASE CONFIG
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

3. **Replace** with your actual config from Step 5
4. Save the file

## Step 8: Test Your App

1. Open `budget_tracker_pro.html` in Chrome or Edge
2. You should see a login page
3. Try creating an account with your admin email
4. After login, check if "ADMIN" badge appears next to your name
5. Click the "👑 Admin" tab to see all users
6. Start tracking your finances!

## Step 9: Install as Desktop App (Optional)

**On Windows:**
1. Open the app in Chrome/Edge
2. Look for install icon in address bar (⊕ or 🖥️)
3. Click "Install"
4. App appears in Start Menu

**On Android/iPhone:**
1. Open app in Chrome/Safari
2. Tap menu (⋮ or share icon)
3. Tap "Add to Home Screen"
4. App appears on home screen like native app

---

## Troubleshooting

**"Auth domain not authorized"**
- Go to Firebase Console → Authentication → Settings → Authorized domains
- Add your domain or `localhost`

**"Permission denied"**
- Check Firestore security rules are published
- Make sure you're logged in

**"App not loading"**
- Check browser console for errors (F12)
- Verify Firebase config is correct
- Check internet connection

---

## Support

If you need help, the setup process takes about 10 minutes. Let me know if you get stuck!
